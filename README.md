## oddballza

I build systems that have to **prove** they work rather than assert it — device
drivers talking to hardware nobody documented, and platforms whose correctness
has to survive six months and two upgrades.

That principle runs through everything here: a probe that finds nothing is
indistinguishable from a fact that is not there, so a check that only asserts
*existence* is not a check. Every verifier I write carries a positive control
that must be found and a negative control that must not. One whose controls
misbehave reports BROKEN — never PASS.

Twenty-five years in network and infrastructure architecture, development and DevSecOps — ISP core routing, secure hybrid infrastructure, CI/CD pipelines and regulated environments. This is where the code lives.

Twenty-five years in network and infrastructure architecture, development and DevSecOps
— ISP core routing, secure hybrid infrastructure, CI/CD pipelines and regulated
environments. This is where the code lives.

### Charter — controlled learning & capability platform

A multi-tenant platform for organisations that must demonstrate their training
delivery is correct, not merely claim it. Moodle for learning, WordPress and
WooCommerce for commerce, and the part that actually matters in between:
**repeatable provisioning that verifies itself.**

Anyone can install Moodle. The hard part is standing up a *configured* training
site — roles, policies, gating, enrolment, certificates, commerce — and proving
it is all still correct after two upgrades. Charter is that capability:
idempotent setup that re-asserts intended state after manual drift, a pipeline
that turns a source document into a gated course, and multi-layer verification
running from zero-install static checks up to real-browser regression journeys
against live tenants.

Per-tenant instances, because core Moodle has no tenancy model and regulated
customers require data isolation in procurement anyway. The shared asset is the
automation that provisions, verifies, upgrades and restores them — including a
proven backup, upgrade and rollback lifecycle, and interrupted-restore recovery
demonstrated by killing a real restore mid-flight and confirming it leaves a
reconcilable record rather than silent data loss.

GPL-3.0-or-later. Source is private while it is generalised out of a working
single-tenant deployment.

### Gadgetbridge — upstream contributions

[Gadgetbridge](https://codeberg.org/Freeyourgadget/Gadgetbridge) is the
cloudless replacement for gadget vendors' proprietary Android apps. Merged upstream
so far — full record with merge commits in
[openwatch](https://github.com/oddballza/openwatch):

- **Device drivers** — support for a previously unsupported watch in the Moyoung
  family, charging detection, on-demand blood-oxygen measurement, and fixes to
  log noise and state handling.
- **Body composition** — storage of raw bio-impedance from smart scales and
  estimation of the derived metrics, with derivation kept separate from storage
  so other drivers reuse both.
- **Dashboard** — weight, BMI, blood oxygen, heart rate and sleep-score widgets,
  including the empty and not-yet-measured states that are easy to forget.
- **Data freshness** — making measurements announce themselves, so the UI
  updates when a reading arrives instead of on the next manual refresh.

Open in review: a driver for a family of rebranded BLE scales, a framework
change letting drivers consume passive BLE advertisements instead of holding a
connection, and further body-composition widgets.

### [openwatch](https://github.com/oddballza/openwatch)

Reconnaissance and Gadgetbridge support for the MT55 (Moyoung V2 / Da Fit)
smartwatch — protocol research, diagnostics tooling, and an upstream
coordinator patch.

### Stack

| | |
|---|---|
| **Languages** | Python, Java, Kotlin, PHP, Bash |
| **Android** | background services, BLE GATT clients, settings screens, list and widget UI |
| **Platform** | Moodle, WordPress/WooCommerce, DDEV, idempotent provisioning, backup/upgrade/rollback lifecycle |
| **Persistence** | greenDAO, schema design, database migrations |
| **Serialisation** | Protocol Buffers, custom binary frame formats |
| **Testing** | JUnit, Mockito, Robolectric, real-browser regression journeys, control-verified check suites |
| **Protocol work** | HCI snoop log analysis, byte-level frame decoding, encrypted BLE advertisements (AES-CCM), clean-room reverse engineering from captures of my own hardware |

### How I work

- One concern per change. Small patches get reviewed; large ones get parked.
- Nothing is finished until a test has been watched to fail without it.
- Test fixtures are synthetic. Real measurements from real people are health
  data and stay out of repositories.
- Where hardware verification isn't possible, I say so plainly rather than
  implying it was.
- Findings get corroborated across independent captures before they are written
  down as fact.

**Elsewhere:** [Codeberg](https://codeberg.org/oddballza) · [LinkedIn](https://www.linkedin.com/in/nick-p-za/)
