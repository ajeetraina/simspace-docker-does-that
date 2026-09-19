# Docker Sandboxes - box the agent in, then hand it signed tools

It's **12:00**. For the last task, Max lets an autonomous coding agent loose on
the repo - and it has the **exact same permissions he does**. It can read every
file, use his **SSH keys and cloud tokens**, reach the whole network, and run
anything: `rm -rf`, or an `npm install` that pulls a poisoned package.

A plain container shares the host kernel - a fence, not a wall. For an agent in
"YOLO mode," you want a real boundary. And the boundary is only half the story:
the agent still has to *choose* things - like which base image to build on. Box it
in, then point it at **signed tools** so the choices it makes are the safe ones.

## What `sbx` is

**Docker Sandboxes** (the `sbx` CLI) runs an agent inside a lightweight
**microVM**. The agent still gets full permissions - but *inside the box*: its own
Docker daemon, its own network, and a **read-only** view of your host. A
prompt-injected or misbehaving agent cannot reach your host daemon or your
credentials, because from inside the sandbox they are not there.

- **Filesystem:** works on your code, host mounted **read-only**
- **Network:** deny-by-default; you allow-list what it may reach
- **Credentials:** stay in your OS keychain; nothing is written into the VM

## Set up the sandbox

One-time host setup - trust Docker's Homebrew tap, install the CLI, and start
the sandbox daemon.

Tells Homebrew that `docker/tap` is a trusted source for casks. This is a
**Homebrew** command — there is no `docker tap` CLI subcommand:

```bash
brew trust docker/tap
```

On older Homebrew you may see `brew tap docker/tap` instead of `brew trust` —
either works in this lab.

```bash
brew install docker/tap/sbx
```

```bash
sbx daemon start -d
```

Nothing is wired in yet. Confirm the sandbox has no MCP servers:

```bash
sbx mcp ls
```

## Govern the tools the agent calls (MCP)

Agents don't work alone - they call tools over **MCP** (Model Context Protocol):
a catalog server, a database server, a web-fetch server. Each one is code you now
trust, running with **your** credentials. A prompt-injected agent plus an
over-scoped tool is the whole **lethal trifecta**.

`sbx` governs this itself - no separate Docker CLI. It enforces a **Cedar**
access policy over three MCP actions: `register` a server, `invokeTool` on it, and
`invokePrimordial` (the built-in gateway primitives). In production you scope
`invokeTool` to the read-only tools and deny the mutating ones - so a
prompt-injected agent can *read* the hardened catalog but never rewrite it.

## Wire in the DHI MCP server

Docker hosts the **DHI MCP server** at `https://dhi.io/mcp` - a remote server the
agent queries to choose hardened base images (search by name, CVEs, attestations,
packages, or compliance). Register it **with the sandbox**, by URL - through `sbx`,
not the Docker CLI:

```bash
sbx mcp add remotedhi --url https://dhi.io/mcp
```

Inspect what you just added:

```bash
sbx mcp inspect remotedhi
```

It is a **remote** server over `streamable-http`. The tools it now exposes to the
sandboxed agent are read-only queries against Docker's hardened catalog -
`dhi_get_image_cves`, `dhi_get_image_details`, `dhi_get_image_packages`,
`dhi_get_tag_definition`, `dhi_list_repositories` - the same signed evidence you
measured by hand with Scout earlier. Confirm it registered:

```bash
sbx mcp ls
```

## Now let the agent build it

Drop the agent into the sandbox with the DHI MCP server statically attached, and
hand it the same containerize task - the one that first shipped `FROM node:20`
with a stack of high CVEs. Nothing about the prompt changes; only the environment
around the agent does:

```bash
sbx run claude --static-mcp remotedhi -p "Containerize the product-catalog app for production. Choose a hardened base image, keep the final image shell-free, and attach an SBOM."
```

Before it writes a single `FROM`, the agent calls `dhi_get_image_cves` and
`dhi_get_tag_definition` against Docker's hardened catalog, sees that
`dhi.io/node:20` carries near-zero CVEs and ships its own attestations, and *only
then* writes the Dockerfile. Measure what it produced with the same Scout command
from earlier:

```bash
docker scout quickview
```

Same hardened base you reached by hand in the last section - except the agent got
there on its own, unattended, inside a box it could not escape, from signed
catalog data it could not forge. **The fast path it took by itself *is* the
hardened one.**

## One file, the whole sandbox

You wired this box up one command at a time. A **sandbox environment file**
declares the same thing once - the agent, the DHI MCP server, and the governing
policy - so a teammate or a CI job recreates the identical box from a file
committed to the repo. Save it at the repo root as `.sbxenv.yaml`:

```yaml save-as=.sbxenv.yaml
schemaVersion: "1"
name: catalog-sandbox
agent: claude

workspace:
  path: product-catalog
  clone: true

# Scoped, read-only DHI governance - register + read the catalog, never rewrite it.
sandboxOptions:
  profile: dhi-readonly

mcp:
  servers:
    - name: remotedhi
      url: https://dhi.io/mcp
```

Now the commands you ran by hand collapse into one. `sbx env run` creates the
sandbox, registers `remotedhi`, applies the policy, and attaches you to the agent:

```bash
sbx env run
```

> **Docker does that?!** Box the agent in (`sbx` microVM) **and** govern what it
> can call (the DHI MCP server, wired through `sbx` and policy-gated). A boundary
> so a bad agent cannot reach your host, and a signed tool so a good agent checks a
> base image's CVEs *before* it commits to it - the safe path and the fast path
> become the same path.

That's five capabilities, one morning, one product-catalog app - **before lunch.** 🐳
