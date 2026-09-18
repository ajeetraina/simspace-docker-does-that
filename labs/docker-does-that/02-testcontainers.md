<!--
layout: image
image: assets/slide-14.png
alt: "09:45 - time to write tests. Max needs a database to test the app. A mock, or the shared staging DB everyone fights over?"
chrome: false
-->

Note: 09:45 - time to write tests. Max needs a database. A mock that drifts, or the
shared staging DB everyone fights over?

---

<!--
layout: image
image: assets/slide-15.png
alt: "Testcontainers - bringing the power of containers directly into the testing process."
chrome: false
-->

Note: Testcontainers - bringing the power of containers directly into the testing
process. Now part of Docker.

---

<!--
layout: image
image: assets/slide-16.png
alt: "The problem - mocks drift from the real engine; shared test infra means contention and flaky tests."
chrome: false
-->

Note: The problem - mocks drift from the real engine (green tests, broken prod);
shared test infra means contention.

---

<!--
layout: image
image: assets/slide-17.png
alt: "Testcontainers - spin up a real dependency as a container from inside your test suite. It starts before your tests, your code connects, and it's torn down automatically."
chrome: false
-->

Note: Testcontainers spins up a real dependency as a container from inside your
test suite - started before your tests, connected to, and torn down automatically.

---

<!--
layout: image
image: assets/slide-18.png
alt: "Real Postgres, per test run - a Go TestOrders example using Testcontainers to start a real Postgres just for the test."
chrome: false
-->

Note: Real Postgres, per test run. A Go example: TestOrders starts a real Postgres
just for this test, then tears it down.
