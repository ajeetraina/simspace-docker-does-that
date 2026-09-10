<!--
layout: section
eyebrow: "09:00 — coffee, editor, AI agent"
-->

# You let an agent loose on your repo.

…and it has the exact same permissions you do.

Note: Nine AM. You kick off an AI coding agent — Claude Code, Codex, Gemini,
whatever. You type "yes, run it." Great productivity. Also: that agent now runs
as you.

---

# The problem

:::card{label="What \"yes to all\" really means" accent=red variant=fill}
The agent can read every file, use your **SSH keys and cloud tokens**, reach the
whole network, and run anything — including `rm -rf` or an `npm install` that pulls
a poisoned package.
:::

A plain container shares the host kernel — a fence, not a wall. For an autonomous
agent in "YOLO mode," you want a real boundary.

Note: The risk isn't hypothetical. Agents delete the wrong directory, leak a token,
or install a compromised dependency. A container helps but shares the kernel.

---

# Docker **Sandboxes** — the `sbx` CLI

A **trust boundary** around your agent: it runs inside a lightweight **microVM**
with its own kernel and its own Docker daemon — a hard hypervisor wall between the
agent and your host.

:::card{label="Filesystem" accent=green}
Works on your code, can't touch the rest of your machine.
:::

:::card{label="Network" accent=green}
**Deny-by-default.** You allow-list what it may reach.
:::

:::card{label="Credentials" accent=green}
Secrets live in your OS keychain; a host-side proxy injects them on outbound calls
— never written to disk or into the VM.
:::

Note: Sandboxes wraps the agent in a microVM — its own kernel, its own daemon, a
hypervisor boundary. Even `rm -rf /` inside can't reach your host. Network is
deny-by-default. Credentials never land in the VM.

---

# It's one command

```bash
# standalone sbx — no Docker Desktop required
sbx run claude          # or: codex · gemini · copilot

# ✔ microVM booted  (own kernel · own dockerd)
# ✔ network policy: deny-by-default
# ✔ secrets: OS keychain → proxy (nothing written to VM)
```

![The sbx CLI booting a microVM sandbox](assets/sbx-run.png)

:::card{label="Takeaway" accent=blue variant=fill}
Give agents room to work **without** giving them your machine. GA since Jan 2026 —
free to try.
:::

Note: The whole thing is one command. Standalone CLI — works with Rancher Desktop
too, no Docker Desktop dependency. Room to work, without handing over the machine.
