<!--
layout: image
image: assets/slide-18.png
alt: "09:45 - Max needs a database to test the app. A mock? Or the shared staging DB everyone fights over?"
chrome: false
-->

Note: The feature works; now the tests. It touches Postgres. Two bad-but-common
options: mock it, or point at a shared test DB.

---

<!--
layout: image
image: assets/slide-19.png
alt: "Testcontainers - bringing the power of containers directly into the testing process"
chrome: false
-->

Note: An open-source library on the Docker API - real, ephemeral service instances
inside your test suite, no mocks.

---

<!--
layout: image
image: assets/slide-20.png
alt: "The problem - mocks drift from the real engine; shared test infra is flaky and contended"
chrome: false
-->

Note: You want the real Postgres, Kafka, Redis - but disposable, isolated, gone
when the test ends.

---

<!--
layout: image
image: assets/slide-21.png
alt: "Testcontainers - spin up a real dependency from inside your test suite. Java, Go, Python, Node.js, .NET, Rust."
chrome: false
-->

Note: It starts before your tests, your code connects, and it's torn down after.
Now part of Docker.

---

<!--
layout: image
image: assets/slide-22.png
alt: "Real Postgres, per test run - a Go example using postgres.Run and defer pg.Terminate"
chrome: false
-->

Note: Look how little code. Real dependencies, isolated per run.
