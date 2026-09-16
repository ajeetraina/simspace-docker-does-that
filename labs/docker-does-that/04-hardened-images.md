<!--
layout: section
eyebrow: "11:15 — ship with secure images"
-->

# You type `FROM node:20`

…and inherit a few hundred packages you never asked for.

Note: Scout just told you the base is the problem. First line of the Dockerfile
pulls a full base image — and with it a shell, a package manager, and hundreds of
libraries you'll never use but now have to patch.

---

# The problem

:::card{label="The patch treadmill" accent=red variant=fill}
A standard base image ships a large surface: OS packages, a shell, build tools.
Every one is a potential CVE, and keeping up is **your** ongoing job — forever.
:::

You wanted to ship a feature. Instead you're triaging vulnerabilities in software
you didn't write and don't use.

Note: Most CVEs in your image aren't in your code — they're in the base. And
patching them is a treadmill that never stops.

---

# Docker **Hardened Images** (DHI)

Base images that arrive **already patched and minimal**. Docker maintains them;
you inherit the work.

- **Near-zero CVEs**, minimal surface — no shell / package manager in runtime variants
- **SBOM** + **SLSA Build L3** provenance + cryptographic **signatures**, on every image
- Critical CVEs patched fast — Docker targets **~24 hours**
- Built on **Debian & Alpine** — familiar, not a new distro to learn

Now **free & open** (Apache 2.0) — 1,000+ images. Enterprise adds SLA-backed
remediation, FIPS/STIG.

Note: Hardened Images flip it: the base arrives patched and stripped down. SBOM,
provenance, signatures baked in. Big news from December 2025: over a thousand are
now free and open under Apache 2.0.

---

# Usually a one-line change

```dockerfile filename=Dockerfile highlight=5
# before — full base, you own the patching
# FROM node:20

# after — hardened base: patched + minimal + signed
FROM dhi.io/node:20

WORKDIR /app
COPY --chown=app:app . .
RUN npm ci --omit=dev
USER app
CMD ["node", "server.js"]
```

<svg viewBox="0 0 900 170" width="100%" role="img" aria-label="Re-running Scout after the one-line FROM swap: node:20 shows 2 critical and 14 high CVEs; dhi.io/node:20 shows 0 critical and 0 high.">
  <g font-family="ui-sans-serif, system-ui, sans-serif">
    <rect x="10" y="14" width="420" height="142" rx="12" fill="#fdeaea" stroke="#d64545"/>
    <text x="30" y="46" font-size="17" font-weight="800" fill="#7f1d1d">FROM node:20</text>
    <text x="30" y="78" font-size="15" fill="#7f1d1d">shell · package manager · 100s of packages</text>
    <text x="30" y="120" font-size="30" font-weight="800" fill="#d64545">2 Critical · 14 High</text>
    <text x="30" y="144" font-size="13" fill="#a15252">Scout policy: FAILED</text>
    <polygon points="440,85 476,85 476,76 496,86 476,96 476,87 440,87" fill="#2496ed"/>
    <rect x="470" y="14" width="420" height="142" rx="12" fill="#e6f4ea" stroke="#1a7f37"/>
    <text x="490" y="46" font-size="17" font-weight="800" fill="#14532d">FROM dhi.io/node:20</text>
    <text x="490" y="78" font-size="15" fill="#14532d">distroless · signed · SBOM + SLSA L3</text>
    <text x="490" y="120" font-size="30" font-weight="800" fill="#1a7f37">0 Critical · 0 High</text>
    <text x="490" y="144" font-size="13" fill="#3f7a52">Scout policy: PASSED ✓</text>
  </g>
</svg>

:::card{label="Takeaway" accent=blue variant=fill}
Your base image arrives **pre-patched**. The CVE treadmill becomes someone else's
job.
:::

Note: Adoption is usually just swapping the FROM line. Same Dockerfile shape.
Multi-stage and non-root patterns still apply. Re-run Scout after the swap and the
CVE count drops off a cliff — the two capabilities pair perfectly.
