# Testcontainers - a real database in your tests

It's **09:45**. The Product Catalog talks to Postgres, and Max needs to test it.
The two usual options both hurt:

- **Mocks** drift from the real engine - green tests, broken prod.
- **Shared test DBs** are flaky and contended - "works after I re-seed."

**Testcontainers** spins up a *real* dependency as a container **from inside your
test suite**. It starts before your tests, your code connects to it, and it's torn
down automatically after. Now a first-party Docker project.

Here's the test Max wrote - a real Postgres, started just for this run:
:filelink[orders_test.go]{path="orders_test.go"}

## Run the tests

```bash
go test ./...
```

Watch a real `postgres:17-alpine` container boot, the test run against it, and the
container get terminated when the test ends.

> **Docker does that?!** Real dependencies - Postgres, Kafka, Redis - isolated per
> run, with no shared infra to fight over. Libraries exist for Java, Go, Python,
> Node.js, .NET, and Rust.

Next: the image builds - but what's actually *inside* it?
