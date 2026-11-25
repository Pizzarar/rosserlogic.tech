---
title: "Homelab"
image: /static/sprites/og-homelab.png
description: "A small self-hosted lab that builds, tests and serves my projects: five instances, a private mesh network, and CI on every push."
extra:
  theme: day
  zone: pro
  nav_parent: "/work"
  body_style: crt
---

<div class="lab-banner"><img class="pixelated" src='/static/sprites/homelab-banner.png' width="1600" height="400" alt="Pixel-art night scene of a small home lab: a workstation desk and headless machines connected by glowing mesh lines"></div>

<p class="lead">A small self-hosted lab that builds, tests, and serves my projects.</p>

<p class="lab-note">The build and development instances run headless, tucked away out of the office. Status labels below are static, not live checks.</p>

## Instances

<div class="lab-grid">
  <article class="lab-card" aria-labelledby="lab-workstation">
    <img class="pixelated" src='/static/sprites/homelab-workstation.png' width="256" height="256" alt="Pixel-art workstation desk with two monitors and a desk lamp">
    <div class="lab-card-body">
      <h3 id="lab-workstation">Workstation</h3>
      <p class="lab-role">Primary workstation</p>
      <span class="lab-status lab-online"><span aria-hidden="true">&#9679;</span> ONLINE</span>
      <ul>
        <li>Daily driver; where most work starts.</li>
        <li>Control point for remote development and lab administration.</li>
      </ul>
    </div>
  </article>
  <article class="lab-card" aria-labelledby="lab-dev">
    <img class="pixelated" src='/static/sprites/homelab-dev.png' width="256" height="256" alt="Pixel-art headless machine on a shelf with several terminal panes">
    <div class="lab-card-body">
      <h3 id="lab-dev">Dev Node</h3>
      <p class="lab-role">Development instance</p>
      <span class="lab-status lab-online"><span aria-hidden="true">&#9679;</span> ONLINE</span>
      <ul>
        <li>Windows, headless, accessed remotely.</li>
        <li>Runs parallel AI coding agents for studio projects.</li>
      </ul>
    </div>
  </article>
  <article class="lab-card" aria-labelledby="lab-build">
    <img class="pixelated" src='/static/sprites/homelab-build.png' width="256" height="256" alt="Pixel-art headless tower with an amber beacon, a build progress readout and a sprite grid">
    <div class="lab-card-body">
      <h3 id="lab-build">Build Node</h3>
      <p class="lab-role">Build &amp; generation instance</p>
      <span class="lab-status lab-prov"><span aria-hidden="true">&#9680;</span> PROVISIONING</span>
      <ul>
        <li>Linux, headless; currently being built.</li>
        <li>Self-hosted CI runners that test every push before merge.</li>
        <li>GPU-accelerated image-generation pipeline that produces game sprites.</li>
      </ul>
    </div>
  </article>
  <article class="lab-card" aria-labelledby="lab-media">
    <img class="pixelated" src='/static/sprites/homelab-media.png' width="256" height="256" alt="Pixel-art small machine with an audiobook cassette and headphones">
    <div class="lab-card-body">
      <h3 id="lab-media">Media Node</h3>
      <p class="lab-role">Media instance</p>
      <span class="lab-status lab-online"><span aria-hidden="true">&#9679;</span> ONLINE</span>
      <ul>
        <li>Audiobookshelf audiobook server.</li>
        <li>Hosts game servers.</li>
      </ul>
    </div>
  </article>
  <article class="lab-card" aria-labelledby="lab-storage">
    <img class="pixelated" src='/static/sprites/homelab-storage.png' width="256" height="256" alt="Pixel-art multi-bay drive enclosure with activity lights">
    <div class="lab-card-body">
      <h3 id="lab-storage">Storage Node</h3>
      <p class="lab-role">Storage &amp; backup instance</p>
      <span class="lab-status lab-online"><span aria-hidden="true">&#9679;</span> ONLINE</span>
      <ul>
        <li>Central storage for the other instances.</li>
        <li>Backups for the other instances.</li>
      </ul>
    </div>
  </article>
</div>

## Topology

<figure class="lab-topo">
<svg viewBox="0 0 880 340" role="img" aria-labelledby="homelab-topo-title homelab-topo-desc" preserveAspectRatio="xMidYMid meet">
  <title id="homelab-topo-title">Homelab topology</title>
  <desc id="homelab-topo-desc">Inside a private mesh network: the workstation connects to the development instance, which pushes to the CI and build instance. The build instance sends sprites to storage and backups. The media instance and storage and backups exchange data in both directions.</desc>
  <defs>
    <marker id="lab-arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0 0 L10 5 L0 10 z" fill="var(--be-ink)"/></marker>
  </defs>
  <rect x="4" y="4" width="872" height="332" fill="var(--be-surface)" stroke="var(--be-ink)" stroke-width="3" stroke-dasharray="10 6"/>
  <text x="20" y="30" fill="var(--be-ink)" font-family="var(--font-pixel)" font-size="15" letter-spacing="1.5">PRIVATE MESH NETWORK</text>
  <g stroke="var(--be-ink)" stroke-width="3" fill="none" marker-end="url(#lab-arrow)">
    <line x1="228" y1="110" x2="312" y2="110"/>
    <line x1="548" y1="110" x2="632" y2="110"/>
    <line x1="730" y1="152" x2="730" y2="234"/>
  </g>
  <g stroke="var(--be-ink)" stroke-width="3" fill="none" marker-start="url(#lab-arrow)" marker-end="url(#lab-arrow)">
    <line x1="548" y1="280" x2="632" y2="280"/>
  </g>
  <g font-family="var(--font-pixel)" fill="var(--be-ink)" text-anchor="middle" font-size="13">
    <text x="270" y="90">(remote)</text>
    <text x="590" y="90">(push)</text>
    <text x="748" y="200" text-anchor="start">(sprites)</text>
    <text x="590" y="258">(data)</text>
  </g>
  <g stroke="var(--be-ink)" stroke-width="3" fill="var(--be-crt)">
    <rect x="40" y="68" width="188" height="84"/>
    <rect x="316" y="68" width="232" height="84"/>
    <rect x="636" y="68" width="188" height="84"/>
    <rect x="636" y="238" width="188" height="84"/>
    <rect x="316" y="238" width="232" height="84"/>
  </g>
  <g font-family="var(--font-pixel)" text-anchor="middle" fill="var(--be-phosphor)" font-size="18">
    <text x="134" y="104">Workstation</text>
    <text x="432" y="104">Dev Node</text>
    <text x="730" y="104">Build Node</text>
    <text x="730" y="274">Storage Node</text>
    <text x="432" y="274">Media Node</text>
  </g>
  <g font-family="var(--font-pixel)" class="lab-sub" text-anchor="middle" fill="var(--be-phosphor)" font-size="13">
    <text x="134" y="130">Primary workstation</text>
    <text x="432" y="130">Development instance</text>
    <text x="730" y="130">CI / build instance</text>
    <text x="730" y="300">Storage &amp; backups</text>
    <text x="432" y="300">Media instance</text>
  </g>
</svg>
<figcaption>Addresses, ports and network names are left out on purpose.</figcaption>
</figure>

## What it does for me

<ul class="lab-does">
  <li><strong>CI on every push without paid minutes.</strong> Self-hosted runners test every push before merge, with no metered cloud minutes.</li>
  <li><strong>Overnight sprite generation for <em>Escape From Idle</em>.</strong> The generation pipeline runs on a headless instance, off my main workstation.</li>
  <li><strong>Centralized backups.</strong> Project artifacts, sprites and media live on central storage with backups.</li>
  <li><strong>Remote access from anywhere without exposing ports.</strong> The instances talk over a private mesh network, with nothing listening publicly.</li>
</ul>

<div class="hero-actions"><a href="/work" class="btn btn-secondary">WORK</a><a href="/vibesquad" class="btn btn-secondary">VIBESQUAD</a></div>
