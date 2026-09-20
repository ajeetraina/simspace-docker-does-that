<!--
layout: image
image: assets/slide-01.webp
alt: "Docker does that?! - Five Docker capabilities you may not know about. WeAreDevelopers 2026."
chrome: false
-->

Note: Title. "Docker does that?!" - five Docker capabilities you may not know
about. WeAreDevelopers 2026.

---

<!--
layout: image
image: assets/slide-02.webp
alt: "Meet your speakers - Kristiyan Velkov and Ajeet Singh Raina."
chrome: false
-->

Note: Meet your speakers - Kristiyan Velkov (Docker Captain) and Ajeet Singh Raina
(Developer Advocate).

---

<!--
layout: default
-->

<style>
/* DDT-NEXT-THEME: flat near-black to match the baked image slides */
.deck-canvas--dark { --docker-deep: #0B0F19; --deck-accent: #9db8ff; background: #0B0F19 !important; }
.bigshift { font-weight: 800; line-height: 1.08; letter-spacing: -0.015em;
  font-size: 4.7cqi; max-width: 20ch; margin: 0; }
.bigshift.punch { margin-top: 0.7em; }
.bigshift .accent { color: #f5c518; }
.productbar { margin-top: 1.2em; }
.productbar img { width: 70%; max-width: 1040px; border-radius: 8px; }
</style>

<div class="bigshift">
Docker isn't just a container company anymore.
</div>

:::fragment

<div class="bigshift punch">
It's an <span class="accent">AI company!</span>
</div>

<div class="productbar">

![Docker's AI products - model runner, compose, gordon, mcp gateway, mcp, mcp hub, mcp toolkit, sandboxes](assets/product-bar.webp)

</div>

:::

Note: The one-line thesis of this talk - Docker isn't just a container company
anymore, it's an AI company, building the platform to build, run, and ship agents
securely. Everything that follows is proof.

---

<!--
layout: split
-->

<style>
/* DDT-NEXT-THEME: flat near-black to match the baked image slides */
.deck-canvas--dark { --docker-deep: #0B0F19; --deck-accent: #9db8ff; background: #0B0F19 !important; }
/* THEN / NOW column headings, centered */
.deck-canvas--dark h2 { text-align: center; letter-spacing: 0.08em; margin-bottom: 0.7em; }
/* Software-stack logos as white tiles, echoing the ecosystem grid */
.stacklogos img { height: 40px; width: 40px; object-fit: contain; background: #fff;
  border-radius: 10px; padding: 9px; margin: 0 8px 8px 0; box-sizing: content-box;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.45); vertical-align: middle; }
/* Docker Hub content checklist */
.hubchecklist { list-style: none; padding: 0; margin: 0.3em 0 0; }
.hubchecklist li { position: relative; padding-left: 46px; margin: 17px 0; }
.hubchecklist li::before { content: ""; position: absolute; left: 0; top: 50%;
  transform: translateY(-50%); width: 26px; height: 26px; border-radius: 7px;
  border: 2px solid #3a4358; box-sizing: border-box; }
.hubchecklist li.checked::before { background: #2563eb; border-color: #2563eb; }
.hubchecklist li.checked::after { content: ""; position: absolute; left: 9px; top: 46%;
  transform: translateY(-60%) rotate(45deg); width: 7px; height: 13px;
  border: solid #fff; border-width: 0 3px 3px 0; }
</style>

<!-- region -->

## THEN

:::fragment

Docker Hub meant one thing - **millions of container images**.

<div class="stacklogos">

![Postgres](assets/logos/postgresql.svg)
![Redis](assets/logos/redis.svg)
![MongoDB](assets/logos/mongodb.svg)
![MySQL](assets/logos/mysql.svg)
![Kafka](assets/logos/kafka.svg)
![RabbitMQ](assets/logos/rabbitmq.svg)
![Elasticsearch](assets/logos/elasticsearch.svg)
![NGINX](assets/logos/nginx.svg)
![Node.js](assets/logos/nodejs.svg)
![Python](assets/logos/python.svg)
![Go](assets/logos/golang.svg)
![Rust](assets/logos/rust.svg)
![Grafana](assets/logos/grafana.svg)
![Spark](assets/logos/spark.svg)
![Kubernetes](assets/logos/kubernetes.svg)

</div>

:::

<!-- region -->

## NOW

:::fragment

Docker provides tools for working with AI across your development workflow.

<ul class="hubchecklist">
<li>Images</li>
<li>Helm Charts</li>
<li>Sandbox Kits</li>
<li>AI Models</li>
<li>Compose</li>
<li>Extensions</li>
<li>Plugins</li>
</ul>

:::

Note: Then and now. For years Docker Hub meant one thing - millions of container
images, every database, language, and framework. Not anymore: Docker Hub now hosts
Images, Helm Charts, Sandbox Kits, AI Models, Compose, Extensions, and Plugins. It
is not just a software stack anymore, it is an agentic stack too. (Builds: THEN
first, then NOW.)

---

<!--
layout: image
image: assets/slide-03.webp
alt: "Agenda - Gordon, Testcontainers, Docker Scout, Hardened Images, Sandboxes."
chrome: false
-->

Note: Agenda - the five capabilities: Gordon, Testcontainers, Docker Scout,
Hardened Images, and Sandboxes.

---

<!--
layout: image
image: assets/slide-04.webp
alt: "Docker Platform - build, run, and share software. Securely. Local and Cloud."
chrome: false
-->

Note: The Docker Platform - build, run, and share software, securely, across local
and cloud.

---

<!--
layout: image
image: assets/slide-05.webp
alt: "Docker AI Platform - build, run, and share AI agents. Securely. Local and Cloud."
chrome: false
-->

Note: The Docker AI Platform - build, run, and share AI agents, securely, across
local and cloud.

---

<!--
layout: default
-->

<style>
/* DDT-NEXT-THEME: flat near-black to match the baked image slides */
.deck-canvas--dark { --docker-deep: #0B0F19; --deck-accent: #9db8ff; background: #0B0F19 !important; }
.planeyebrow { color: #6b7fff; font-weight: 800; letter-spacing: 0.14em; font-size: 0.72em; }
.planrow { display: flex; gap: 20px; margin-top: 1.3em; }
.plancard { flex: 1; border-top: 4px solid #2563eb; padding-top: 14px; }
.plancard .t { font-weight: 700; font-size: 1.05em; color: #cbd5e1; }
.plancard .h { font-weight: 800; font-size: 1.15em; margin: 8px 0 10px; white-space: nowrap; }
.plancard .d { color: #9aa6c2; font-size: 0.92em; line-height: 1.3; }
</style>

<span class="planeyebrow">THE PLAN</span>

# One developer - Max. One morning. Five surprises.

<div class="planrow">
<div class="plancard"><div class="t">09:00</div><div class="h">Gordon</div><div class="d">AI assistant for Docker developers</div></div>
<div class="plancard"><div class="t">09:45</div><div class="h">Testcontainers</div><div class="d">A real DB in your tests</div></div>
<div class="plancard"><div class="t">10:30</div><div class="h">Docker Scout</div><div class="d">Base images arrive patched</div></div>
<div class="plancard"><div class="t">11:15</div><div class="h">Hardened Images</div><div class="d">Know what's inside. Enforce policy</div></div>
<div class="plancard"><div class="t">12:00</div><div class="h">Sandboxes</div><div class="d">Pair with an AI agent safely</div></div>
</div>

Note: The plan - one developer, Max. One morning. Five surprises, from 09:00
through 12:00: Gordon, Testcontainers, Docker Scout, Hardened Images, Sandboxes.

---

<!--
layout: image
image: assets/slide-08.webp
alt: "Task - Max has been asked to containerize the Product Catalog sample app, following best practices."
chrome: false
-->

Note: The task - Max has been asked to containerize the Product Catalog sample app,
following the best practices.

---

<!--
layout: image
image: assets/slide-09.webp
alt: "Section transition into Max's morning."
chrome: false
-->

Note: Transition into Max's morning.
