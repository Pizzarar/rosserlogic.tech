---
title: "SerbiseNow: AI Enhancement Triage"
image: /static/sprites/og-serbisenow.png
description: "SerbiseNow is a ServiceNow scoped app, built with the ServiceNow SDK (Fluent), that triages enhancement requests with an LLM-assisted pipeline, deterministic rules and a blind human review step."
extra:
  theme: day
  zone: pro
  nav_parent: "/work"
  body_style: paper
  banner: serbisenow
---

<div class="tag-row">
<span class="tag">ServiceNow SDK (Fluent)</span>
<span class="tag">TypeScript</span>
<span class="tag">ES5 script includes</span>
<span class="tag">Python 3.11+</span>
<span class="tag">ACLs &amp; business rules</span>
<span class="tag">Mock-LLM eval</span>
</div>

**In one line:** a ServiceNow app that routes incoming enhancement requests through AI triage, then locks a human reviewer's decision so the AI cannot quietly overwrite it.

**Source:** private repository, available on request.

## The problem

Enhancement requests arrive as free text. Someone has to read each one, decide how much care it needs, and route it. That judgment is slow, uneven, and hard to audit. An LLM can pull structured features out of a request, but I did not want a model making the routing call, and I wanted to be able to measure how often a human disagrees with it.

## The flow

<figure class="flow">
<svg class="flow-svg" viewBox="0 0 360 427" role="img" aria-labelledby="sn-t" xmlns="http://www.w3.org/2000/svg"><title id="sn-t">SerbiseNow enhancement triage flow in five steps: intake, AI triage with evidence guardrails, blind-review ACL gate, lock business rule, human reviewer decision</title><defs><marker id="sn" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="fl-ah" d="M0 0 L10 5 L0 10 z"/></marker></defs><g class="fl-n teal"><rect class="fl-box teal" x="15" y="8" width="330" height="46"/><text class="fl-t" x="180" y="27" text-anchor="middle">1. Intake</text><text class="fl-s" x="180" y="45" text-anchor="middle">request saved as enh_request row</text></g><line class="fl-ln" x1="180.0" y1="54" x2="180.0" y2="76" marker-end="url(#sn)"/><g class="fl-n violet"><rect class="fl-box violet" x="15" y="78" width="330" height="80"/><text class="fl-t" x="180" y="97" text-anchor="middle">2. AI triage + guardrails</text><text class="fl-s" x="180" y="115" text-anchor="middle">ai_triage: prescan, redact,</text><text class="fl-s" x="180" y="132" text-anchor="middle">3 samples, validate, rubric.</text><text class="fl-s" x="180" y="149" text-anchor="middle">Pasted secret: lane C, no model call</text></g><line class="fl-ln" x1="180.0" y1="158" x2="180.0" y2="180" marker-end="url(#sn)"/><g class="fl-n plain"><rect class="fl-box plain" x="15" y="182" width="330" height="63"/><text class="fl-t" x="180" y="201" text-anchor="middle">3. Blind-review ACL gate</text><text class="fl-s" x="180" y="219" text-anchor="middle">20 field-level read ACLs hide the AI</text><text class="fl-s" x="180" y="236" text-anchor="middle">suggestion; admin override is off</text></g><line class="fl-ln" x1="180.0" y1="245" x2="180.0" y2="267" marker-end="url(#sn)"/><g class="fl-n plain"><rect class="fl-box plain" x="15" y="269" width="330" height="63"/><text class="fl-t" x="180" y="288" text-anchor="middle">4. Lock business rule</text><text class="fl-s" x="180" y="306" text-anchor="middle">only the Review fields can change;</text><text class="fl-s" x="180" y="323" text-anchor="middle">runs for admins too, logs no values</text></g><line class="fl-ln" x1="180.0" y1="332" x2="180.0" y2="354" marker-end="url(#sn)"/><g class="fl-n pink"><rect class="fl-box pink" x="15" y="356" width="330" height="63"/><text class="fl-t" x="180" y="375" text-anchor="middle">5. Human reviewer decision UI</text><text class="fl-s" x="180" y="393" text-anchor="middle">confirm or override with a reason</text><text class="fl-s" x="180" y="410" text-anchor="middle">from a fixed list. Lane A, B or C</text></g></svg>
<figcaption>The pipeline end to end. Names are the real table and record names; the model only extracts features.</figcaption>
</figure>

In words:

1. **Intake.** A request is saved as an `enh_request` record.
2. **AI triage.** A daily scheduled job runs each new request through: prescan, redact, prompt, three model samples, validate, rubric. The model only extracts features; deterministic rules and a human make the decision.
3. **Blind human review.** A reviewer records their own lane and priority *before* seeing the AI suggestion. A configurable share of rows (default 20%) is blind; in the simulation's first phase every row is.
4. **Locked decision.** The reviewer confirms or overrides the AI suggestion with a reason from a fixed list. After that, only the Review fields of the row can change.

Each request lands in lane A, B or C. Lane A is eligible for an auto-generated catalog item, lane B gets a draft spec for a human to finish, and lane C is the highest-caution lane. The rubric checks lane C reasons first, and the model's opinion and the output validator can only make the lane stricter, never looser. A request that contains a pasted secret goes straight to lane C and the model is never called.

## What's built

- **Tables:** `enh_request`, `ai_triage` (one row per triage run, with version stamps, redacted input, lane columns, scores, review fields and metrics) and `guardrail_incident`.
- **Roles and ACLs:** `triage_reviewer`, `triage_admin` and `triage_service`. Read, create, write and delete are split by role, and reviewers can edit only the Review fields.
- **Blind review:** enforced with 20 field-level read ACLs on the AI-suggestion fields, with admin override turned off so an admin-only user cannot peek.
- **Business rules:** one locks every non-Review field (it runs for admins too, aborts the update, and logs only the row id, user name and changed column names, never values); others set the metric flags and propose a lane A spec.
- **System properties:** 17 main settings (batch size, samples per record, blind-review rate, confidence thresholds, allowed categories, version stamps), plus simulation and guardrail properties. Admin-only.
- **Review UI:** a custom "Review" form view, "Pending triage" and "All triage runs" lists, and UI actions to record a decision, confirm, override and re-triage. An admin-only metrics page sits alongside.
- **Prompt-injection defence:** the prompt treats request text as untrusted data and sets a flag instead of complying.
- **Guardrail job:** watches lane and status metrics and can step the simulation phase down or disable the app.
- **Simulation layer:** a phase switch lets reviewers run the whole pipeline on synthetic data with no real model.

The default LLM client is a deterministic mock. The real endpoint is a placeholder with no credentials, and nothing here is wired to a live model.

## How it's tested

- **Node tests:** 532 passing, 0 failing, across 17 suites in 21 files. The server logic is plain ES5 script includes, loaded directly by the node test runner.
- **Python eval harness (`triage_eval`):** 234 passing tests. The harness runs prescan, redact, triage ×3, validate, rubric, then reports agreement, a confusion matrix, calibration buckets, injection and secrets suites, false-positive rates and an ablation. The data is synthetic and the mock LLM is the default client. The harness's own caveat applies: *numbers prove the harness, not the model.*
- **ServiceNow ATF:** 16 tests are defined in Fluent (5 for the core pipeline, 11 end to end). They have **not** been run, because there is no instance wired up to run them against.

Counts below were re-run offline on 2026-11-26, from a clean checkout of the committed code. ATF is not part of this run.

<div class="window window-crt readout">
<div class="window-bar"><span>OFFLINE TEST RUN · 2026-11-26</span><span class="controls" aria-hidden="true"></span></div>
<div class="window-body"><pre><code>$ node --test "test/*.test.js"
# tests 532   # suites 17   # pass 532   # fail 0
$ python -m pytest triage_eval/tests -q
234 passed
$ python -m triage_eval.contract ‑‑check
prompt_version=0.1  schema_version=1.0
schema.json matches Appendix B
$ python -m triage_eval run --gold &lt;synthetic gold&gt;
records: 100 (test 55)   [mock LLM, synthetic data, offline]
secrets suite: 16/16 caught before any LLM call
injection suite: 10/10
schema validity 156/156 · evidence grounding 645/645
critical misroutes 4/55 and AI-gold kappa 0.451 miss the Phase-0 bars (mock model)
note: synthetic gold; numbers prove the harness, not the model</code></pre></div>
</div>


## Status

All data is synthetic. This is a built and tested prototype on a personal developer instance, not a production deployment. I make no accuracy or time-savings claims.

## Stack

ServiceNow SDK (Fluent, TypeScript) for the app definition. Server logic in plain ES5 script includes. A Python 3.11+ evaluation harness using `jsonschema`, `pyyaml` and `pytest`.
