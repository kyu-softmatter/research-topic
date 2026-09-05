# `V1` · frontier — the maturity axis, positive pole

Distilled 2026-09-05 by the `T-013` procedure · status `draft` — **the first run of `T-013`, ever**
Axis: `X1` maturity · opposite pole [`V2` unfinished](V2-unfinished.md)
Contract: [`_common.md`](_common.md) · Related: `T-012` · `T-013` · `T-014` · `T-054` · `Q-005`

> **A persona is not an individual** (`T-018`). This file makes **no attribution by name**. The author lists of the sources below are ordinary citations and nothing is inferred from them about what any person values.

---

## 1. Value conditions

Constants. Written **before** the sources were found, per `T-013` step ①.

| ID | Condition |
|---|---|
| **`c1`** | A capability that did not exist ~5 years ago is now available — an instrument, an algorithm, a synthesis route, or a compute regime. |
| **`c2`** | The literature states the problem was **blocked on that capability**, not merely unstudied. |
| **`c3`** | The first result the new capability buys is **a measurement or a phase diagram**, not a demonstration of the capability itself. |

> **`c3` is the discriminator that does the work.** Without it the pole says yes to every new technique paper, and "we can now do X" becomes indistinguishable from "X is worth doing." **A capability demonstration is not a frontier; it is the thing that opens one.**

**Each condition can return `no`.** No new capability → `c1: no`. A capability arriving with no problem waiting for it → `c2: no`. **This was not automatic** — see `T-055`.

---

## 2. Sources

### ① Outlook — `T-012`①

| Source | DOI | Verified |
|---|---|---|
| Gompper et al., *The 2025 motile active matter roadmap*, *J. Phys. Condens. Matter* — **32 authors, open access** | `10.1088/1361-648X/adac98` | ✔ OpenAlex, 2026-09-05 |
| Gompper et al., *The 2020 motile active matter roadmap*, *J. Phys. Condens. Matter* — **37 authors, open access** | `10.1088/1361-648X/ab6348` | ✔ OpenAlex, 2026-09-05 |

**The condition appears in the 2025 abstract, in the literature's own words:**

> *"**With many fundamental properties of motile active matter now reasonably well understood and under control, the ground is prepared for** the study of physical aspects and mechanisms of motion in complex environments, of the behavior of systems with new physical features like chirality, of the development of novel micromachines and microbots, of the emergent collective behavior and swarming of intelligent self-propelled particles, and of particular features of microbial systems."*

**That sentence is `c1` and `c2` stated by the domain literature rather than by this repo.** It names the arrived capability ("now well understood and under control") and enumerates five directions it unblocks. This is what `C-008` ⓑ was for.

### ② Trajectory — `T-014`

**The instrument is the roadmap diff.** Two editions of the same article five years apart, author sets overlapping (37 → 32). What 2025 claims as newly attackable and 2020 does not is a `c1` candidate with **a locator at both ends**.

What 2025 adds and 2020 does not have: **non-reciprocal and non-additive interactions** · **sensing, information processing, and adjustment of motion** (with micro-robotics named as the engineering goal) · the five directions quoted above. What 2020 framed as the field's focus — **propulsion mechanisms** — 2025 treats as settled.

### ③ Measured trajectory

OpenAlex `title_and_abstract.search`, retrieved 2026-09-05. **Numbers are search results, not this repo's** ([charter.md](../charter.md) §5).

| Query | 2020 | 2025 | Growth | vs baseline |
|---|---:|---:|---:|---:|
| `non-reciprocal AND active matter` | 13 | 50 | **3.8×** | **2.4×** |
| `chiral AND active matter` | 48 | 161 | **3.4×** | **2.1×** |
| `active matter AND porous media` | 4 | 16 | **4.0×** | **2.5×** |
| `motility-induced phase separation` (2020-era core) | 41 | 84 | 2.1× | 1.3× |
| `active Brownian particle` — **field baseline** | 176 | 280 | 1.6× | 1.0× |

**`trajectory_check` verdict: `consistent`.** All three directions the 2025 roadmap names as newly opened grow 2–2.5× faster than the field baseline; the 2020-era core grows at near baseline. `non-reciprocal` inflects in 2021, flat at 8–16/yr for the six years before.

> **The baseline row is the methodological point, and it is a finding** (`T-055`). Without a denominator every topic in a growing field looks like a frontier. **A raw count cannot run this check.**
>
> **⚠ The queries are crude.** Keyword matching on title and abstract, no disambiguation. The counts are indicative and **are not a basis for a verdict on any single topic** — they support the claim that the 2025 roadmap's framing tracks the literature, and nothing narrower.

---

## 3. What was not done — `T-012`③

**The 2025 roadmap's own gap:** it claims the ground is prepared for *"emergent collective behavior and swarming of intelligent self-propelled particles"* while the abstract also states that **interactions are "often non-additive and non-reciprocal."** Non-additivity is named as a difficulty and is **not** among the five directions said to be ready. So the roadmap asserts a capability for collective behaviour and simultaneously names an unresolved obstacle to it.

**This is `V1`'s own weak point, and it belongs here rather than in a rebuttal:** by `c2`, a direction whose blocker is still named is not unblocked. **The nearest untouched adjacent area is the same-order question the roadmap does not raise** — whether the "well understood and under control" claim holds for *interacting* systems or only for dilute ones.

---

## 4. Trigger condition

Convened **once per topic** (BD `I-051`), when the topic is or could be tied to a capability that arrived recently.

**Re-convened only on hitting a wall**, and then what was tried and why it failed goes in with it.

**Convene `V2` at the same time or not at all.** One pole produces no `divergence/` → [`_common.md`](_common.md) §6.

---

## 5. Question habits

The shape this lineage's questions take. BD `I-053` — **a different search query per persona.**

- **"What became possible, and when exactly?"** Dates the capability. A capability with no arrival date is not a capability, it is a wish.
- **"What was this waiting for?"** Looks for the prior statement that it was blocked. If nobody said it was blocked, `c2` is `no`.
- **"What is the first number this buys?"** Forces `c3`. A question this pole cannot answer with a measurement or a phase diagram is a question about the technique, not the science.

**Search bias:** the recent end of the trajectory, and **method sections rather than Outlook sections** when checking `c1`. Diffing two editions of the same review is this pole's cheapest move.

---

## 6. Open against this pole

- **Everything above rests on abstracts.** The section-level content of both roadmaps was not read. `c2` in particular — *"the literature states it was blocked"* — needs the 2020 section that says so, and no such locator has been recorded. **The strongest claim here is verified at abstract resolution only.**
- **A five-year window is arbitrary.** `c1` says "~5 years" because that is the roadmap spacing, not because anything argues for it. **A threshold this repo should not be setting at all** → [charter.md](../charter.md) §3.
- **The pole is easy to satisfy dishonestly.** *"This is now possible"* is a sentence an LLM will always produce plausibly. `c3` and the measured trajectory are the only guards, and `c3` has never been tested against a real topic.
