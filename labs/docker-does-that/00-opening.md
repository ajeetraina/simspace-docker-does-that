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
.bigshift { font-weight: 800; line-height: 1.12; letter-spacing: -0.015em;
  font-size: 6.6cqi; max-width: 15ch; margin: 0.2em 0 0; }
.bigshift .punch { display: block; margin-top: 1.1em; }
.bigshift .accent { color: #e8833a; }
</style>

<div class="bigshift">
Docker isn't just a container company anymore.
<span class="punch">It's an <span class="accent">AI company&nbsp;!</span></span>
</div>

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
layout: image
image: assets/slide-07.webp
alt: "The plan - one developer, Max, one morning, five surprises, from 09:00 to 12:00."
chrome: false
-->

Note: The plan - one developer, Max. One morning. Five surprises, from 09:00
through 12:00.

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
