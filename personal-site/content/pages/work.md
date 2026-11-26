---
title: "Work"
image: /static/sprites/og-projects.png
description: "Professional work: enterprise IT and ServiceNow automation, a ServiceNow AI triage workflow, VibeSquad, and a self-hosted homelab."
aliases:
  - /projects
extra:
  theme: day
  zone: pro
  body_style: crt
  banner: projects
---

<p class="lead">The professional side: enterprise IT, ServiceNow automation, and developer tooling.</p>

<section aria-labelledby="featured-title" id="featured">
<h2 id="featured-title">Featured</h2>
<div class="card-grid">
  <a class="card" href="#it-operations"><svg class="flow-svg card-thumb-svg" viewBox="0 0 1200 630" aria-hidden="true" focusable="false" xmlns="http://www.w3.org/2000/svg"><defs><marker id="wt" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="fl-ah" d="M0 0 L10 5 L0 10 z"/></marker></defs><g class="fl-n violet"><rect class="fl-box violet" x="15" y="190" width="360" height="250"/><text class="fl-t" x="195" y="311" text-anchor="middle">CMDB</text></g><g class="fl-n teal"><rect class="fl-box teal" x="420" y="190" width="360" height="250"/><text class="fl-t" x="600" y="311" text-anchor="middle">Refresh</text></g><g class="fl-n pink"><rect class="fl-box pink" x="825" y="190" width="360" height="250"/><text class="fl-t" x="1005" y="311" text-anchor="middle">Dashboards</text></g><line class="fl-ln" x1="377" y1="315" x2="416" y2="315" marker-end="url(#wt)"/><line class="fl-ln" x1="782" y1="315" x2="821" y2="315" marker-end="url(#wt)"/></svg><span class="card-label">ENTERPRISE IT</span><h3>Enterprise IT / ServiceNow</h3><p>Workflow design, CMDB cleanup (800+ models), management dashboards, and PowerShell recovery tooling.</p><div class="tag-row"><span class="tag">ServiceNow</span><span class="tag">CMDB</span><span class="tag">PowerShell</span></div></a>
  <a class="card" href="/projects/serbisenow"><img class="card-thumb" src="/static/sprites/og-serbisenow.png" width="1200" height="630" loading="lazy" alt="" aria-hidden="true"><span class="card-label">SERVICENOW SDK</span><h3>SerbiseNow</h3><p>A general ServiceNow AI enhancement-triage flow built with the ServiceNow SDK.</p><div class="tag-row"><span class="tag">ServiceNow SDK</span><span class="tag">Fluent</span><span class="tag">Triage</span></div></a>
  <a class="card" href="/vibesquad"><img class="card-thumb" src="/static/sprites/og-vibesquad.png" width="1200" height="630" loading="lazy" alt="" aria-hidden="true"><span class="card-label">DESKTOP APP</span><h3>VibeSquad</h3><p>Run coding agents as Squads: you talk ideas through with a brainstorm buddy, and a lead splits the plan up and sends each piece to the cheapest model that can handle it.</p><div class="tag-row"><span class="tag">Squads</span><span class="tag">Buddy + Lead</span><span class="tag">Desktop App</span></div></a>
  <a class="card" href="/homelab"><img class="card-thumb" src="/static/sprites/og-homelab.png" width="1200" height="630" loading="lazy" alt="" aria-hidden="true"><span class="card-label">SELF-HOSTED</span><h3>Homelab</h3><p>Five self-hosted instances on a private mesh network: CI on every push, sprite generation, central storage and backups.</p><div class="tag-row"><span class="tag">CI Runners</span><span class="tag">Self-Hosted</span><span class="tag">Backups</span></div></a>
</div>
</section>

<section aria-labelledby="itops-title" id="it-operations">
<h2 id="itops-title">Enterprise IT / ServiceNow</h2>
<p class="lead">The day job: enterprise IT and ServiceNow work.</p>
<ul>
  <li><strong>ServiceNow Endpoint Refresh Workflow, CMDB Normalization (800+ Models) &amp; Management Dashboards</strong>: I designed the endpoint refresh workflow to replace manual coordination, normalized 800+ inconsistent CMDB hardware-model entries, and built management and technician dashboards that provide self-service visibility.</li>
  <li><strong>ServiceNow Onboarding &amp; Platform Knowledge Base (Obsidian)</strong>: I authored a ServiceNow knowledge base in Obsidian that is the platform onboarding standard for new hires, and an advanced-functionality reference for current staff.</li>
  <li><strong>PowerShell Self-Service Remediation &amp; WinRE Offline Account-Recovery Toolkit</strong>: a failing application component was averaging 3+ tickets a day. I automated the fix into a self-service tool and co-developed a Windows Recovery Environment toolkit with an offline account-recovery module.</li>
</ul>
<figure class="flow">
<svg class="flow-svg" viewBox="0 0 360 393" role="img" aria-labelledby="wk-t" xmlns="http://www.w3.org/2000/svg"><title id="wk-t">Enterprise IT flow: free-text hardware models, CMDB normalization, endpoint refresh workflow, then manager and technician dashboards</title><defs><marker id="wk" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="fl-ah" d="M0 0 L10 5 L0 10 z"/></marker></defs><g class="fl-n plain"><rect class="fl-box plain" x="15" y="8" width="330" height="63"/><text class="fl-t" x="180" y="27" text-anchor="middle">Free-text hardware models</text><text class="fl-s" x="180" y="45" text-anchor="middle">800+ entries: variants, typos,</text><text class="fl-s" x="180" y="62" text-anchor="middle">invalid values</text></g><line class="fl-ln" x1="180" y1="71" x2="180" y2="93" marker-end="url(#wk)"/><g class="fl-n violet"><rect class="fl-box violet" x="15" y="95" width="330" height="63"/><text class="fl-t" x="180" y="114" text-anchor="middle">CMDB model normalization</text><text class="fl-s" x="180" y="132" text-anchor="middle">one standardized record per model</text><text class="fl-s" x="180" y="149" text-anchor="middle">reliable asset tracking</text></g><line class="fl-ln" x1="180" y1="158" x2="180" y2="180" marker-end="url(#wk)"/><g class="fl-n teal"><rect class="fl-box teal" x="15" y="182" width="330" height="80"/><text class="fl-t" x="180" y="201" text-anchor="middle">Endpoint refresh workflow</text><text class="fl-s" x="180" y="219" text-anchor="middle">trigger data</text><text class="fl-s" x="180" y="236" text-anchor="middle">task generation</text><text class="fl-s" x="180" y="253" text-anchor="middle">assignment logic</text></g><line class="fl-ln" x1="110" y1="262" x2="90" y2="286" marker-end="url(#wk)"/><line class="fl-ln" x1="250" y1="262" x2="270" y2="286" marker-end="url(#wk)"/><g class="fl-n pink"><rect class="fl-box pink" x="4" y="288" width="172" height="97"/><text class="fl-t" x="90" y="307" text-anchor="middle">Manager dashboard</text><text class="fl-s" x="90" y="325" text-anchor="middle">self-service queue</text><text class="fl-s" x="90" y="342" text-anchor="middle">totals, team loads,</text><text class="fl-s" x="90" y="359" text-anchor="middle">open demands and</text><text class="fl-s" x="90" y="376" text-anchor="middle">projects</text></g><g class="fl-n pink"><rect class="fl-box pink" x="184" y="288" width="172" height="97"/><text class="fl-t" x="270" y="307" text-anchor="middle">Tech dashboards</text><text class="fl-s" x="270" y="325" text-anchor="middle">assigned workload,</text><text class="fl-s" x="270" y="342" text-anchor="middle">instances, tasks,</text><text class="fl-s" x="270" y="359" text-anchor="middle">all in real time</text></g></svg>
<figcaption>How the enterprise refresh work fits together: clean the model data first, then drive the workflow, then give people self-service views. Generic illustration, no internal names.</figcaption>
</figure>
<p>Roles and employers are on the <a href="/resume">résumé</a>.</p>
</section>

<section aria-labelledby="after-title">
<h2 id="after-title">Looking for the games?</h2>
<p>Game and personal projects live in <a href="/personal">After Hours</a>: Idle Minds, Escape From Idle, RedFrontier, SportsBallBattles, and Pssst.</p>
</section>
