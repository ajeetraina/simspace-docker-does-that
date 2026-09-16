<!--
layout: image
image: assets/slide-27.png
alt: "10:30 - ship with secure images: you type FROM node:20 and inherit a few hundred packages you never asked for"
chrome: false
-->

Note: You package the service. The first line pulls a full base image - a shell, a
package manager, hundreds of libraries you'll never use but now have to patch.

---

<!--
layout: image
image: assets/slide-28.png
alt: "Docker Hardened Images - near-zero CVEs, SBOM + SLSA Build L3 + signatures, patched within ~24h, built on Debian & Alpine"
chrome: false
-->

Note: Hardened Images flip it: the base arrives patched and stripped down, with
SBOM, provenance, and signatures baked in.

---

<!--
layout: image
image: assets/slide-29.png
alt: "The problem - the patch treadmill: a standard base image is a large surface and keeping up is your ongoing job forever"
chrome: false
-->

Note: Most CVEs in your image aren't in your code - they're in the base.

---

<!--
layout: image
image: assets/slide-30.png
alt: "The problem - what 'yes to all' really means: the agent can use your SSH keys and cloud tokens and run anything"
chrome: false
-->

Note: A plain container shares the host kernel - a fence, not a wall. For an
autonomous agent in YOLO mode, you want a real boundary. (Sets up Sandboxes next.)

---

<!--
layout: image
image: assets/slide-31.png
alt: "Usually a one-line change - FROM node:20 becomes FROM dhi.io/node:20; base arrives pre-patched"
chrome: false
-->

Note: Adoption is usually just swapping the FROM line. The CVE treadmill becomes
someone else's job.
