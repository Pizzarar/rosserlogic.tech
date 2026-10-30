---
title: "Roster & Paseo Multi-Agent Workflow"
image: /static/sprites/og-roster.png
description: "Roster is a TypeScript plugin for Paseo for running a team of coding agents: a live roster, a board grouped by lead, workspace cleanup, and lead handoffs."
aliases:
  - /roster
extra:
  body_style: crt
  banner: roster
---

<p><strong>Repository:</strong> <a href="https://github.com/Pizzarar/Roster" target="_blank" rel="noopener noreferrer">github.com/Pizzarar/Roster</a></p>

<div class="tag-row">
<span class="tag">TypeScript</span>
<span class="tag">React Native (UI primitives)</span>
<span class="tag">@getpaseo/plugin 0.13.2</span>
<span class="tag">Private Encrypted Network</span>
<span class="tag">Git Worktrees</span>
</div>

## Overview

Roster is a plugin for Paseo for running a team of coding agents. It adds a live roster with lead pins, so the active Lead stays pinned above the workspace list; a board grouped by lead; a two-tap Stop for a stuck agent; and lead handoffs (detach, adopt, relay). A workspace and worktree cleanup view shows stale worktrees that are safe to archive.

It slots into a broader way of working: a self-hosted Paseo daemon on a private encrypted network, a role-scoped team, isolated git worktrees, and staged human checkpoints, all covered below.

## How It Works

Roster doesn't rename agents. The agents rename and retire themselves, following naming rules I set in their instructions (a new lead takes the `★ LEAD` prefix; the one it replaces renames itself `(old)`). Roster reads those names and labels and sorts agents from them.

- **Spotting a lead:** an agent with a `role=lead` label is a lead. Without a role label, Roster checks the name: by default a name starting with `★ LEAD` is a lead, and one starting with `(old)` is a retired lead. Both patterns can be changed in the plugin settings.
- **Pinning:** every active lead gets its own row at the top of Roster's sidebar section, above the board and Workspaces links. The row label drops the `★ LEAD ·` prefix. Retired leads aren't pinned.
- **Handoffs:** when an agent creates another, Paseo labels the new one with its creator. When a new lead is created by another agent, Roster detaches it from its creator. If the creator was a lead, Roster moves that lead's running workers to the new lead and forwards their finished, failed and needs-permission events to it.
- **Finding the lead:** Roster adds one line to every new agent's instructions: run `paseo ls -g --json` and pick the agent in the project's folder whose name starts with `★ LEAD`, not `(old)`.

## The Workflow It Drives

Roster is the control surface for a coordinated team, not a single generalist chat thread. Work is split across role-scoped profiles: a **Lead** who coordinates; **implementers** (**standard**, **hard**, and a **work-order implementer** on trial); **Mechanical**; **Spec**; **Planner**; **Scout**; **Pre-check**; **Audit**; **cross-family reviewers** who critique output with an independent model family so no model grades its own work; and an **escalation-only senior reasoning tier** for the hardest knots.

Parallel streams run in their own isolated git worktrees so changes never collide, and each stream halts at staged human checkpoints (`Gate A → Gate B → Gate C`) before the next phase begins. `HANDOFF.md` and `DISPATCH_LOG.md` record who did what and where, keeping the whole chain reviewable.

The daemon lives on a private encrypted network rather than behind public ports, so the board, workspaces, and review gates look the same from a desktop or a phone, without opening inbound ports or standing up a public tunnel.

## Under the Hood

- **Package:** `paseo-plugin-roster` `0.2.0`, built on `@getpaseo/plugin` `0.13.2` (TypeScript + React Native UI primitives).
- **Surfaces:** `client/` (lead pins, lead-grouped board, worktree cleanup, settings) · `server/` (two-tap Stop, lead handoffs, lead-finding prompt) · `shared/` (settings schema + RPC contract).
- **History:** `fb34817` (initial commit) → `3eaa7a8` (v0.1.0) → `13ee7ac` (lead handoffs + workspace cleanup, v0.2.0).

## Gallery

<figure>
  <picture class="pixel-diagram">
    <source media="(min-width: 1200px)" srcset="/static/previews/roster/workflow-diagram.png" width="1056" height="560">
    <img src='/static/previews/roster/workflow-diagram-narrow.png' data-asset="proj-roster-workflow-diagram" width="272" height="1376" alt="Roster workflow diagram: operator to private encrypted network to Paseo daemon to lead to role-scoped team to cross-family review to staged human gates" class="pixelated">
  </picture>
  <figcaption>Private encrypted network → Paseo daemon → Lead → role-scoped team → review gates</figcaption>
</figure>
