<!--
layout: section
eyebrow: "09:45 — time to write tests"
-->

# Your test needs a database.

So… a mock? Or that shared staging DB everyone fights over?

Note: The feature works; now the tests. It touches Postgres. Two bad-but-common
options: mock the database, or point at a shared test DB. Both hurt.

---

<!-- layout: split -->

# The problem

<!-- region -->

:tag[Mocks]{accent=red}

Drift from the real engine. Green tests, broken prod. You end up testing your mock,
not your query.

<!-- region -->

:tag[Shared infra]{accent=red}

Flaky, stateful, contended. One person's migration breaks everyone. "Works after I
re-seed."

Note: Mocks drift — you're testing your assumptions, not the database. Shared infra
is flaky and contended. What you want is the real engine, but throwaway.

---

# Testcontainers

Spin up a **real** dependency as a container **from inside your test suite**. It
starts before your tests, your code connects to it, and it's torn down
automatically after. Now a Docker project.

`Java` · `Go` · `Python` · `Node.js` · `.NET` · `Rust` — Postgres · Kafka · Redis · …

Note: Testcontainers puts a real database inside the test suite. It boots the
container, hands your test a connection string, and cleans up after. Libraries for
every major language. Docker acquired the project — it's first-party now.

---

# Real Postgres, per test run

```go filename=orders_test.go
func TestOrders(t *testing.T) {
    ctx := context.Background()

    // a real Postgres, started just for this test
    pg, err := postgres.Run(ctx, "postgres:17-alpine",
        postgres.WithDatabase("shop"),
        postgres.WithUsername("test"),
        postgres.WithPassword("test"),
    )
    require.NoError(t, err)
    defer pg.Terminate(ctx)          // gone when the test ends

    dsn, _ := pg.ConnectionString(ctx, "sslmode=disable")
    db := mustOpen(dsn)
    // ...run your real queries against a real engine...
}
```

:::card{label="Takeaway" accent=blue variant=fill}
Stop maintaining mocks. Stop fighting shared infra. **Real dependencies, isolated
per run.**
:::

Note: Look how little code. `postgres.Run` gives you a real engine; `defer
Terminate` cleans it up. No compose to babysit, no shared state. Every run is clean.
This gets the biggest "oh" from test-weary teams.
