<!--
layout: section
eyebrow: "12:00 — run the whole stack, then lunch"
-->

# You know Compose. You don't know these two.

Watch, and the long-requested jobs support.

Note: End of the morning: bring the whole stack up with Compose. Everyone knows
`compose up`. Two things you may have missed: Watch, and native jobs.

---

# Compose **Watch**

Edit code on your host → Compose **syncs or rebuilds** the affected service
automatically. No more manual `down`/`up` loops while you iterate.

```yaml filename=compose.yaml
services:
  web:
    build: .
    develop:
      watch:
        - action: sync          # copy changed files into the container
          path: ./src
          target: /app/src
        - action: rebuild       # rebuild when deps change
          path: package.json
```

Run it with `docker compose watch`.

Note: Watch turns Compose into a live-reload dev loop. `sync` copies changed files
straight in; `rebuild` kicks in when dependencies change. Replaces a lot of bespoke
nodemon/entr/volume hacks.

---

# Compose **jobs** — run-to-completion tasks

Migrations, seeders, batch tasks — declare them **in the Compose file** as tasks
that run once and exit 0, instead of gluing shell scripts around `compose up`.

```yaml filename=compose.yaml highlight=9-10
services:
  db:
    image: docker.io/dhi/postgres:17

  migrate:
    build: .
    command: ["./migrate", "up"]
    depends_on:
      db:
        condition: service_healthy
    deploy:
      mode: replicated-job      # run once, to completion (exit 0)
```

:::card{label="Takeaway" accent=blue variant=fill}
Compose isn't just long-running services anymore — **one-off jobs are
first-class**.
:::

Note: Jobs — one of the most-requested Compose features. A job runs to completion
and exits. Perfect for a migration that must finish before the app starts — note
`depends_on` with `service_healthy`. Notice the db is a Hardened Image — it all
connects.
