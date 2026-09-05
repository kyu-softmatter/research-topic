# Value lineages — discussion material

Drafted 2026-08-31 · revised 2026-08-31 (names removed · status lowered) · **superseded in part 2026-09-05** (`T-051` — the three axes replaced) · status `sketch`
Related: [ideas.md](../ideas.md) `T-009` · `T-012` · `T-013` · `T-018` · `T-035` · `T-051` · `C-002` · `C-008` · `C-009` · `Q-004`

> ## ⚠ Superseded in part — 2026-09-05
>
> **The three axes below are replaced by user decision** (`T-051`): `X1`
> reducibility · `X2` mechanism-vs-phenomenology · `X3` measurability are dropped
> for **trend · difficulty · impact**. **This file has not been rewritten**, so
> everything from §"3 axes / 6 poles" down — including the whole literature
> section — is **kept for the record, not for use.**
>
> **What survives the replacement:** the name-removal rule, the unit of division
> (a pole of a value axis, `T-018`), and the `T-013` procedure. **What does not:**
> the 21 literature rows, which were the only concrete material for `T-013`
> step ②, and `T-015`'s comparison path, which existed only because `V1`
> reduction had a reachable canonical author.
>
> **`C-008` is the open blocker.** The new axes are *meta* axes, so `T-012`'s
> canonical source — a review's Outlook section — has nothing to aim at.

> ## This document is not a decision
>
> **The 3-axis / 6-pole assignment and the literature lists below are discussion material** → [README.md](../../README.md) §0.
>
> **What the value axes are, and how many, is for Prof. Takatori to decide.** This file is written out concretely not because any of it is settled but **to give the discussion something specific to push against** — hearing "not that, and this one works like so" against a wrong draft is cheaper than asking "what are the value axes in active matter?" against a blank page.
>
> | In this document | Status |
> |---|---|
> | **The rule for removing names** (citations stay, attributions go) | **Decided** |
> | **Unit of division = a pole of a value axis** (`T-018`) | **Decided** |
> | **The distillation procedure** `T-013` (value condition → source → consistency) | **Decided** — inherited from BD `I-096` |
> | What the 3 axes and 6 poles are | **A draft. Expect replacement** |
> | Each pole's **value conditions** | **Empty.** Only the pole names exist |
> | The literature lists | **Material.** A `?` marks a DOI that was never verified |

## Where this document sits

[ideas.md](../ideas.md) is the **idea log**; this is **data**.

Its earlier name was `roster.md` (a roster of names). With the names gone it is not a roster.

---

## Why the names were removed

User instruction. `T-035` ("strip names before anything leaves") had this as a **later** step; it is done **at the definition stage** instead.

### The rule

> **Citations stay. Attributions go.**

| Kept | Removed |
|---|---|
| Literature citations, author names included. **Normal scholarship, no problem** | Sentences of the form *"this person considers X valuable"* |
| The location of a review's Outlook section (DOI + section number) | The roster of names itself |
| A lineage's body of literature | `[designated]` markers (they attach to names) |

### A second reason not to hold a roster here

**BD's roster already holds ~200 names.** Under `T-004` (index, do not migrate) this repo does not duplicate it. When an author filter is needed, reference [`BD:design/personas-roster.md`](https://github.com/kyu-softmatter/Brownian-Dynamics-Agent) — and note that those tags were assigned by **methodological canonicity** (BD `I-096`), a different axis from value assignment (`T-013`) to begin with (`Q-003`).

---

## What this revision also fixed — unanticipated

Removing names was instructed as a safety measure, but it **moved four design problems at once.**

| ID | Before | After |
|---|---|---|
| **`C-002`** person vs axis | Head-on collision with BD `I-067`. Open | **Transformed.** The unit of division became **a pole of a value axis** → §Unit of division |
| **`Q-004`** persona count | Person-based, so **no upper bound** | **Closed.** Back-derived from axes, hence finite — currently 3 axes / 6 poles |
| **`T-016`** role overlap | One person authoring J3 while also being a persona target → `trivially_satisfied` | **Sharply weakened.** A persona is not a specific individual, so the overlap is not structural |
| **`C-006`** integration obstacle | Attribution by name forces private, so no monorepo | **Relaxed** here, and **dissolved 2026-09-04** (`T-044`): removing names took the largest argument, and the decision to stay public took the rest → §Open |

> **The instruction turned out to be a route around `C-002`.** `T-010` argued that dividing by person was defensible, but not dividing was better — **the intent (seeing through researchers' research philosophies) carries over into lineages**, and so does the property that disagreement is the product (two poles per axis).

---

## Unit of division — a pole of a value axis

BD `I-067` had **one persona per axis.** The goal was orthogonality, so that verdicts never conflict.

Here it is **two per axis — the two poles.** The goal is the opposite: disagreement is the product (`T-010`).

```
value axis X?       the two poles attach opposite value to the same target
   |
   +-- V(a)  ---+
   |            +--> a divergence entry (kb-schema sec. 4.3)
   +-- V(b)  ---+        damped by resolvable_by (T-034)
```

**Convene one pole and no `divergence/` exists** → [`_common.md`](_common.md) §6.

---

## 3 axes / 6 poles — draft

| Axis | The question it splits on | Pole | Direction of the value condition |
|---|---|---|---|
| **X1 · reducibility** | Is being reducible to a thermodynamic or dimensionless quantity a condition of value? | **V1 reduction** | Reducible means valuable. Expressible as a stress, a pressure, an effective temperature |
| | | **V2 emergence** | A new state appearing in the lab means valuable. Reducibility is not a condition |
| **X2 · mechanism vs phenomenology** | Must the microscopic mechanism be established for it to be valuable? | **V3 mechanism** | Establishing the mechanism means valuable. Down to boundary conditions and chemical fields |
| | | **V4 minimal model** | Getting a phase diagram from a minimal model means valuable. Mechanism is irrelevant |
| **X3 · measurability** | Is there value in defining, theoretically, a quantity that cannot be measured? | **V5 measurement** | Measurable means valuable. Including probe perturbation and resolution |
| | | **V6 theoretical definition** | A consistent definition means valuable. Present measurability is not a condition |

> **`X1` is recommended as the Phase 1 test pair.** Reasons in §Phase 1.
> **`X3` has the same shape as a tension inside BD** — `A1` (measurability) against `A6` (nonequilibrium quantification). A footnote in BD's roster under `A6` already records it: *"using Stokes–Einstein as a `cross` path is not valid in an active system in the first place."*
> **The `divergence.axis` enum in [kb-schema.md](../kb-schema.md) §4.3 comes from this table** — `reducibility`, `mechanism_vs_phenomenology`, `measurability`. Since the table is a draft, so is the enum.

---

## Phase 1 — the test pair

**Why a pair and not one:** philosophy ⑤ (disagreement is the product) and `C-005` (the divergence schema) cannot be tested without a pair.

| Axis | Why this one | Why not |
|---|---|---|
| **X1 reducibility** ← **recommended** | ① both poles have **thick** bodies of literature ② **one pole's canonical author can be asked directly** (`T-015`) — so for `V1`'s value conditions a comparison path exists ③ dead centre of the group's own domain | — |
| **X2 mechanism** | The divergence shows plainly on the surface of the literature | No comparison path |
| **X3 measurability** | Maps onto a tension inside BD, so it feeds J3 directly | The poles are asymmetric — `V6`'s literature may be thin |

Settled at agenda 3 of the 2026-09-03 discussion.

---

## Literature entry points

**Material for step ② of the `T-013` procedure.** Start from literature, not from names — the same reason BD `I-068` established for its axis personas.

**Verification marks:** `✔` = carried in BD's roster, so already checked by the user · `?` = **proposed in this session and unverified.** DOIs get settled in Phase 1.

### X1 · reducibility

| Pole | Reference | Outlook | Verified |
|---|---|---|---|
| **V1** | Takatori, Yan & Brady, *PRL* **113** (2014) — swim pressure. The canonical source for BD `A5.E8` | original paper | ✔ |
| **V1** | Takatori & Brady, *Curr. Opin. Colloid Interface Sci.* (2016) | review | `?` |
| **V1** | Brady & Bossis, "Stokesian Dynamics", *Annu. Rev. Fluid Mech.* **20** (1988) | review | ✔ |
| **V1** | ten Hagen, van Teeffelen & Löwen, *JPCM* **23** (2011) — exact single-ABP MSD | original paper | ✔ |
| **V2** | Marchetti et al., "Hydrodynamics of soft active matter", *Rev. Mod. Phys.* **85** (2013) | **Outlook section** | ✔ |
| **V2** | Needleman & Dogic, *Nat. Rev. Mater.* **2** (2017) | review | `?` |
| **V2** | Palacci et al., *PRL* **105** (2010) — measured active sedimentation steady state | original paper | ✔ |

### X2 · mechanism vs phenomenology

| Pole | Reference | Outlook | Verified |
|---|---|---|---|
| **V3** | Anderson, "Colloid transport by interfacial forces", *Annu. Rev. Fluid Mech.* **21** (1989) | review | ✔ |
| **V3** | Golestanian, Liverpool & Ajdari (2005, 2007) — self-propelled phoretic particles | original papers | ✔ |
| **V3** | Lauga & Powers, *Rep. Prog. Phys.* **72** (2009) — hydrodynamics of microswimmers | review | ✔ |
| **V4** | Tailleur & Cates, *PRL* **100** (2008) — active steady-state density | original paper | ✔ |
| **V4** | Cates & Tailleur, "Motility-Induced Phase Separation", *Annu. Rev. Condens. Matter Phys.* **6** (2015) | review | `?` |
| **V4** | Stenhammar et al. (2014) — MIPS coarsening | original paper | ✔ |

### X3 · measurability

| Pole | Reference | Outlook | Verified |
|---|---|---|---|
| **V5** | Furst & Squires, *Microrheology* (Oxford, 2017) | **textbook — weak Outlook** | ✔ |
| **V5** | Crocker & Grier (1996) — particle-tracking algorithms | original paper | ✔ |
| **V5** | Savin & Doyle (2005) — static and dynamic errors in tracking | original paper | ✔ |
| **V6** | Harada & Sasa (2005) — the exact relation between FDT violation and dissipation | original paper | ✔ |
| **V6** | Cugliandolo (2011) — when an effective temperature holds | review | ✔ |
| **V6** | Sekimoto, *Stochastic Energetics* | textbook | ✔ |

> **`V5`'s first row is a candidate counterexample to `T-012`** — a textbook is **canonical for a method** but weak on Outlook. So **a pole thick in methodological canon may be thin in value canon.** Consistent with what `T-012` predicts, but it leaves open what `V5`'s value conditions get back-derived from.

---

## Special as a source of value — roadmap reviews

`T-012` names the **Outlook section of a review** as the source of value. If so, **roadmap-format reviews are the best entry point** — they collect many authors' Outlooks in one article.

| Reference | Why special | Verified |
|---|---|---|
| Gompper et al., *The 2020 motile active matter roadmap*, *J. Phys. Condens. Matter* **32** (2020) | **Dozens of Outlooks, separated section by section.** The structure already matches per-pole value-condition extraction | `?` — also check whether a newer edition exists |
| Bechinger et al., "Active particles in complex and crowded environments", *Rev. Mod. Phys.* **88** (2016) | Active particles broadly. Likely has an Outlook | `?` |
| Marchetti et al., *Rev. Mod. Phys.* **85** (2013) | Ten years of active matter compressed (BD `I-068`'s phrasing) plus an Outlook | ✔ |

> **This table is Phase 1's first target.**

---

## Open

- **All six pole assignments are drafts.** The `T-013` procedure (value condition → source → consistency) has never been run once. The current assignment **stands in for it, resting on impressions of the literature**, and although a pole's name reads like its value condition, **the conditions have not been written.**
- **Every `?` reference is unverified.** Settling DOIs is Phase 1's first task, and **the review list proposed in this session is not a basis for advancing the design.**
- **Names are gone and the repo stays public** — decided 2026-09-04 (`T-044`). Neither of `T-019`'s two reasons was retracted; both moved from gating visibility to constraining content. ① the topic assessments that will accumulate in the KB are unpublished research directions, so **there has to be a rule about what J1 may write, and it is unwritten** ② `X1`'s `V1` literature **overlaps the group's own output**, so without naming the lineage **the reading list points at it anyway** — now an accepted cost rather than a reason to close the repo. → [README.md](../../README.md) §8
- **How much practical difference there is between a pole pointing at a body of literature and pointing at a person.** The item above is the limit, and going public raises what it is worth: **how much of `T-035`'s name-stripping actually strips is still unmeasured**, and it now decides whether `V1`'s entry points need thinning rather than whether the repo is readable.
- **`V6`'s literature may be thin** — if `X3`'s poles are asymmetric, the divergence test is not a fair one.
