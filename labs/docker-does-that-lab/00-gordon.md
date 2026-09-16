# Gordon - the AI assistant that understands Docker

It's **09:00**. You're **Max**, and your task for the morning is to containerize the
**Product Catalog** app - following best practices.

## Meet the Product Catalog

A Node.js / Express service backing an online store - and it doesn't stand alone.
It talks to a database, an event bus, and object storage:

```text no-run-button
                         GET /products
                              │
                              ▼
                   ┌──────────────────────┐
                   │   Product Catalog     │
                   │   Node.js · Express   │
                   └───────────┬──────────┘
             ┌─────────────────┼──────────────────┐
             ▼                 ▼                   ▼
     ┌──────────────┐  ┌──────────────┐  ┌────────────────────┐
     │  PostgreSQL  │  │    Kafka     │  │       AWS S3        │
     │ product data │  │ update events│  │  product images    │
     └──────────────┘  └──────────────┘  │  (LocalStack · dev) │
                                          └────────────────────┘
             └───────────────▶ Inventory service (downstream · mocked in dev)
```

Take a look at what Max is starting with:
:filelink[README.md]{path="README.md"} · :filelink[server.js]{path="server.js"} · :filelink[package.json]{path="package.json"}

## A project with no container in sight

List the repo. It's **source only** - everything to *run* the app, nothing to
*ship* it:

```bash
tree
```

No `Dockerfile`, no `compose.yaml`. That's Max's job this morning.

## Ask Gordon to containerize the app

A generic coding agent will happily *guess* at a Dockerfile - and hand you a bloated,
root-running, single-stage mess. Instead, ask the assistant that actually knows
Docker: **Gordon**, built into Docker Desktop and the `docker` CLI.

The **Run** button types the command into the terminal and executes it:

```bash
docker ai "containerize this product catalog sample app"
```

Gordon inspects the repo, recognizes the Node.js service and its dependencies, and
scaffolds a `.dockerignore`, a multi-stage non-root `Dockerfile`, and a
`compose.yaml` for the whole dev stack - no guessing.

## See what Gordon wrote

The generated files now sit right alongside the source:

```bash
tree
```

Open them yourself - :filelink[Dockerfile]{path="Dockerfile"} is genuinely
multi-stage and runs as a non-root `node` user; :filelink[compose.yaml]{path="compose.yaml"}
wires up Postgres, Kafka, and LocalStack (S3) so the whole thing boots with one command.

## Bring the whole stack up

Don't take Gordon's word for it - run it. This is the *result* of the
containerization:

```bash
docker compose up
```

The app image builds from the multi-stage `Dockerfile`, its dependencies start,
and the service reports healthy on `:3000`.

## Verify it's really serving

```bash
curl localhost:3000/products
```

Real JSON comes back from the containerized service - the app Max started the
morning with is now running in a container, best practices and all.

> **Docker does that?!** The AI assistant is already in Docker Desktop, and it
> reasons about *your* project, not a generic template.

Next up: your feature works - now it needs tests, and tests need a database.
