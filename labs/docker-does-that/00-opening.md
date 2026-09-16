<!--
layout: title
source: ""
-->

# Docker does that?!

Five Docker capabilities you may not know about.

Note: Welcome. Quick promise: five things Docker can do that most people don't
realize ship with the tools they already have. We'll walk through one ordinary
working morning and drop each capability in where it naturally fits. Everything is
free to try.

---

<!--
layout: split
theme: dark
eyebrow: "Whale, hello there 👋"
logo: assets/docker-logo-white.svg
-->

# Meet your speakers

<!-- region -->

:::card{label="Docker Captain" accent=blue variant=fill}
**Kristiyan Velkov** · `@krisvelkov`

11+ years in web development and DevOps. Docker Captain, Cursor Ambassador,
international speaker, and author of 4 technical books.
:::

<!-- region -->

:::card{label="Developer Advocate" accent=blue variant=fill}
**Ajeet Singh Raina** · `@ajeetsraina`

20+ years across system integration testing, consulting & DevRel. Former Docker
Captain; leads a 17,000-member Bengaluru meetup. Author of "Operational AI with
Docker."
:::

Note: Quick hellos, then straight into the platform — no long intros.

---

<!-- layout: split -->

# Agenda

<!-- region -->

:::card{label="01" accent=blue variant=fill}
**Gordon**
:::

:::card{label="02" accent=blue variant=fill}
**Testcontainers**
:::

:::card{label="03" accent=blue variant=fill}
**Docker Scout**
:::

<!-- region -->

:::card{label="04" accent=blue variant=fill}
**Docker Hardened Images (DHI)**
:::

:::card{label="05" accent=blue variant=fill}
**Docker Sandboxes and MCP**
:::

Note: Five stops this morning. Gordon, Testcontainers, Scout, Hardened Images, and
Sandboxes. Each one is something Docker quietly grew into that you can use today.

---

<!--
layout: image
image: assets/ecosystem-grid.png
alt: "A grid of technology logos — Docker provides an entire ecosystem of building blocks"
chrome: false
-->

Note: When people think "Docker" they think one whale and one Dockerfile. But this
is the reality — an entire ecosystem of building blocks. Hold this thought: it's
bigger than "package my app."

---

# Docker **Platform.**

Build, run, and share software. Securely — local and cloud.

:::card{label="Build" accent=blue}
**Build software.** Fast + secure.
:::

:::card{label="Run" accent=blue}
**Run software.** Safely.
:::

:::card{label="Share" accent=blue}
**Share software.** Versioned + governed.
:::

Note: The way to think about it today: a platform. Build, run, share software —
locally and in the cloud, with security and governance underneath. Every one of my
five capabilities lives somewhere on this picture.

---

# Docker **AI Platform.**

Build, run, and share AI **agents**. Securely — local and cloud.

:::card{label="Build" accent=green}
**Build agents.** Fast + secure.
:::

:::card{label="Run" accent=green}
**Run agents.** Safely.
:::

:::card{label="Share" accent=green}
**Share agents.** Versioned + governed.
:::

Note: Same frame, one word changed: agents. This is where a lot of the "wait,
Docker does that?" stuff has landed in the last year.

---

<!--
layout: image
image: assets/build-test-run-ship.png
alt: "Build. Test. Run. Ship. — the developer lifecycle, end to end"
chrome: false
-->

Note: Build, test, run, ship — the whole loop. Keep this arc in mind; the five
capabilities each land on one of these beats.

---

<!--
layout: section
theme: dark
eyebrow: "The shift"
logo: assets/docker-logo-white.svg
-->

# Docker isn't just a container company anymore.

It's an **AI company** — the platform to build, run, and ship agents, securely.

Note: Say it plainly and let it land. For a decade we knew Docker as the container
company. That's no longer the whole story. The five things I'm about to show you
are the proof, not the pitch. Model Runner, Compose, MCP Toolkit — the AI building
blocks now ship in the box.

---

<!--
layout: image
image: assets/the-shift-illustrated.png
alt: "The shift — Docker as an AI company: model runner, compose, mcp toolkit"
chrome: false
-->

Note: The same message, shown as the developer's mental model — build, run, ship
agents, with Model Runner, Compose, and the MCP Toolkit doing the heavy lifting.

---

<!--
layout: section
eyebrow: "The premise"
-->

# Most of us use Docker to package and ship an app.

That answer was **complete five years ago.** The toolchain has grown a lot — here's
where the newer pieces fit.

Note: Be honest with the room — raise your hand if you use Docker mainly to build
an image and ship it. That was a complete answer in 2020. It isn't anymore.

---

# One developer. One morning. Five surprises.

| Time  | Capability          | What it solves                          |
| ----- | ------------------- | --------------------------------------- |
| 09:00 | **Gordon**          | An AI assistant that *understands* Docker. |
| 09:45 | **Testcontainers**  | A real database in your tests.          |
| 10:30 | **Docker Scout**    | Know what's inside; enforce policy.     |
| 11:15 | **Hardened Images** | Base images arrive already patched.     |
| 12:00 | **Sandboxes**       | Pair with an AI agent — safely.         |

Maps onto **Build · Run · Share · Security** — the platform picture you just saw.

Note: Here's the morning. Roughly 4–5 minutes each. Don't memorize the clock — it's
a spine so each capability shows up when you'd actually reach for it. Gordon at
nine, sandboxes right before lunch.

---

<!-- layout: split -->

# **TASK:** Max should containerize the Product Catalog app

<!-- region -->

:::card{label="The task" accent=blue variant=fill}
Containerize the **Product Catalog** sample app — **following best practices**.
:::

One service, several real dependencies. We'll follow **Max** through one morning
and drop each capability in where he'd actually reach for it.

<!-- region -->

:tag[Application]{accent=blue} → :tag[PostgreSQL]{accent=green} · product data

:tag[Application]{accent=blue} → :tag[AWS S3]{accent=green} · product images

:tag[Kafka]{accent=green} → product updates → :tag[Inventory service]{accent=blue}

Note: Meet Max, our developer. His job this morning: containerize the Product
Catalog app the right way. It's a realistic shape — an app, Postgres, object
storage, a message broker, a downstream service. Keep this diagram in mind; every
capability maps to a real moment in this build.

---

<!--
layout: image
image: assets/the-plan-illustrated.png
alt: "The plan — one developer (Max), one morning, five surprises, then lunch"
chrome: false
-->

Note: The same plan, the fun version — Max's morning from Gordon at nine to
sandboxes at noon, then lunch. Build, run, share, security, together.
