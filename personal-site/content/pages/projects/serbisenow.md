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

Test counts were run on 2026-11-25.

## Status

All data is synthetic. This is a built and tested prototype on a personal developer instance, not a production deployment. I make no accuracy or time-savings claims.

## Stack

ServiceNow SDK (Fluent, TypeScript) for the app definition. Server logic in plain ES5 script includes. A Python 3.11+ evaluation harness using `jsonschema`, `pyyaml` and `pytest`.
