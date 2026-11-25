---
title: "RedFrontier: Frontier Homestead"
image: /static/sprites/og-redfrontier.png
description: "RedFrontier is a public Lua RedM server project: a small-group PvE extraction sandbox with homesteads, A-Life outlaw camps, a tailor catalog and a 4806-check test suite. In development."
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

It sits on RSGCore, ox_lib and oxmysql, with Lua 5.4 on client and server, a vanilla JS/HTML/CSS NUI, OneSync, and a server-authoritative model for inventory, money, loot, heat and insurance. There are 23 custom `fh_` resources and 12 vendored third-party resources with pinned versions.

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

133 pure-Lua spec files, run with the project's own runner (embedded Lua 5.4 through Python `lupa`) or with `busted`. At commit `9c461b4`, the runner reports **4806 checks, 0 failures across 133 specs**. These are unit specs. They do not replace in-game testing.

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
