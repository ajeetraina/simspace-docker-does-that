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

## 1. Look at the current base

Gordon's :filelink[Dockerfile]{path="Dockerfile"} starts from the full `node:20`
base — the one Scout flagged:

```bash
cat Dockerfile
```

## 2. Swap to a hardened base — a one-line change

Adoption is usually **one line**: `FROM node:20` → `FROM dhi.io/node:20`. Apply it:

```bash
sed -i 's|node:20|dhi.io/node:20|' Dockerfile
```

Confirm the change landed — the base is now the patched, signed hardened image:

```bash
cat Dockerfile
```

## 3. Build on the hardened base

```bash
docker build -t my-app:latest .
```

## 4. Re-scan — the CVE count collapses

The same Scout command that **failed** the policy on `node:20` now **passes**:

```bash
docker scout quickview my-app:latest
```

> **Docker does that?!** Your base image arrives pre-patched. The CVE treadmill
> becomes someone else's job.

One last thing before lunch: Max hands the repo back to an autonomous agent.
