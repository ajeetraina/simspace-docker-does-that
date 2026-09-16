# Docker Sandboxes - isolate the AI coding agent

It's **12:00**. For the last cleanup, Max lets an autonomous coding agent loose on
the repo - and it has the **exact same permissions he does**. It can read every
file, use his **SSH keys and cloud tokens**, reach the whole network, and run
anything: `rm -rf`, or an `npm install` that pulls a poisoned package.

A plain container shares the host kernel - a fence, not a wall. For an agent in
"YOLO mode," you want a real boundary.

**Docker Sandboxes** (the `sbx` CLI) wraps the agent in a lightweight **microVM**
with its own kernel and its own Docker daemon - a hard hypervisor wall:

- **Filesystem:** works on your code, can't touch the rest of your machine
- **Network:** deny-by-default; you allow-list what it may reach
- **Credentials:** secrets stay in your OS keychain; a host-side proxy injects them on outbound calls - never written to disk or into the VM

## Run an agent in a sandbox

```bash
sbx run claude
```

One command - no Docker Desktop required. Swap `claude` for `codex`, `gemini`, or
`copilot`. The microVM boots, the network policy locks down, and the agent goes
live able to edit your code and **nothing else**.

> **Docker does that?!** Give agents room to work *without* giving them your
> machine. GA since Jan 2026 - free to try.

That's five capabilities, one morning, one product-catalog app - **before lunch.** 🐳
