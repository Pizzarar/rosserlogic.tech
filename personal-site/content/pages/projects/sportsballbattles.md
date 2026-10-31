---
title: "SportsBallBattles"
image: /static/sprites/og-sportsballbattles.png
description: "A Godot arcade football auto-battler and roster-management prototype pairing a pure deterministic simulation with 3D active-ragdoll Game Day playback."
aliases:
  - /sportsballbattles
extra:
  body_style: crt
  banner: sportsballbattles
---

<div class="tag-row">
<span class="tag">Godot 4.7.2</span>
<span class="tag">GDScript 2.0</span>
<span class="tag">Jolt Physics 3D</span>
<span class="tag">Deterministic Sim</span>
<span class="tag">Active Ragdoll</span>
</div>

<p>SportsBallBattles is an Idle Minds prototype in active development. The repository is private, so there is no public source link or playable build yet.</p>

## Overview

SportsBallBattles is an arcade football auto-battler. Between matches you draft, manage, and upgrade a roster; on Game Day you sit back and watch the plays unfold in 3D active-ragdoll chaos: limbs, tackles, and a broadcast camera with replay.

The engine is split clean down the middle, and that split is the interesting part. The **simulation** is pure deterministic integer math with zero scene dependencies, so every match resolves the same way every time. The **presentation** is a separate layer that reads the sim's output and renders the 3D ragdolls, the broadcast camera, and the stadium atmosphere. Simulation and presentation are decoupled.

The project is self-described as "complete except art and audio". Every visual below is work-in-progress placeholder geometry and UI.

## Under the Hood

- **Project:** Godot 4.7.2, GL Compatibility renderer, Jolt Physics 3D, GDScript 2.0.
- **Simulation:** a `sim/` layer of pure data with integer math, an injected RNG, and an emitted event log, with no scene or node dependencies.
- **Presentation:** a `presentation/playback/` layer that drives active ragdolls, the physical football, throws and catches, broadcast camera and replay, 11-on-11 filler, and the night-stadium mode.
- **Progression:** hub roster management, shop tier upgrades, a tutorial, and a hall of fame between matches.

## Gallery

Every capture below is labeled **work in progress, placeholder art**.

<div class="pgal" data-pgal role="region" aria-roledescription="gallery" aria-label="SportsBallBattles screenshots">
<div class="pgal-dev" data-title="SportsBallBattles"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src='/static/previews/sportsballbattles/night-kickoff.png' data-asset="proj-sportsballbattles-night-kickoff" data-final="static/previews/sportsballbattles/night-kickoff.png" width="1200" height="750" loading="lazy" alt="SportsBallBattles night stadium kickoff view: work in progress, placeholder art">
  <figcaption>Night stadium kickoff view: work in progress, placeholder art</figcaption>
</figure></li>
<li><figure>
  <img src='/static/previews/sportsballbattles/pre-snap-formation.png' data-asset="proj-sportsballbattles-pre-snap-formation" data-final="static/previews/sportsballbattles/pre-snap-formation.png" width="1200" height="750" loading="lazy" alt="SportsBallBattles pre-snap formation view: work in progress, placeholder art">
  <figcaption>Pre-snap formation view: work in progress, placeholder art</figcaption>
</figure></li>
<li><figure>
  <img src='/static/previews/sportsballbattles/hub-offense.png' data-asset="proj-sportsballbattles-hub-offense" data-final="static/previews/sportsballbattles/hub-offense.png" width="1200" height="750" loading="lazy" alt="SportsBallBattles hub offense roster view: work in progress, placeholder art">
  <figcaption>Hub offense roster view: work in progress, placeholder art</figcaption>
</figure></li>
<li><figure>
  <img src='/static/previews/sportsballbattles/shop-upgrades.png' data-asset="proj-sportsballbattles-shop-upgrades" data-final="static/previews/sportsballbattles/shop-upgrades.png" width="1200" height="750" loading="lazy" alt="SportsBallBattles shop upgrades view: work in progress, placeholder art">
  <figcaption>Shop upgrades view: work in progress, placeholder art</figcaption>
</figure></li>
<li><figure>
  <img src='/static/previews/sportsballbattles/hall-of-fame.png' data-asset="proj-sportsballbattles-hall-of-fame" data-final="static/previews/sportsballbattles/hall-of-fame.png" width="1200" height="750" loading="lazy" alt="SportsBallBattles hall of fame view: work in progress, placeholder art">
  <figcaption>Hall of fame view: work in progress, placeholder art</figcaption>
</figure></li>
</ul>
</div></div>
</div>

<figure>
  <picture>
    <source media='(prefers-reduced-motion: no-preference)' srcset='/static/previews/sportsballbattles/tackle-loop.webp' type='image/webp'>
    <img src='/static/previews/sportsballbattles/tackle-poster.png' width='800' height='450' loading='lazy' alt='Looping capture of a Game Day playback: a receiver catches a pass, and a defender tackles the receiver, who falls as a ragdoll. Work in progress, placeholder art.'>
  </picture>
  <figcaption>work in progress, placeholder art. Looping capture of one Game Day play: a pass completion, then the tackle.</figcaption>
</figure>

