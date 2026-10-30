---
title: "Pssst: OSRS Companion"
description: "Pssst pairs a Java 11 RuneLite desktop plugin with a native Kotlin / Jetpack Compose Android companion app to surface live Old School RuneScape account state over LAN."
aliases:
  - /pssst
extra:
  day_body: true
---

<div class="tag-row">
<span class="tag">Kotlin</span>
<span class="tag">Jetpack Compose</span>
<span class="tag">Material3</span>
<span class="tag">Java 11</span>
<span class="tag">RuneLite Plugin API</span>
<span class="tag">LAN UDP</span>
<span class="tag">WorkManager</span>
<span class="tag">Room</span>
</div>

<p><strong>Android repo:</strong> <a href="https://github.com/Pizzarar/Pssst---OSRS-Companion-App--Android" target="_blank" rel="noopener noreferrer">Pssst — OSRS Companion App (Android)</a> &middot; <strong>RuneLite plugin repo:</strong> <a href="https://github.com/Pizzarar/Pssst---OSRS-Companion-App--RL" target="_blank" rel="noopener noreferrer">Pssst — OSRS Companion App (RuneLite)</a></p>

<p><strong>Release:</strong> signed <code>v1.0.0</code> Android APK (3,219,453 bytes, published 2026-10-20) — <a href="https://github.com/Pizzarar/Pssst---OSRS-Companion-App--Android/releases/tag/v1.0.0" target="_blank" rel="noopener noreferrer">download on GitHub Releases</a>. Both repositories carry a BSD-2-Clause license.</p>

## Overview &amp; Architecture

Pssst is a two-part system: a RuneLite plugin that runs inside the Old School RuneScape desktop client, and a native Android app that receives its output over the LAN.

**RuneLite plugin (Java 11).** The companion repo's entry point is `CompanionPlugin.java`, registered via `runelite-plugin.properties` (`displayName=Pssst Companion`, `author=Aub`, `plugins=com.pssst.runelite.CompanionPlugin`) and configured by `CompanionConfig.java`. Its build targets Java 11 (`release = 11`) with RuneLite `client:+`, Lombok, and JUnit 4. The core package includes `NetworkDispatcher.java` (an outbound-only LAN snapshot sender that never opens a listening port), plus snapshot/observation stores, pairing, delivery policy, item/price/icon bookkeeping, and bank/quest state tracking. Domain trackers live in `farming/FarmingTracker.java`, `birdhouse/BirdhouseTracker.java`, and `slayer/SlayerReader.java`.

**Android app (Kotlin + Jetpack Compose).** `app/build.gradle.kts` uses `jvmToolchain(17)`, Jetpack Compose (Material3 + Compose BOM), Navigation 3, WorkManager, Room, DataStore Preferences, and Gson; `namespace = "com.pssst"`, `minSdk = 24` (Android 7.0), `targetSdk = 36`, `compileSdk = 36`, `versionCode = 1`, `versionName = "1.0"`, with R8 minification enabled in release. The LAN receiver and ingest path is `receiver/PhoneReceiver.kt`, `receiver/ReceiverHost.kt`, `receiver/ReceiverPrefs.kt`, `data/SnapshotIngest.kt`, `data/StateDto.kt`, and Room persistence in `data/local/`. The UI is `ui/MainActivity.kt` plus ten screens under `ui/main/` (Overview, Storage, Inventory, Bank, Grand Exchange, Potion Storage, Progression, Timers, Dashboard, and Setup), themed by custom OSRS pixel-art components. Background work runs through WorkManager sync and reminder workers, with gameplay math in `util/`.

## Plugin Hub Status

The desktop plugin is functional via a **developer/sideload build** and is **not** listed on the official RuneLite Plugin Hub. It streams account telemetry outbound-only over the LAN to a configured phone address, so the app relies on the Android receiver rather than a bidirectional connection.

## Gallery

<div class="phone-hero">
<figure>
  <img src="/static/previews/pssst/overview.png" data-asset="proj-pssst-overview" data-final="static/previews/pssst/overview.png" width="444" height="927" alt="Pssst Android companion app Overview dashboard tab showing live Old School RuneScape account state">
  <figcaption>Overview dashboard tab — live account state on Android</figcaption>
</figure>
</div>

<div class="phone-grid">
<figure>
  <img src="/static/previews/pssst/timers-dailies.png" data-asset="proj-pssst-timers-dailies" data-final="static/previews/pssst/timers-dailies.png" width="444" height="973" alt="Pssst Android companion app Timers &amp; Dailies tab showing active OSRS timers and daily tasks">
  <figcaption>Timers &amp; Dailies tab</figcaption>
</figure>

<figure>
  <img src="/static/previews/pssst/storage.png" data-asset="proj-pssst-storage" data-final="static/previews/pssst/storage.png" width="444" height="927" alt="Pssst Android companion app Storage &amp; Bank tab">
  <figcaption>Storage &amp; Bank tab</figcaption>
</figure>

<figure>
  <img src="/static/previews/pssst/exchange.png" data-asset="proj-pssst-exchange" data-final="static/previews/pssst/exchange.png" width="444" height="927" alt="Pssst Android companion app Grand Exchange offers tab">
  <figcaption>Grand Exchange offers tab</figcaption>
</figure>

<figure>
  <img src="/static/previews/pssst/progress.png" data-asset="proj-pssst-progress" data-final="static/previews/pssst/progress.png" width="444" height="973" alt="Pssst Android companion app Progression &amp; goals tab">
  <figcaption>Progression &amp; goals tab</figcaption>
</figure>
</div>

<figure>
  <img src="https://placehold.co/1200x750/1e1c40/ff6fa5?text=proj-pssst-architecture" data-asset="proj-pssst-architecture" data-final="assets/img/proj-pssst-architecture.webp" width="1200" height="750" alt="Pssst architecture diagram — RuneLite plugin to Android companion data flow">
  <figcaption>RuneLite plugin → LAN → Android app data flow</figcaption>
</figure>
