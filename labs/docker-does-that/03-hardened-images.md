<!--
layout: section
eyebrow: "10:30 — build the image"
-->

# You type `FROM node:20`

…and inherit a few hundred packages you never asked for.

Note: After the tests, you package the service. First line of the Dockerfile pulls
a full base image — and with it a shell, a package manager, and hundreds of
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
FROM docker.io/dhi/node:20

WORKDIR /app
COPY --chown=app:app . .
RUN npm ci --omit=dev
USER app
CMD ["node", "server.js"]
```

![Docker Hardened Images catalog on Docker Hub](assets/dhi-catalog.png)

:::card{label="Takeaway" accent=blue variant=fill}
Your base image arrives **pre-patched**. The CVE treadmill becomes someone else's
job.
:::

Note: Adoption is usually just swapping the FROM line. Same Dockerfile shape.
Multi-stage and non-root patterns still apply. The point: you stop owning
base-image CVEs.
