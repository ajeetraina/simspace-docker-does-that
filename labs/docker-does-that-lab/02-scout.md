# Docker Scout - know what's inside, enforce policy

It's **10:30**. Before Max pushes the image, one honest question: *what's actually
in it, and is it allowed to ship?* An image is layers of software from many sources
- and you usually find the answer **after** it ships.

**Docker Scout** looks inside any image, right from the CLI or Docker Desktop, and
turns "hope it's fine" into a **policy check**.

## 1. Look inside the image

```bash
docker scout quickview my-app:latest
```

An instant health summary. Want the full story? Try these too:

```bash
docker scout cves my-app:latest
docker scout recommendations my-app:latest
```

`cves` gives the full vulnerability breakdown plus an SBOM; `recommendations`
suggests a safer base to move to.

## 2. Gate the image on policy

```bash
docker scout policy my-app:latest
```

Pass/fail against your org's rules - the same check you'd run in CI. Right now it
**fails** on 2 high vulnerabilities inherited from the base image.

> **Docker does that?!** You know exactly what you ship, and you can block it on
> policy *before* it ever leaves your laptop.

The fix Scout hinted at - a safer base image - is next.
