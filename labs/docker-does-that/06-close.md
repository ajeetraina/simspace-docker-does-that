<!--
layout: default
eyebrow: "The whole morning"
-->

# Five things Docker quietly does now

| Fits under | Capability          | In one line                              |
| ---------- | ------------------- | ---------------------------------------- |
| Build      | **Gordon**          | An AI assistant that understands Docker. |
| Build      | **Testcontainers**  | Real dependencies in your tests.         |
| Security   | **Docker Scout**    | Know what's inside; enforce policy.      |
| Build      | **Hardened Images** | Base images arrive patched.              |
| Run        | **Sandboxes + MCP** | A trust boundary around agents — and their tools. |

Build · Run · Share · Security — the same platform picture, made concrete.

Note: Recap the morning mapped back to the platform picture. Gordon, Testcontainers
and Hardened Images on the build side, Sandboxes on run, Scout as security across
all of it.

---

<!--
layout: section
theme: dark
eyebrow: "The point"
logo: assets/docker-logo-white.svg
-->

# Five capabilities. Before lunch. All free.

And most of it is **already installed** as part of your Docker setup. Pick one, use
it tomorrow — before lunch.

Note: The close I want them to remember: none of this needs a purchase order to
start, and most of it is already on their machine. Challenge: pick one and use it
tomorrow.

---

<!-- layout: split -->

# Thank you 🐳

<!-- region -->

**Docker does that. Now you know.**

- ✓ Gordon — `docker ai` & Docker Desktop
- ✓ Testcontainers — testcontainers.com
- ✓ Scout — `docker scout` & Docker Desktop
- ✓ Hardened Images — docker.com/products/hardened-images
- ✓ Sandboxes — the `sbx` CLI & docs
- ✓ MCP Toolkit — curated, containerized MCP servers

<!-- region -->

![QR code to the slides and links](assets/qr.png)

Note: Thank them, leave links up, point the QR at the repo/slides.

---

# Task complete 🐳

<svg viewBox="0 0 900 180" width="100%" role="img" aria-label="Task complete: the Product Catalog stack is up and healthy — app, Postgres, Kafka, and S3 all running — and the service is serving on port 3000.">
  <g font-family="ui-sans-serif, system-ui, sans-serif">
    <circle cx="70" cy="70" r="40" fill="#1a7f37"/><path d="M50,70 l14,14 l26,-30" stroke="#fff" stroke-width="7" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
    <text x="130" y="60" font-size="22" font-weight="800" fill="#0b214a">The stack is up and healthy</text>
    <text x="130" y="90" font-size="15" fill="#475569">GET /products → 200 · serving on :3000</text>
    <rect x="130" y="120" width="150" height="44" rx="10" fill="#e6f4ea" stroke="#1a7f37"/><text x="205" y="148" text-anchor="middle" font-size="14" font-weight="700" fill="#14532d">app ✔</text>
    <rect x="292" y="120" width="150" height="44" rx="10" fill="#e6f4ea" stroke="#1a7f37"/><text x="367" y="148" text-anchor="middle" font-size="14" font-weight="700" fill="#14532d">postgres ✔</text>
    <rect x="454" y="120" width="150" height="44" rx="10" fill="#e6f4ea" stroke="#1a7f37"/><text x="529" y="148" text-anchor="middle" font-size="14" font-weight="700" fill="#14532d">kafka ✔</text>
    <rect x="616" y="120" width="150" height="44" rx="10" fill="#e6f4ea" stroke="#1a7f37"/><text x="691" y="148" text-anchor="middle" font-size="14" font-weight="700" fill="#14532d">s3 ✔</text>
  </g>
</svg>

Note: Max's morning, done — the whole stack up and healthy, the app serving, and
it's lunchtime. Good code tastes better.

---

<!--
layout: section
eyebrow: "Now you try it"
-->

# Do it yourself — the hands-on lab

Everything Max did this morning is a **hands-on lab** next door: containerize with
Gordon, run Testcontainers, scan with Scout, swap to a hardened base, and sandbox an
agent — a simulated terminal, nothing to install.

**→ "Docker does that?! — Hands-on Lab"** — the second card on this workshop's landing page.

Note: Don't just watch — the companion lab lets everyone run the exact five
capabilities in a browser terminal. Point them at the second card on the landing
page. Great for the workshop slot right after this talk, or as self-paced follow-up.

---

<!--
layout: section
theme: dark
eyebrow: "Over to you"
logo: assets/docker-logo-white.svg
-->

# Q&A

What would you reach for first — before lunch?

Note: Open the floor. Common questions: how sandboxes differ from a plain
container, whether DHI needs a paid plan (no — 1,000+ are free), and how Scout
policy plugs into existing CI.

---

<!--
layout: split
theme: dark
eyebrow: "Connect with us"
-->

# Connect with us

<!-- region -->

:::card{label="Docker Captain" accent=blue variant=fill}
**Kristiyan Velkov**

- 𝕏 `@krisvelkov`
- in Kristiyan Velkov
:::

<!-- region -->

:::card{label="Developer Advocate" accent=blue variant=fill}
**Ajeet Singh Raina**

- 𝕏 `@ajeetsraina`
- in Ajeet Singh Raina
:::

Note: Point them at both of us — questions, slides, and the repo. Thanks for
spending the morning with us.
