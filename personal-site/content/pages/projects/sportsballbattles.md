---
title: "SportsBallBattles"
description: "A Godot 4.7.2 arcade football auto-battler and roster-management prototype pairing a pure deterministic simulation with 3D active-ragdoll Game Day playback."
aliases:
  - /sportsballbattles
extra:
  day_body: true
---

<div class="tag-row">
<span class="tag">Godot 4.7.2</span>
<span class="tag">GDScript 2.0</span>
<span class="tag">Jolt Physics 3D</span>
<span class="tag">GL Compatibility</span>
<span class="tag">Deterministic Sim</span>
<span class="tag">Active Ragdoll</span>
</div>

<p>SportsBallBattles is an Idle Minds prototype in active development. The repository is private, so there is no public source link or playable build yet.</p>

## Overview &amp; Architecture

SportsBallBattles is a Godot 4.7.2 project configured for the GL Compatibility renderer (Jolt Physics 3D) and GDScript 2.0. `project.godot` sets `config/name="Sports Ball Battler"`, the GL Compatibility renderer, and Jolt Physics 3D, with a main scene of `res://game/main.tscn`, 60 physics ticks per second, and autoload singletons `GameSession`, `Audio`, and `_mcp_game_helper`. The GUT test framework lives under `addons/gut/`.

The architecture separates a **pure deterministic simulation** from its **presentation**. The `sim/` layer is pure data with integer math, an injected `SimRng`, and an emitted `EventLog`, with zero scene/Node dependencies. The `presentation/playback/` layer renders 3D Game Day with active ragdoll physics (`ActiveRagdoll`, `Muscles`, `BodyDriver`, `ContactDirector`, `PhysicsLOD`), a physical football, throws/catches, broadcast camera and replay, 11-on-11 filler, physics freeze, procedural legs/feet, camera framing, game day juice, and night stadium mode.

Between matches, progression runs through hub roster management (Offense/Defense, drag-drop, compact cards), shop tier upgrades, a tutorial, and a hall of fame.

The project is self-described as "complete except art and audio" — all current visuals are work-in-progress placeholder geometry and UI.

## Gallery

Every capture below is labeled **work in progress, placeholder art**.

<figure>
  <img src="/static/previews/sportsballbattles/night-kickoff.png" data-asset="proj-sportsballbattles-night-kickoff" data-final="static/previews/sportsballbattles/night-kickoff.png" width="1200" height="750" alt="SportsBallBattles night stadium kickoff view — work in progress, placeholder art">
  <figcaption>work in progress, placeholder art</figcaption>
</figure>

<figure>
  <img src="/static/previews/sportsballbattles/pre-snap-formation.png" data-asset="proj-sportsballbattles-pre-snap-formation" data-final="static/previews/sportsballbattles/pre-snap-formation.png" width="1200" height="750" alt="SportsBallBattles pre-snap formation view — work in progress, placeholder art">
  <figcaption>work in progress, placeholder art</figcaption>
</figure>

<figure>
  <img src="/static/previews/sportsballbattles/hub-offense.png" data-asset="proj-sportsballbattles-hub-offense" data-final="static/previews/sportsballbattles/hub-offense.png" width="1200" height="750" alt="SportsBallBattles hub offense roster view — work in progress, placeholder art">
  <figcaption>work in progress, placeholder art</figcaption>
</figure>

<figure>
  <img src="/static/previews/sportsballbattles/shop-upgrades.png" data-asset="proj-sportsballbattles-shop-upgrades" data-final="static/previews/sportsballbattles/shop-upgrades.png" width="1200" height="750" alt="SportsBallBattles shop upgrades view — work in progress, placeholder art">
  <figcaption>work in progress, placeholder art</figcaption>
</figure>

<figure>
  <img src="/static/previews/sportsballbattles/hall-of-fame.png" data-asset="proj-sportsballbattles-hall-of-fame" data-final="static/previews/sportsballbattles/hall-of-fame.png" width="1200" height="750" alt="SportsBallBattles hall of fame view — work in progress, placeholder art">
  <figcaption>work in progress, placeholder art</figcaption>
</figure>
