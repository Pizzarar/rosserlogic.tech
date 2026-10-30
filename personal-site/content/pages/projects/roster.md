---
title: "Roster & Paseo Multi-Agent Workflow"
description: "Roster is a TypeScript plugin for Paseo that turns a multi-agent workspace into a live roster, lead-grouped board, workspace cleanup, and lead handoffs — the control surface for a private encrypted network, role-scoped agent team."
aliases:
  - /roster
extra:
  day_body: true
---

<div class="tag-row">
<span class="tag">TypeScript</span>
<span class="tag">React Native (UI primitives)</span>
<span class="tag">@getpaseo/plugin 0.13.2</span>
<span class="tag">Private Encrypted Network</span>
<span class="tag">Git Worktrees</span>
</div>

Repository: <a href="https://github.com/Pizzarar/Roster" target="_blank" rel="noopener noreferrer">github.com/Pizzarar/Roster</a>

## Overview &amp; Architecture

Roster is a Paseo plugin written in TypeScript. Its manifest declares the package name `paseo-plugin-roster`, version `0.2.0` (unreleased — 0 git tags/releases), an MIT `LICENSE`, and a dependency on `@getpaseo/plugin` `0.13.2` (requiring Paseo `0.13.2+`). The UI is built with React Native primitives.

The plugin is split across a client and a server surface, with a shared contract in between:

- **Client** (`index.client.tsx` + `client/`): sidebar lead pins, the agent board grouped by lead, a workspaces cleanup view, and plugin settings.
- **Server** (`index.server.ts` + `server/`): two-tap Stop, lead handoffs (detach, adopt, relay), and the lead-finding system prompt line.
- **Shared** (`shared/`): the settings schema and the client/server RPC contract.

Documentation lives in `README.md` and `OVERVIEW.md`.

## The Paseo Network &amp; Multi-Agent Team Workflow

Roster was built to drive a specific way of working: not a single generalist chat thread, but a coordinated team of role-scoped agents running on a self-hosted Paseo daemon that can be reached from anywhere.

### Anywhere Coordination over a Private Encrypted Network

The workstation Paseo daemon is bound to a private encrypted network rather than exposed through public ports. Any device on that network — desktop or phone — sees the same live agent board, workspaces, and review gates, so progress can be checked, a gate review answered, or a lead handoff triggered from anywhere without opening inbound ports or standing up a public tunnel.

### Role-Scoped Profiles &amp; Cross-Family Review

Work is split across specialized agent profiles matched to the shape of each task rather than piled into one long conversation, with no fixed model-to-role lock-in: **Lead** coordinates and dispatches; **implementers** (**standard**, **hard**, and a **work-order implementer** on trial) build features and scoped work orders; **Mechanical** handles low-judgment edits and build tasks; **Spec** and **Planner** turn goals into structured plans and work orders; **Scout** and **Pre-check** run one-shot lookups and pre-verify worker output before the Lead reads it; **Audit** runs read-only verification passes; **cross-family reviewers** critique output using a different model family than the one that produced the work so no model grades its own output; and an **escalation-only senior reasoning tier** handles the hardest architectural or debugging knots.

### Worktree Isolation &amp; Human Gates

Parallel streams each run in their own isolated git worktree so changes never collide, and every stream halts at staged human-in-the-loop gates (`Gate A → Gate B → Gate C`) before the next phase begins. Handoff state files and a persistent dispatch log record who did what and where, so the whole chain stays reviewable and reproducible. Roster makes that workflow manageable day-to-day: lead pins keep the active Lead above the workspace list, the handoff actions (detach, adopt, relay) move workers cleanly when a Lead is replaced, and the workspaces/worktree cleanup view surfaces stale worktrees that are safe to archive.

## Recent Development

Work on `origin/main` is tracked across three commits:

- `fb34817` (2026-10-29) — Initial commit
- `3eaa7a8` (2026-10-29) — Roster v0.1.0: lead pins, agent board, worktrees, stop
- `13ee7ac` (2026-10-30) — Lead handoffs and workspace cleanup (v0.2.0)

## Gallery

<figure>
  <img src="https://placehold.co/1200x750/1e1c40/ff6fa5?text=proj-roster-board" data-asset="proj-roster-board" data-final="assets/img/proj-roster-board.webp" width="1200" height="750" alt="Roster agent board grouping Paseo agents by lead, status, and task lane">
  <figcaption>Roster agent board, grouped by lead and status</figcaption>
</figure>

<figure>
  <img src="https://placehold.co/1200x750/1e1c40/ff6fa5?text=proj-roster-sidebar" data-asset="proj-roster-sidebar" data-final="assets/img/proj-roster-sidebar.webp" width="1200" height="750" alt="Roster compact left sidebar roster tree view">
  <figcaption>Compact left sidebar roster tree</figcaption>
</figure>

<figure>
  <img src="https://placehold.co/1200x750/1e1c40/ff6fa5?text=proj-roster-workspaces" data-asset="proj-roster-workspaces" data-final="assets/img/proj-roster-workspaces.webp" width="1200" height="750" alt="Roster workspaces and worktree cleanup overview">
  <figcaption>Workspaces and worktree cleanup overview</figcaption>
</figure>

<figure>
  <img src="https://placehold.co/1200x750/1e1c40/ff6fa5?text=proj-roster-workflow-diagram" data-asset="proj-roster-workflow-diagram" data-final="assets/img/proj-roster-workflow-diagram.webp" width="1200" height="750" alt="High-level diagram of the private encrypted network to Paseo daemon to Lead and Worker worktrees with cross-family review gate workflow">
  <figcaption>Private encrypted network → Paseo daemon → Lead/Worker worktrees with review gate</figcaption>
</figure>
