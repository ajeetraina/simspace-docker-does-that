# Gordon — the AI assistant that understands Docker

It's **09:00**. You're **Max**, and your task for the morning is to containerize the
**Product Catalog** app — following best practices.

A generic coding agent will happily *guess* at a Dockerfile — and hand you a bloated,
root-running, single-stage mess. Instead, ask the assistant that actually knows
Docker: **Gordon**, built into Docker Desktop and the `docker` CLI.

Take a look at what Max is starting with:
:filelink[README.md]{path="README.md"} · :filelink[server.js]{path="server.js"} · :filelink[package.json]{path="package.json"}

## Ask Gordon to containerize the app

The **Run** button types the command into the terminal and executes it:

```bash
docker ai "containerize this product catalog sample app"
```

Gordon inspects the repo, recognizes the Node.js service and its dependencies, and
scaffolds a `.dockerignore`, a multi-stage non-root `Dockerfile`, and a
`compose.yaml` for the whole dev stack — no guessing.

> **Docker does that?!** The AI assistant is already in Docker Desktop, and it
> reasons about *your* project, not a generic template.

Next up: your feature works — now it needs tests, and tests need a database.
