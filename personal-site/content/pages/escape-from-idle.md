---
title: "Escape From Idle"
image: /static/sprites/og-escape-from-idle.png
description: "Escape From Idle is a post-apocalyptic modern-shooter idle game with extraction raids and a Melvor-style automation ladder. In development by Idle Minds."
extra:
  body_style: crt
  banner: escape-from-idle
  studio_mode: true
---

<figure>
  <img src="/static/previews/efi/efi-hideout.png" data-asset="efi-key-art" data-final="static/previews/efi/efi-hideout.png" width="1920" height="1080" alt="Escape From Idle hideout overview: experimental UI build, work in progress">
  <figcaption>In development: experimental UI build, work in progress</figcaption>
</figure>

**Escape From Idle** is a post-apocalyptic modern-shooter idle game built around extraction raids that run on a ticking timer. The longer you stay, the better the loot and the worse the threat.

## Features

- Extraction raids with a ticking raid timer: threat and loot scale together the longer you stay.
- Loot containers themed to their location, so you learn where the good stuff hides.
- Hireable mercenaries to build out your crew.
- A Melvor-style ladder that carries you from running every raid by hand to full automation.

## Pricing

Planned $5 flat. No ads, no in-app purchases, no gacha.

## Status

Currently in development at Idle Minds, built in Godot. Target platforms, release window, and store page details will be shared once locked in.

## Main Game Screens

<div class="pgal" data-pgal role="region" aria-roledescription="gallery" aria-label="Escape From Idle screenshots">
<div class="pgal-dev" data-title="Escape From Idle"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src="/static/previews/efi/efi-raids.png" data-asset="efi-raids" data-final="static/previews/efi/efi-raids.png" width="1920" height="1080" loading="lazy" alt="Escape From Idle extraction raids screen: experimental UI build, work in progress">
  <figcaption>Extraction raids screen: experimental UI build, work in progress</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/efi/efi-crafting.png" data-asset="efi-crafting" data-final="static/previews/efi/efi-crafting.png" width="1920" height="1080" loading="lazy" alt="Escape From Idle crafting screen: experimental UI build, work in progress">
  <figcaption>Crafting screen: experimental UI build, work in progress</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/efi/efi-hideout-upgrades.png" data-asset="efi-hideout-upgrades" data-final="static/previews/efi/efi-hideout-upgrades.png" width="1920" height="1080" loading="lazy" alt="Escape From Idle hideout upgrades screen: experimental UI build, work in progress">
  <figcaption>Hideout upgrades screen: experimental UI build, work in progress</figcaption>
</figure></li>
</ul>
</div></div>
</div>

## How the Raid View Took Shape

The raid view is being built in a separate UI lab before it goes into the main game. Everything in this section is that lab prototype, not in the main game yet. The art is placeholder made by AI agents and tools (an image generator, Blender renders, a pixel compiler, Godot captures).

### 1. A concept mock

It started with concept mocks from an image generator. This one is the stash screen.

<figure>
  <img src="/static/previews/efi/journey/stash-mock.png" data-asset="efi-journey-stash-mock" data-final="static/previews/efi/journey/stash-mock.png" width="1024" height="572" loading="lazy" alt="Concept mock of a stash screen: a grid of items such as duct tape, canned food, a rifle magazine and a helmet, with a side menu for raids, stash, skills, hideout and traders.">
  <figcaption>AI image-generator concept mock, October 2026. A picture, not a capture of anything running.</figcaption>
</figure>

### 2. The tactical map

The first playable raid view put the raid on an isometric map, with contacts, squad vitals, raid timers and a field log around it.

<div class="pgal" data-pgal data-pgal-full role="region" aria-roledescription="gallery" aria-label="Tactical map raid view captures">
<div class="pgal-dev" data-title="Raid view: tactical map"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src="/static/previews/efi/journey/map-contact-trail.png" data-asset="efi-journey-map-contact" data-final="static/previews/efi/journey/map-contact-trail.png" width="1600" height="900" loading="lazy" alt="Tactical map raid view: an isometric dock district with a scav contact and its trail, squad vitals, raid timers and a field log. Placeholder UI.">
  <figcaption>Contact: a scav and its trail on the map, with squad vitals, timers and the field log. Placeholder UI and numbers.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/efi/journey/map-deploy.png" data-asset="efi-journey-map-deploy" data-final="static/previews/efi/journey/map-deploy.png" width="1600" height="900" loading="lazy" alt="Tactical map raid view showing a Deploying banner for Harbor District. Placeholder UI.">
  <figcaption>Deploying into Harbor District. Placeholder UI and numbers.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/efi/journey/map-extract.png" data-asset="efi-journey-map-extract" data-final="static/previews/efi/journey/map-extract.png" width="1600" height="900" loading="lazy" alt="Tactical map raid view after extraction: a summary of XP earned and loot kept. Placeholder UI.">
  <figcaption>Extracted: XP earned and the loot kept. Placeholder UI and numbers.</figcaption>
</figure></li>
</ul>
</div></div>
</div>

### 3. The corridor

Next the raid moved into a first-person corridor: one rendered background per stop, with pixel enemies placed on top. It is a series of stills, not real-time 3D.

<div class="pgal" data-pgal role="region" aria-roledescription="gallery" aria-label="3D corridor raid view">
<div class="pgal-dev" data-title="Raid view: corridor"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src="/static/previews/efi/journey/corridor-stop2.png" data-asset="efi-journey-corridor-stop2" data-final="static/previews/efi/journey/corridor-stop2.png" width="1600" height="900" loading="lazy" alt="Rendered background for a corridor stop: a concrete passage with crates under a ceiling lamp. Placeholder art.">
  <figcaption>A corridor stop, rendered in Blender by an agent. Placeholder art.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/efi/journey/corridor-stop6-exit.png" data-asset="efi-journey-corridor-exit" data-final="static/previews/efi/journey/corridor-stop6-exit.png" width="1600" height="900" loading="lazy" alt="Rendered background for the last corridor stop: an open passage toward the exit, lit by two lamps. Placeholder art.">
  <figcaption>The exit stop, same pipeline. Placeholder art.</figcaption>
</figure></li>
<li><figure>
  <picture>
    <source media='(prefers-reduced-motion: no-preference)' srcset='/static/previews/efi/combat-loop.webp' type='image/webp'>
    <img src='/static/previews/efi/combat-poster.png' width='800' height='525' loading='lazy' alt='Looping capture of a fight in the corridor view: a scav steps out in a dockside container corridor, takes hits as its health bar drops, and goes down.'>
  </picture>
  <figcaption>The corridor view running: one scav fight, real Godot capture.</figcaption>
</figure></li>
</ul>
</div></div>
</div>

### 4. Pixel sprites

The enemies are pixel sprites. Concept art goes through a small Python pixel compiler (15 colours, a 1 px outline), and the result is placed into the corridor.

<figure class="px-figure">
  <img class="pixelated" src='/static/previews/efi/journey/scav-k3.png' data-asset="efi-journey-scav-k3" data-final="static/previews/efi/journey/scav-k3.png" width="48" height="76" loading="lazy" alt="A single pixel-art scav sprite in a hood and dark gear, holding a rifle, shown enlarged.">
  <figcaption>The scav sprite that was picked, 48 × 76 pixels, shown at 8× (4× on phones).</figcaption>
</figure>

<div class="pgal" data-pgal data-pgal-full role="region" aria-roledescription="gallery" aria-label="Pixel sprite sheets">
<div class="pgal-dev" data-title="Pixel sprites"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src="/static/previews/efi/journey/sprite-lineup.png" data-asset="efi-journey-sprite-lineup" data-final="static/previews/efi/journey/sprite-lineup.png" width="1690" height="1640" loading="lazy" alt="Sprite lineup sheet: scav, scav in cover, armored scav, a PMC pair and the Dockmaster boss, each in idle, breathe, aim and fire poses.">
  <figcaption>The current lineup: scav, armored scav, a PMC pair and the Dockmaster boss, each with idle, breathe, aim and fire poses.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/efi/journey/sprite-look1-before.png" data-asset="efi-journey-sprite-look1" data-final="static/previews/efi/journey/sprite-look1-before.png" width="2300" height="902" loading="lazy" alt="Older sprite set shown in the corridor at in-game size, then enlarged below.">
  <figcaption>Before: an earlier sprite set, in the corridor and enlarged. Replaced by the lineup above.</figcaption>
</figure></li>
</ul>
</div></div>
</div>

### 5. Where it is now

Rendered corridor, pixel enemy, cover to shoot from.

<figure>
  <picture>
    <source media='(prefers-reduced-motion: no-preference)' srcset='/static/previews/efi/journey/showcase-loop.webp' type='image/webp'>
    <img src="/static/previews/efi/journey/showcase-cover-aim.png" data-asset="efi-journey-showcase" data-final="static/previews/efi/journey/showcase-cover-aim.png" width="1600" height="900" loading="lazy" alt="Container corridor lit by a warm lamp: a pixel-art scav crouches behind sandbags and aims a rifle down the corridor.">
  </picture>
  <figcaption>The current corridor look: a scav aiming over sandbags. UI lab prototype, placeholder art built by AI agents.</figcaption>
</figure>

## Recent Work

### Main game

- Raid kit board: pick a destination and read its briefing on one board before a raid.
- Hydroponics: up to four shelf rows, five kinds of grower, and crops that only grow on some of them.
- Traders: contract offers as pick or pass cards, and a mood line for each trader.
- Items now carry a rarity.
- Hideout rooms you haven't unlocked yet stay hidden.

### UI lab: new enemy sprites

Lab only, not in the main game yet. The sprites are AI-generated, with extra poses and mirrors made by script.

<div class="pgal" data-pgal data-pgal-full role="region" aria-roledescription="gallery" aria-label="UI lab: new enemy sprites">
<div class="pgal-dev" data-title="UI lab: scav sprites"><div class="pgal-screen">
<ul class="pgal-track" tabindex="0" aria-label="Screenshots: use the arrow keys or the buttons to change">
<li><figure>
  <img src='/static/previews/efi/lab/scav-matrix-a.png' data-asset="efi-lab-scav-matrix-a" data-final="static/previews/efi/lab/scav-matrix-a.png" class="pixelated" width="752" height="456" loading="lazy" alt="Pixel scav sprite sheet, three rows (facing right, facing the camera, facing left) by four poses: idle, breathe, aim and fire.">
  <figcaption>Scav: three angles × idle, breathe, aim, fire. AI-generated, lab only.</figcaption>
</figure></li>
<li><figure>
  <img src='/static/previews/efi/lab/scav-matrix-b.png' data-asset="efi-lab-scav-matrix-b" data-final="static/previews/efi/lab/scav-matrix-b.png" class="pixelated" width="752" height="456" loading="lazy" alt="Pixel scav sprite sheet, three rows by four poses: flinching, hiding in cover, aiming from cover and firing from cover.">
  <figcaption>Scav: flinch and three cover poses. AI-generated, lab only.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/efi/lab/rx3b-scav.png" data-asset="efi-lab-rx3b-scav" data-final="static/previews/efi/lab/rx3b-scav.png" width="960" height="600" loading="lazy" alt="Raid corridor between red shipping containers: the pixel scav stands in the centre and fires toward the camera, a health bar labelled SCAV below it.">
  <figcaption>The scav in the raid corridor, firing. Lab capture; AI-generated sprite, AI placeholder background.</figcaption>
</figure></li>
<li><figure>
  <img src="/static/previews/efi/lab/rx3b-armored.png" data-asset="efi-lab-rx3b-armored" data-final="static/previews/efi/lab/rx3b-armored.png" width="960" height="600" loading="lazy" alt="The same container corridor with an armored scav sprite firing toward the camera.">
  <figcaption>The armored scav in the same spot. Lab capture; AI-generated sprite, AI placeholder background.</figcaption>
</figure></li>
</ul>
</div></div>
</div>
