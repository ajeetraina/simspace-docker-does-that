# Docker Sandboxes + MCP - isolate the agent AND the tools it calls

It's **12:00**. For the last cleanup, Max lets an autonomous coding agent loose on
the repo - and it has the **exact same permissions he does**. It can read every
file, use his **SSH keys and cloud tokens**, reach the whole network, and run
anything: `rm -rf`, or an `npm install` that pulls a poisoned package.

A plain container shares the host kernel - a fence, not a wall. For an agent in
"YOLO mode," you want a real boundary.

## Part 1 - Sandbox where the agent runs

**Docker Sandboxes** (the `sbx` CLI) wraps the agent in a lightweight **microVM**
with its own kernel and its own Docker daemon - a hard hypervisor wall:

- **Filesystem:** works on your code, can't touch the rest of your machine
- **Network:** deny-by-default; you allow-list what it may reach
- **Credentials:** secrets stay in your OS keychain; a host-side proxy injects them on outbound calls - never written to disk or into the VM

Run an agent inside a sandbox:

```bash
sbx run claude
```

One command - no Docker Desktop required. Swap `claude` for `codex`, `gemini`, or
`copilot`. The microVM boots, the network policy locks down, and the agent goes
live able to edit your code and **nothing else**.

## Part 2 - Govern the tools the agent calls (MCP)

Sandboxing *where the agent runs* is only half the story. Agents don't work alone -
they call tools over **MCP** (Model Context Protocol): a GitHub server, a database
server, a web-fetch server. Each one is code you now trust, often `npx`-installed
from who-knows-where, running with **your** credentials. A prompt-injected agent
plus an over-scoped tool is the whole **lethal trifecta**.

The **Docker MCP Toolkit & Catalog** treats MCP servers like any other image:
curated, signed, versioned, and containerized - governed the same way you already
govern images (including on **Docker Hardened Images**).

### 1. Browse the verified catalog

```bash
docker mcp catalog ls
```

200+ verified servers on Docker Hub - signed and versioned, not `npx` from a random
repo.

### 2. Enable the servers this project needs

```bash
docker mcp server enable github postgres
```

Each server runs **in its own container**, isolated. Pair it with `sbx` and the
tool is walled off too.

### 3. Start the MCP gateway

```bash
docker mcp gateway run
```

One **gateway** brokers every call and injects secrets from Docker - so tokens are
**never** pasted into agent config. Now the agent reaches its tools through a single,
audited, containerized front door.

> **Docker does that?!** Sandbox *where the agent runs* (`sbx`) **and** govern
> *what it can call* (MCP Toolkit). Together they close both halves of the loop -
> give agents room to work without giving them your machine or your credentials.

That's five capabilities, one morning, one product-catalog app - **before lunch.** 🐳
