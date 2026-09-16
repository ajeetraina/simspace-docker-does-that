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

# Not one whale and one Dockerfile

<svg viewBox="0 0 900 300" width="100%" role="img" aria-label="A grid of Docker building blocks: Desktop, Engine, Compose, Hub, Build Cloud, Scout, Hardened Images, Testcontainers, Gordon, Model Runner, MCP Toolkit, Sandboxes.">
  <g font-family="ui-sans-serif, system-ui, sans-serif" font-size="17" font-weight="700">
    <rect x="10"  y="10"  width="210" height="66" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="115" y="49" text-anchor="middle" fill="#0b214a">Docker Desktop</text>
    <rect x="234" y="10"  width="210" height="66" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="339" y="49" text-anchor="middle" fill="#0b214a">Docker Engine</text>
    <rect x="458" y="10"  width="210" height="66" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="563" y="49" text-anchor="middle" fill="#0b214a">Compose</text>
    <rect x="682" y="10"  width="208" height="66" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="786" y="49" text-anchor="middle" fill="#0b214a">Docker Hub</text>
    <rect x="10"  y="90"  width="210" height="66" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="115" y="129" text-anchor="middle" fill="#0b214a">Build Cloud</text>
    <rect x="234" y="90"  width="210" height="66" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="339" y="129" text-anchor="middle" fill="#0b214a">Docker Scout</text>
    <rect x="458" y="90"  width="210" height="66" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="563" y="129" text-anchor="middle" fill="#0b214a">Hardened Images</text>
    <rect x="682" y="90"  width="208" height="66" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="786" y="129" text-anchor="middle" fill="#0b214a">Testcontainers</text>
    <rect x="10"  y="170" width="210" height="66" rx="12" fill="#e6f4ea" stroke="#1a7f37"/><text x="115" y="209" text-anchor="middle" fill="#14532d">Gordon</text>
    <rect x="234" y="170" width="210" height="66" rx="12" fill="#e6f4ea" stroke="#1a7f37"/><text x="339" y="209" text-anchor="middle" fill="#14532d">Model Runner</text>
    <rect x="458" y="170" width="210" height="66" rx="12" fill="#e6f4ea" stroke="#1a7f37"/><text x="563" y="209" text-anchor="middle" fill="#14532d">MCP Toolkit</text>
    <rect x="682" y="170" width="208" height="66" rx="12" fill="#e6f4ea" stroke="#1a7f37"/><text x="786" y="209" text-anchor="middle" fill="#14532d">Sandboxes</text>
    <text x="10" y="278" font-size="15" font-weight="600" fill="#64748b">Blue: the platform you know   ·   Green: the AI building blocks that now ship in the box</text>
  </g>
</svg>

Note: When people think "Docker" they think one whale and one Dockerfile. But this
is the reality — an entire ecosystem of building blocks. The blue tiles are the
platform you know; the green row is the AI stack that now ships in the box. Hold this
thought: it's bigger than "package my app."

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

# Build · Test · Run · Ship

<svg viewBox="0 0 900 150" width="100%" role="img" aria-label="The developer lifecycle as a pipeline: Build, then Test, then Run, then Ship, with the capabilities that land on each beat.">
  <g font-family="ui-sans-serif, system-ui, sans-serif">
    <rect x="10"  y="30" width="190" height="72" rx="12" fill="#0b214a"/><text x="105" y="66" text-anchor="middle" font-size="20" font-weight="800" fill="#ffffff">BUILD</text><text x="105" y="90" text-anchor="middle" font-size="12" fill="#8fb6e6">Gordon · DHI</text>
    <rect x="238" y="30" width="190" height="72" rx="12" fill="#0b214a"/><text x="333" y="66" text-anchor="middle" font-size="20" font-weight="800" fill="#ffffff">TEST</text><text x="333" y="90" text-anchor="middle" font-size="12" fill="#8fb6e6">Testcontainers</text>
    <rect x="466" y="30" width="190" height="72" rx="12" fill="#0b214a"/><text x="561" y="66" text-anchor="middle" font-size="20" font-weight="800" fill="#ffffff">RUN</text><text x="561" y="90" text-anchor="middle" font-size="12" fill="#8fb6e6">Sandboxes</text>
    <rect x="694" y="30" width="196" height="72" rx="12" fill="#0b214a"/><text x="792" y="66" text-anchor="middle" font-size="20" font-weight="800" fill="#ffffff">SHIP</text><text x="792" y="90" text-anchor="middle" font-size="12" fill="#8fb6e6">Scout (across all)</text>
    <g fill="#2496ed">
      <polygon points="200,66 238,66 238,60 252,68 238,76 238,70 200,70"/>
      <polygon points="428,66 466,66 466,60 480,68 466,76 466,70 428,70"/>
      <polygon points="656,66 694,66 694,60 708,68 694,76 694,70 656,70"/>
    </g>
  </g>
</svg>

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

# Build · Run · Ship **agents**

<svg viewBox="0 0 900 210" width="100%" role="img" aria-label="Docker as an AI company: three AI building blocks — Model Runner, Compose, MCP Toolkit — feeding the build, run, and ship of agents.">
  <g font-family="ui-sans-serif, system-ui, sans-serif">
    <rect x="10"  y="14" width="284" height="80" rx="12" fill="#e6f4ea" stroke="#1a7f37"/><text x="152" y="48" text-anchor="middle" font-size="18" font-weight="800" fill="#14532d">Model Runner</text><text x="152" y="74" text-anchor="middle" font-size="13" fill="#3f7a52">run LLMs locally, OpenAI-compatible</text>
    <rect x="308" y="14" width="284" height="80" rx="12" fill="#e6f4ea" stroke="#1a7f37"/><text x="450" y="48" text-anchor="middle" font-size="18" font-weight="800" fill="#14532d">Compose</text><text x="450" y="74" text-anchor="middle" font-size="13" fill="#3f7a52">models + agents in one file</text>
    <rect x="606" y="14" width="284" height="80" rx="12" fill="#e6f4ea" stroke="#1a7f37"/><text x="748" y="48" text-anchor="middle" font-size="18" font-weight="800" fill="#14532d">MCP Toolkit</text><text x="748" y="74" text-anchor="middle" font-size="13" fill="#3f7a52">tools your agent can call, governed</text>
    <g fill="#1a7f37"><polygon points="152,94 146,110 158,110"/><polygon points="450,94 444,110 456,110"/><polygon points="748,94 742,110 754,110"/></g>
    <rect x="10" y="120" width="880" height="72" rx="12" fill="#0b214a"/>
    <text x="450" y="152" text-anchor="middle" font-size="20" font-weight="800" fill="#ffffff">Build · Run · Ship AI agents — securely, local &amp; cloud</text>
    <text x="450" y="178" text-anchor="middle" font-size="13" fill="#8fb6e6">the same platform, one word changed: agents</text>
  </g>
</svg>

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

# One morning, five surprises, then lunch

<svg viewBox="0 0 900 200" width="100%" role="img" aria-label="Max's morning as a timeline: 09:00 Gordon, 09:45 Testcontainers, 10:30 Scout, 11:15 Hardened Images, 12:00 Sandboxes, then lunch.">
  <g font-family="ui-sans-serif, system-ui, sans-serif">
    <line x1="40" y1="100" x2="860" y2="100" stroke="#2496ed" stroke-width="4"/>
    <!-- nodes -->
    <circle cx="70"  cy="100" r="12" fill="#2496ed"/><text x="70"  y="70" text-anchor="middle" font-size="15" font-weight="800" fill="#0b214a">09:00</text><text x="70"  y="140" text-anchor="middle" font-size="14" font-weight="700" fill="#334155">Gordon</text>
    <circle cx="240" cy="100" r="12" fill="#2496ed"/><text x="240" y="70" text-anchor="middle" font-size="15" font-weight="800" fill="#0b214a">09:45</text><text x="240" y="140" text-anchor="middle" font-size="14" font-weight="700" fill="#334155">Testcontainers</text>
    <circle cx="410" cy="100" r="12" fill="#2496ed"/><text x="410" y="70" text-anchor="middle" font-size="15" font-weight="800" fill="#0b214a">10:30</text><text x="410" y="140" text-anchor="middle" font-size="14" font-weight="700" fill="#334155">Scout</text>
    <circle cx="580" cy="100" r="12" fill="#2496ed"/><text x="580" y="70" text-anchor="middle" font-size="15" font-weight="800" fill="#0b214a">11:15</text><text x="580" y="140" text-anchor="middle" font-size="14" font-weight="700" fill="#334155">Hardened Images</text>
    <circle cx="750" cy="100" r="12" fill="#2496ed"/><text x="750" y="70" text-anchor="middle" font-size="15" font-weight="800" fill="#0b214a">12:00</text><text x="750" y="140" text-anchor="middle" font-size="14" font-weight="700" fill="#334155">Sandboxes</text>
    <circle cx="860" cy="100" r="14" fill="#f59e0b"/><text x="860" y="70" text-anchor="middle" font-size="15" font-weight="800" fill="#92400e">12:30</text><text x="860" y="140" text-anchor="middle" font-size="14" font-weight="700" fill="#92400e">Lunch 🍽</text>
  </g>
</svg>

Note: The same plan, the fun version — Max's morning from Gordon at nine to
sandboxes at noon, then lunch. Build, run, share, security, together.
