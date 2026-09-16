<!--
layout: image
image: assets/slide-32.png
alt: "12:00 - isolate the AI coding agent: you let an agent loose on your repo, and it has the exact same permissions you do"
chrome: false
-->

Note: Almost lunch. Max hands the repo to an autonomous agent for the last cleanup -
and it runs as him.

---

<!--
layout: image
image: assets/slide-33.png
alt: "Docker Sandboxes - a trust boundary around your agent: a microVM with its own kernel and dockerd; deny-by-default network; secrets via host proxy"
chrome: false
-->

Note: Sandboxes wraps the agent in a microVM - its own kernel, its own daemon, a
hypervisor boundary. Filesystem scoped, network deny-by-default, secrets never in
the VM.

---

<!--
layout: image
image: assets/slide-34.png
alt: "It's one command - standalone sbx, no Docker Desktop required: sbx run claude (or codex, gemini, copilot)"
chrome: false
-->

Note: The whole thing is one command. Give agents room to work without giving them
your machine. GA since Jan 2026 - free to try.

---

<!--
layout: section
eyebrow: "12:15 - and the tools the agent calls"
-->

# An agent is only as safe as the **tools** it can call.

Sandboxing *where the agent runs* is half the story. What about *what it reaches out to*?

Note: The sandbox contains the agent. But agents don't work alone - they call tools
over MCP: a GitHub server, a database server, a web-fetch server. Each one is code
you're now trusting, often `npx`-installed from who-knows-where, running with your
tokens. That's the other half of the surface.

---

# The problem

:::card{label="Ungoverned MCP" accent=red variant=fill}
Every MCP server is code you run with **your** credentials. Installed ad-hoc
(`npx some-mcp-server`), unversioned, unsigned - and it can read whatever your agent
can. A prompt-injected agent + an over-scoped tool is the whole **lethal trifecta**.
:::

Note: MCP is the USB port for AI - powerful, and exactly why you don't plug in random
sticks. Ad-hoc servers run unsandboxed with your secrets. Combine private data,
untrusted content, and the ability to act, and you have real exfiltration risk.

---

# Docker **MCP Toolkit & Catalog**

Curated, containerized MCP servers - governed the same way you govern images.

:::card{label="Catalog" accent=blue variant=fill}
**200+ verified servers** on Docker Hub. Signed and versioned - not `npx` from a
random repo.
:::

:::card{label="Containerized" accent=blue variant=fill}
Every server runs **in its own container**, isolated - pair it with `sbx` and the
tool is walled off too.
:::

:::card{label="Gateway + secrets" accent=blue variant=fill}
One **MCP Gateway** brokers every call; secrets come from Docker, **never** pasted
into agent config.
:::

Note: Docker's answer is to treat MCP servers like any other image: a curated catalog
of verified, signed, versioned servers; each one running in a container through a
single gateway that handles secrets and access. Same governance muscle you already
have for images, pointed at tools.

---

# One gateway, every tool

<svg viewBox="0 0 900 200" width="100%" role="img" aria-label="An agent talks to a single MCP Gateway, which brokers calls to containerized MCP servers - GitHub, Postgres, Fetch - each in its own container, with secrets injected by Docker.">
  <g font-family="ui-sans-serif, system-ui, sans-serif">
    <rect x="10" y="70" width="180" height="60" rx="12" fill="#0b214a"/><text x="100" y="98" text-anchor="middle" font-size="16" font-weight="800" fill="#ffffff">🤖 Agent</text><text x="100" y="118" text-anchor="middle" font-size="12" fill="#8fb6e6">in an sbx sandbox</text>
    <polygon points="190,100 226,100 226,92 246,101 226,110 226,102 190,102" fill="#2496ed"/>
    <rect x="250" y="60" width="180" height="80" rx="12" fill="#eaf2fd" stroke="#2496ed"/><text x="340" y="95" text-anchor="middle" font-size="16" font-weight="800" fill="#0b214a">MCP Gateway</text><text x="340" y="118" text-anchor="middle" font-size="12" fill="#3a5a86">brokers calls · injects secrets</text>
    <g fill="#1a7f37"><polygon points="430,80 466,80 466,72 486,81 466,90 466,82 430,82"/><polygon points="430,100 466,100 466,92 486,101 466,110 466,102 430,102"/><polygon points="430,120 466,120 466,112 486,121 466,130 466,122 430,122"/></g>
    <rect x="490" y="26" width="400" height="42" rx="10" fill="#e6f4ea" stroke="#1a7f37"/><text x="690" y="53" text-anchor="middle" font-size="14" font-weight="700" fill="#14532d">GitHub server · container</text>
    <rect x="490" y="79" width="400" height="42" rx="10" fill="#e6f4ea" stroke="#1a7f37"/><text x="690" y="106" text-anchor="middle" font-size="14" font-weight="700" fill="#14532d">Postgres server · container</text>
    <rect x="490" y="132" width="400" height="42" rx="10" fill="#e6f4ea" stroke="#1a7f37"/><text x="690" y="159" text-anchor="middle" font-size="14" font-weight="700" fill="#14532d">Fetch server · container</text>
  </g>
</svg>

:::card{label="Takeaway" accent=blue variant=fill}
Sandbox **where the agent runs** *and* govern **what it can call**. `sbx` + MCP
Toolkit close both halves of the loop.
:::

Note: Picture it end to end: the agent runs in a microVM, and every tool call goes
through one gateway to a containerized, signed server, with secrets handled by Docker.
Wall around the agent, wall around the tools. And with that, the morning's done -
time for lunch.
