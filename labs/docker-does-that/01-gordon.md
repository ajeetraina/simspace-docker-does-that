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

![Gordon containerizing the Product Catalog app in Docker Desktop](assets/gordon-desktop.png)

:::card{label="Takeaway" accent=blue variant=fill}
Don't let a generic agent **guess** at Docker. Ask the one that **knows** it —
and it's already in Docker Desktop.
:::

Note: One prompt. Gordon reads the project and produces a sane, multi-stage,
non-root Dockerfile plus a working compose file for the whole stack — no guessing,
best practices by default. This is the "wait, Docker does that?" moment number one.
