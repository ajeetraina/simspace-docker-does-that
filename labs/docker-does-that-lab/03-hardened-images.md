# Docker Hardened Images — bases that arrive patched

It's **11:15**. Scout just failed the policy on CVEs Max didn't introduce — they
came from `FROM node:20`, which drags in a shell, a package manager, and hundreds of
packages he'll never use but now has to patch. That's the **patch treadmill**.

**Docker Hardened Images (DHI)** are base images that arrive **already patched and
minimal**. Docker maintains them; you inherit the work:

- **Near-zero CVEs**, minimal surface — no shell / package manager in runtime variants
- **SBOM** + **SLSA Build L3** provenance + cryptographic **signatures** on every image
- Critical CVEs patched fast — Docker targets **~24 hours**
- Now **free & open** (Apache 2.0) — 1,000+ images, built on Debian & Alpine

Adoption is usually a **one-line change** in the :filelink[Dockerfile]{path="Dockerfile"}:

```dockerfile no-run-button
# before — you own the patching
FROM node:20

# after — patched + minimal + signed
FROM dhi.io/node:20
```

## Build on the hardened base

```bash
docker build -t my-app:latest .
```

Then re-run Scout — the CVE count that failed your policy collapses:

```bash
docker scout quickview my-app:latest
```

> **Docker does that?!** Your base image arrives pre-patched. The CVE treadmill
> becomes someone else's job.

One last thing before lunch: Max hands the repo back to an autonomous agent.
