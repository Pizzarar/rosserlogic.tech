---
title: "Roster & Paseo Multi-Agent Workflow"
description: "Roster is a TypeScript plugin for Paseo that turns a multi-agent workspace into a live roster, lead-grouped board, workspace cleanup, and lead handoffs — the control surface for a private encrypted network, role-scoped agent team."
aliases:
  - /roster
extra:
  day_body: true
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

Running a team of coding agents sounds clean in theory — until the screen fills with a wall of unnamed tabs and you can't tell who's leading, which worktree is dirty, or what's sitting in a human review gate waiting on you. Roster is the fix for that.

It's a plugin for Paseo that turns a multi-agent workspace into something you can actually steer: a live roster with lead pins so the active Lead stays pinned above the workspace list, a board grouped by lead so every task lane is visible at a glance, a two-tap Stop for whatever's stuck, and lead handoffs (detach, adopt, relay) so a change of Lead doesn't strand the team. A workspace/worktree cleanup view surfaces stale worktrees that are safe to archive.

It slots into a broader way of working: a self-hosted Paseo daemon on a private encrypted network, a role-scoped team, isolated git worktrees, and staged human checkpoints — all covered below.

## The Workflow It Drives

Roster is the control surface for a coordinated team, not a single generalist chat thread. Work is split across role-scoped profiles — a **Lead** who coordinates; **implementers** (**standard**, **hard**, and a **work-order implementer** on trial); **Mechanical**; **Spec**; **Planner**; **Scout**; **Pre-check**; **Audit**; **cross-family reviewers** who critique output with an independent model family so no model grades its own work; and an **escalation-only senior reasoning tier** for the hardest knots.

Parallel streams run in their own isolated git worktrees so changes never collide, and each stream halts at staged human checkpoints — `Gate A → Gate B → Gate C` — before the next phase begins. `HANDOFF.md` and `DISPATCH_LOG.md` record who did what and where, keeping the whole chain reviewable.

The daemon lives on a private encrypted network rather than behind public ports, so the board, workspaces, and review gates look the same from a desktop or a phone — without opening inbound ports or standing up a public tunnel.

## Under the Hood

- **Package:** `paseo-plugin-roster` `0.2.0`, built on `@getpaseo/plugin` `0.13.2` (TypeScript + React Native UI primitives).
- **Surfaces:** `client/` (lead pins, lead-grouped board, worktree cleanup, settings) · `server/` (two-tap Stop, lead handoffs, lead-finding prompt) · `shared/` (settings schema + RPC contract).
- **History:** `fb34817` (initial commit) → `3eaa7a8` (v0.1.0) → `13ee7ac` (lead handoffs + workspace cleanup, v0.2.0).

## Gallery

<figure>
  <img src="/static/previews/roster/workflow-diagram.svg" data-asset="proj-roster-workflow-diagram" width="1200" height="640" alt="Roster workflow diagram — operator to private encrypted network to Paseo daemon to lead to role-scoped team to cross-family review to staged human gates">
  <figcaption>Private encrypted network → Paseo daemon → Lead → role-scoped team → review gates</figcaption>
</figure>
