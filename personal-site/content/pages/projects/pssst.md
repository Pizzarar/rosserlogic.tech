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
<span class="tag">Java 11</span>
<span class="tag">RuneLite API</span>
<span class="tag">LAN HTTP POST</span>
<span class="tag">WorkManager</span>
<span class="tag">Room</span>
</div>

<p><strong>Android repo:</strong> <a href="https://github.com/Pizzarar/Pssst---OSRS-Companion-App--Android" target="_blank" rel="noopener noreferrer">Pssst — OSRS Companion App (Android)</a> &middot; <strong>RuneLite plugin repo:</strong> <a href="https://github.com/Pizzarar/Pssst---OSRS-Companion-App--RL" target="_blank" rel="noopener noreferrer">Pssst — OSRS Companion App (RuneLite)</a></p>

<p><strong>Release:</strong> signed <code>v1.0.0</code> Android APK — <a href="https://github.com/Pizzarar/Pssst---OSRS-Companion-App--Android/releases/tag/v1.0.0" target="_blank" rel="noopener noreferrer">download on GitHub Releases</a>. Both repositories carry a BSD-2-Clause license.</p>

## Overview

When I step away from my desk in Old School RuneScape, I still want to know the moment a farming patch finishes, a birdhouse is ready to check, or a Grand Exchange offer fills. I don't want to leave a port open on my PC for that, and I don't want my account state routed through someone else's server. So I built Pssst.

It's a two-part companion. A RuneLite plugin runs inside the desktop client and pushes snapshots of my account **one-way over my home LAN** to a Kotlin app on my phone. The desktop plugin only ever sends — it never listens, never opens a port, and never touches the cloud. The phone app does the receiving and turns those snapshots into a dashboard of live timers, bank and inventory, Grand Exchange offers, and progression.

The desktop plugin runs as a **developer / sideload build** — it is functional, but it is **not** listed on the official RuneLite Plugin Hub.

## Under the Hood

- **Desktop (Java 11, RuneLite API):** `CompanionPlugin` as the entry point, with domain trackers for farming, birdhouses, and slayer, plus snapshot and observation stores feeding an outbound-only sender.
- **Outbound-only transport:** `NetworkDispatcher` POSTs to a configured phone address with exponential backoff and opens **zero** listening ports.
- **Android (Kotlin + Jetpack Compose):** the receiver host hands snapshots to a Room SQLite database and preferences repository, with WorkManager handling sync and reminders behind a 10-screen Compose UI.
- **Details live in code:** `CompanionPlugin`, `NetworkDispatcher`, `PhoneAddress`, `SnapshotStore`, `ObservationStore`, `PayloadFilter`, `FarmingTracker`, `BirdhouseTracker`, `SlayerReader` (plugin) · `PhoneReceiver`, `ReceiverHost`, `SnapshotIngest`, `StateDto`, `AppDatabase`, `UserPreferencesRepository`, `SyncWorker`, `ReminderWorker`, `ReminderPlanner`, `MainActivity` (app).

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
  <img src="/static/previews/pssst/architecture.svg" data-asset="proj-pssst-architecture" width="1200" height="640" alt="Pssst architecture diagram — RuneLite plugin to Android companion data flow">
  <figcaption>RuneLite plugin → LAN → Android app data flow</figcaption>
</figure>
