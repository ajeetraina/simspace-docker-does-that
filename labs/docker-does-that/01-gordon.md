<!--
layout: section
eyebrow: "09:00 — coffee, editor, AI assistant"
-->

# Max lets an AI agent analyze his repo.

…and at first, it looks like it's doing a pretty good job.

**10 minutes later:** it proudly delivers a *really bad* Dockerfile. Instead of
letting a generic AI **guess** how to containerize the app, use something that
actually understands Docker. **Meet Gordon.**

Note: Nine AM, coffee in hand. Max points a general-purpose coding agent at the
repo. It looks confident — then hands back a bloated, root-running, single-stage
Dockerfile. The fix isn't "no AI." It's AI that knows Docker. That's Gordon.

---

<!--
layout: split
theme: dark
eyebrow: "09:00 — Gordon"
logo: assets/docker-logo-white.svg
-->

# **Gordon** — Docker's AI assistant

<!-- region -->

An AI-powered assistant for your Docker workflow, built **directly into Docker
Desktop and the CLI**.

:tag[Free]{accent=green} · :tag[Docker Desktop]{accent=blue} · :tag[`docker ai`]{accent=blue}

<!-- region -->

:::card{label="Analyzes" accent=blue variant=fill}
Reads your environment, proposes solutions, and runs commands **with your
permission**.
:::

:::card{label="Guides" accent=blue variant=fill}
Answers governance and implementation questions **in context**, and steers teams
toward best practices as they build.
:::

:::card{label="Debugs" accent=blue variant=fill}
Reads container logs and proposes fixes when things fail.
:::

Note: Gordon is the assistant baked into Docker Desktop and the docker CLI. It
doesn't just chat — it inspects your actual project, suggests the right move, and
executes only when you say yes. Governance questions, best-practice nudges, and
log-reading debugging all happen in context.

---

# Containerizing the app — with Gordon

```bash
$ docker ai "containerize this product catalog sample app"
```

Gordon inspects the repo and generates **three files** — a `.dockerignore`, a
multi-stage `Dockerfile` (Node 20 Alpine, non-root user, health check, ~270 MB),
and a `compose.yaml` wiring the full dev stack: app, Postgres, Kafka, LocalStack
(S3), and a mock inventory service.

<svg viewBox="0 0 900 130" width="100%" role="img" aria-label="Gordon reads the repo and generates three files: .dockerignore, a multi-stage Dockerfile, and compose.yaml.">
  <g font-family="ui-sans-serif, system-ui, sans-serif">
    <rect x="10" y="30" width="150" height="70" rx="12" fill="#0b214a"/><text x="85" y="62" text-anchor="middle" font-size="17" font-weight="800" fill="#ffffff">docker ai</text><text x="85" y="84" text-anchor="middle" font-size="12" fill="#8fb6e6">reads the repo</text>
    <polygon points="160,65 196,65 196,58 212,66 196,74 196,68 160,68" fill="#2496ed"/>
    <rect x="222" y="12" width="220" height="46" rx="10" fill="#eaf2fd" stroke="#2496ed"/><text x="332" y="40" text-anchor="middle" font-size="15" font-weight="700" fill="#0b214a">.dockerignore</text>
    <rect x="222" y="66" width="220" height="46" rx="10" fill="#eaf2fd" stroke="#2496ed"/><text x="332" y="94" text-anchor="middle" font-size="15" font-weight="700" fill="#0b214a">Dockerfile · multi-stage</text>
    <rect x="222" y="120" width="220" height="0" rx="10" fill="none"/>
    <rect x="460" y="39" width="430" height="52" rx="10" fill="#e6f4ea" stroke="#1a7f37"/><text x="675" y="62" text-anchor="middle" font-size="15" font-weight="700" fill="#14532d">compose.yaml</text><text x="675" y="81" text-anchor="middle" font-size="12" fill="#3f7a52">app · Postgres · Kafka · LocalStack (S3) · mock inventory</text>
  </g>
</svg>

:::card{label="Takeaway" accent=blue variant=fill}
Don't let a generic agent **guess** at Docker. Ask the one that **knows** it —
and it's already in Docker Desktop.
:::

Note: One prompt. Gordon reads the project and produces a sane, multi-stage,
non-root Dockerfile plus a working compose file for the whole stack — no guessing,
best practices by default. This is the "wait, Docker does that?" moment number one.
