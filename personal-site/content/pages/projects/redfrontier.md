---
title: "RedFrontier: Frontier Homestead"
image: /static/sprites/og-redfrontier.png
description: "RedFrontier is a public Lua RedM server project: a small-group PvE extraction sandbox with homesteads, A-Life outlaw camps, a tailor catalog and a 2869-test suite. In development."
extra:
  theme: night
  zone: personal
  nav_parent: "/personal"
  body_style: crt
  banner: redfrontier
---

<div class="tag-row">
<span class="tag">Lua 5.4</span>
<span class="tag">RedM (Cfx.re)</span>
<span class="tag">RSGCore</span>
<span class="tag">ox_lib</span>
<span class="tag">oxmysql</span>
<span class="tag">NUI (vanilla JS/HTML/CSS)</span>
</div>

<p><strong>Repo:</strong> <a href="https://github.com/Pizzarar/RedFrontier" target="_blank" rel="noopener noreferrer">github.com/Pizzarar/RedFrontier</a> (public repo; <strong>in development</strong>)</p>

## Overview

*Frontier Homestead* is the design name: a private, small-group (1 to 4 players) **PvE extraction sandbox** on RedM. The pillars are extraction tension, weight that matters, a functional home, soft consequences and no XP bars. The non-goals are PvP, 32+ players, a custom map and story missions (family questlines and an intro tutorial came later).

The *repo* is public. The *server design* is a private small-group one. This is not a public server you can join.

It sits on RSGCore, ox_lib and oxmysql, with Lua 5.4 on client and server, a vanilla JS/HTML/CSS NUI, OneSync, and a server-authoritative model for inventory, money, loot, heat and insurance. There are 24 custom `fh_` resources and 12 vendored third-party resources with pinned versions.

## Architecture

<figure class="flow">
<svg class="flow-svg" viewBox="0 0 360 488" role="img" aria-labelledby="rf-t" xmlns="http://www.w3.org/2000/svg"><title id="rf-t">RedFrontier architecture: selected fh_ resource dependencies from fxmanifest files, sitting on RSGCore, ox_lib, oxmysql and MariaDB</title><defs><marker id="rf" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="fl-ah" d="M0 0 L10 5 L0 10 z"/></marker></defs><g class="fl-n plain"><rect class="fl-box plain" x="20" y="8" width="320" height="46"/><text class="fl-t" x="180" y="27" text-anchor="middle">fh_core: shared hub</text><text class="fl-s" x="180" y="45" text-anchor="middle">every fh_* below declares it</text></g><g class="fl-n pink"><rect class="fl-box pink" x="20" y="84" width="150" height="38"/><text class="fl-t" x="95" y="108" text-anchor="middle">fh_alife</text></g><g class="fl-n teal"><rect class="fl-box teal" x="190" y="84" width="150" height="38"/><text class="fl-t" x="265" y="108" text-anchor="middle">fh_zones</text></g><g class="fl-n teal"><rect class="fl-box teal" x="20" y="148" width="150" height="38"/><text class="fl-t" x="95" y="172" text-anchor="middle">fh_trade</text></g><g class="fl-n teal"><rect class="fl-box teal" x="190" y="148" width="150" height="38"/><text class="fl-t" x="265" y="172" text-anchor="middle">fh_progression</text></g><g class="fl-n pink"><rect class="fl-box pink" x="20" y="212" width="150" height="38"/><text class="fl-t" x="95" y="236" text-anchor="middle">fh_homestead</text></g><g class="fl-n pink"><rect class="fl-box pink" x="190" y="212" width="150" height="38"/><text class="fl-t" x="265" y="236" text-anchor="middle">fh_tailor</text></g><g class="fl-n pink"><rect class="fl-box pink" x="20" y="276" width="150" height="38"/><text class="fl-t" x="95" y="300" text-anchor="middle">fh_inventory</text></g><g class="fl-n pink"><rect class="fl-box pink" x="190" y="276" width="150" height="38"/><text class="fl-t" x="265" y="300" text-anchor="middle">fh_economy</text></g><line class="fl-ln" x1="170" y1="103" x2="188" y2="103" marker-end="url(#rf)"/><line class="fl-ln" x1="95" y1="122" x2="95" y2="146" marker-end="url(#rf)"/><line class="fl-ln" x1="265" y1="212" x2="265" y2="188" marker-end="url(#rf)"/><line class="fl-ln" x1="265" y1="250" x2="265" y2="274" marker-end="url(#rf)"/><line class="fl-ln" x1="130" y1="250" x2="215" y2="274" marker-end="url(#rf)"/><g class="fl-n crt"><rect class="fl-box crt" x="20" y="366" width="150" height="50"/><text class="fl-t" x="95" y="385" text-anchor="middle">RSGCore</text><text class="fl-s" x="95" y="403" text-anchor="middle">rsg-core, rsg-*</text></g><g class="fl-n crt"><rect class="fl-box crt" x="190" y="366" width="150" height="50"/><text class="fl-t" x="265" y="385" text-anchor="middle">ox_lib/oxmysql</text><text class="fl-s" x="265" y="403" text-anchor="middle">database layer</text></g><line class="fl-ln fl-dash" x1="60" y1="314" x2="60" y2="364" marker-end="url(#rf)"/><text class="fl-s" x="68" y="347">provides rsg-inventory</text><line class="fl-ln" x1="265" y1="314" x2="265" y2="364" marker-end="url(#rf)"/><g class="fl-n crt"><rect class="fl-box crt" x="190" y="442" width="150" height="38"/><text class="fl-t" x="265" y="466" text-anchor="middle">MariaDB</text></g><line class="fl-ln" x1="265" y1="416" x2="265" y2="440" marker-end="url(#rf)"/></svg>
<figcaption>Selected dependencies, taken from each resource's fxmanifest. Solid arrows: depends on. Dashed: fh_inventory provides rsg-inventory. Every fh_ resource shown also declares fh_core.</figcaption>
</figure>

## Systems

- **Homesteads:** fixed plots in two classes. A free, large, raidable wilderness claim (`/fh_claim`) and a bought, small, law-safe town lot (`/fh_buylot`). One of each per character, with an owner-only chest per plot. *Plot positions are placeholders and are not checked in game.*
- **Economy and reputation:** money is cash. Reputation is tracked per region and can rise or fall. Every payment, charge and reputation change goes to a permanent ledger. Progression is a reputation tier of 1 to 3 per region, and only the Heartlands is set up so far.
- **A-Life:** clear an outlaw camp and the local law takes it over. Later an outlaw squad marches back and retakes it. The loop changes what a camp drops and how a region's trade shortages move.
- **Tailor catalog:** fitted outfits as progression. You start in a basic set, buy whole outfits at tailors and general stores, and earn some by hunting and quests. The catalog system is built, but the catalog content is **placeholder** (one starter outfit per sex) and `FittedOutfits` stays off until an in-game probe passes.
- **Also built:** core items, containers and the saddlebag, a forked inventory, buffs, outlaw-camp zones, death and drop bag, hunting and pelts, a roving fence trader, a gunsmith, hired hands, survival, crafting, roads (wagons, trade, heat), quests (a job board, three one-time family stories and an intro) and a tutorial.
- **Player wiki:** a wiki lives in the repo, written from what is built today. Where something is unverified in game, the page says so.

## Status: honest version

In development. Many systems are built and covered by specs but **not yet checked in game** (the wiki marks them "unverified"), so I won't call any of it playable. The tailor catalog content is placeholder. The repo has **no license file**, so it is a public repo, not an open-source release.

## Tests

153 pure-Lua spec files, run with the project's own runner (embedded Lua 5.4 through Python `lupa`). At commit `2beeb5d` on 2026-11-26 the runner reports **2869 tests across 153 specs, 0 failures**. These are unit specs. They do not replace in-game testing.

<div class="window window-crt readout">
<div class="window-bar"><span>run-specs.py · commit 2beeb5d · 2026-11-26</span><span class="controls" aria-hidden="true"></span></div>
<div class="window-body"><pre><code>$ python tools/run-specs.py
ok   spec/access_rules_spec.lua: 19 tests, 0 failures
ok   spec/alife_rules_spec.lua: 32 tests, 0 failures
ok   spec/alife_server_spec.lua: 38 tests, 0 failures
ok   spec/build_flow_spec.lua: 62 tests, 0 failures
...
TOTAL 153 specs, 2869 tests, 0 failures, 0 load errors
load-manifests: 36 resources, 601 files loaded, 2 system resources skipped
load-manifests: 4 findings (4 known, 0 unknown)
Ran 7 tests in 0.009s
OK</code></pre></div>
</div>

The 4 known findings are vendored resources that use Cfx-specific Lua syntax plain Lua cannot parse.

## Community Accolades / Credits

RedFrontier stands on other people's work. This is the repo's `CREDITS.md`, reproduced in full.

**Implemented RedM server base. Thanks to these projects:**

- **RSGCore** (rsg-core, rsg-inventory, rsg-character, rsg-weather, rsg-target, rsg-chat, rsg-loading, and the txAdminRecipe schema/config) by Rexshack-RedM / Rexshack Gaming: <a href="https://github.com/Rexshack-RedM" target="_blank" rel="noopener noreferrer">github.com/Rexshack-RedM</a>
- **fh_inventory** forked from **rsg-inventory** by Rexshack-RedM (stays GPL-3; see `server/resources/[fh]/fh_inventory/LICENSE`). Implemented fh_inventory — Thanks to rsg-inventory by Rexshack-RedM
- **ox_lib** and **oxmysql** by Overextended, maintained as CommunityOx forks: <a href="https://github.com/CommunityOx" target="_blank" rel="noopener noreferrer">github.com/CommunityOx</a>
- **cfx-server-data** (mapmanager, spawnmanager) by the Cfx.re collective (citizenfx)
- **MariaDB** portable server and **FXServer** are downloaded at setup time, not redistributed.

**Feature credits:**

- Implemented the friend allowlist (B-access) on rsg-core's ACE whitelist — Thanks to rsg-core by Rexshack-RedM
- Implemented A-Life — Thanks to S.T.A.L.K.E.R. A-Life by GSC Game World
- Implemented weapon/ammo use — Thanks to rsg-weapons by Rexshack-RedM (weapon, throwable and knife use; rsg-ammo by Rexshack-RedM opens the ammo boxes and saves ammo)
- Implemented catalog-style tailor/general-store clothing progression — Thanks to Red Dead Redemption 2 (single-player tailors and catalogs) by Rockstar Games (design idea only; no assets or text copied)

The A-Life system is inspired by the S.T.A.L.K.E.R. A-Life design. The repo's `server/VENDORED.md` lists exact versions of everything vendored.
