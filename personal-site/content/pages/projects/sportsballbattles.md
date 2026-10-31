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

The project is self-described as "complete except art and audio". Unless a caption says otherwise, every visual below is work-in-progress placeholder geometry and UI.

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


## Recent Work

A few before and after shots from the latest art pass. The 3D players, field and stadium are still placeholder geometry.

### Pixel portraits

Pixel portraits for players and coaches, drawn by a script.

<div class="pgal pgal--tall" data-pgal data-pgal-full role="region" aria-roledescription="gallery" aria-label="Pixel portraits: before and after">
<div class="pgal-dev" data-title="Pixel portraits: before / after"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/coach-pick-before.png" data-asset="sbb-iter-coach-pick-before" data-final="static/previews/sportsballbattles/iter/coach-pick-before.png" width="720" height="1280" loading="lazy" alt="Before: the Pick Your Head Coach screen, a list of coaches such as Air Raid Guru and Penny Pincher, each with an empty yellow box where the portrait goes.">
  <figcaption>Before: an empty box for every coach. The yellow bars are shot-tool messages.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/coach-pick-portraits.png" data-asset="sbb-iter-coach-pick-portraits" data-final="static/previews/sportsballbattles/iter/coach-pick-portraits.png" width="720" height="1280" loading="lazy" alt="After: the same coach list, each coach now with a small pixel-art bust holding a prop for their power.">
  <figcaption>After: a pixel bust for each coach. Agent-made pixel art, drawn by script.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/portrait-sheet.png" data-asset="sbb-iter-portrait-sheet" data-final="static/previews/sportsballbattles/iter/portrait-sheet.png" width="848" height="1264" loading="lazy" alt="Preview sheet rendered in the game: rows of pixel player busts in red, blue, green, purple and black kits, then the coach busts, play icons and tier badges.">
  <figcaption>Player busts in several team kits, plus coaches and icons. Agent-made pixel art, drawn by script.</figcaption>
</figure></li>
</ul>
</div></div>
</div>

### Jerseys and field details

Road jerseys, named end zones, pylons and new light towers.

<div class="pgal" data-pgal data-pgal-full role="region" aria-roledescription="gallery" aria-label="Field and player look: before and after">
<div class="pgal-dev" data-title="Game Day: before / after"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/field-before.png" data-asset="sbb-iter-field-before" data-final="static/previews/sportsballbattles/iter/field-before.png" width="887" height="540" loading="lazy" alt="Before: a pre-snap view from behind the offense, red players against blue players, with a plain blue end zone. Placeholder art.">
  <figcaption>Before: one colour head to toe, a blank end zone. Placeholder art.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/field-after.png" data-asset="sbb-iter-field-after" data-final="static/previews/sportsballbattles/iter/field-after.png" width="887" height="540" loading="lazy" alt="After: the same play, the defense now in white jerseys with blue helmets, the end zone lettered with a team name, arrows beside the yard numbers. Placeholder art.">
  <figcaption>After: road jerseys, a named end zone, pylons. Placeholder art.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/towers-before.png" data-asset="sbb-iter-towers-before" data-final="static/previews/sportsballbattles/iter/towers-before.png" width="1280" height="520" loading="lazy" alt="Before: two light towers drawn as grey poles with flat white slabs on top, over a night field. Placeholder art.">
  <figcaption>Before: a pole and a flat slab. Placeholder art.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/towers-after.png" data-asset="sbb-iter-towers-after" data-final="static/previews/sportsballbattles/iter/towers-after.png" width="1280" height="520" loading="lazy" alt="After: lattice light towers with a grid of lamps and a soft glow around each head. Placeholder art.">
  <figcaption>After: lattice towers with lamp glow. Placeholder art.</figcaption>
</figure></li>
</ul>
</div></div>
</div>

### Pixel menu kit

The menus now use a pixel-style kit from the same script.

<div class="pgal pgal--tall" data-pgal data-pgal-full role="region" aria-roledescription="gallery" aria-label="Menus: before and after">
<div class="pgal-dev" data-title="Menus: before / after"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/hub-before-kit.png" data-asset="sbb-iter-hub-before" data-final="static/previews/sportsballbattles/iter/hub-before-kit.png" width="720" height="1280" loading="lazy" alt="Before: the week hub screen with player cards, a bench and a shop, all in rounded navy boxes.">
  <figcaption>Before: the week hub in rounded navy boxes.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/hub-after-kit.png" data-asset="sbb-iter-hub-after" data-final="static/previews/sportsballbattles/iter/hub-after-kit.png" width="720" height="1280" loading="lazy" alt="After: the same hub screen with square pixel frames, black scoreboard cells for wins, fans and gold, and a slanted Bench heading.">
  <figcaption>After: pixel frames and scoreboard cells. Agent-made pixel art, drawn by script.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/sportsballbattles/iter/coach-pick-after-kit.png" data-asset="sbb-iter-coach-pick-after" data-final="static/previews/sportsballbattles/iter/coach-pick-after-kit.png" width="720" height="1280" loading="lazy" alt="The coach pick screen with pixel portraits, left-aligned text and pixel-framed cards.">
  <figcaption>Coach pick with the new kit. Agent-made pixel art, drawn by script.</figcaption>
</figure></li>
</ul>
</div></div>
</div>
