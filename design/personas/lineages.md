# Value lineages — discussion material

Drafted 2026-08-31 · revised 2026-08-31 (names removed · status lowered) · **rewritten 2026-09-05** (`T-051` axes replaced, then restated per `C-008` ⓑ) · status `sketch`
Related: [ideas.md](../ideas.md) `T-009` · `T-012` · `T-013` · `T-018` · `T-035` · `T-051` · `T-054` · `C-002` · `C-008` · `C-009` · `Q-004` · `Q-005`

> ## ⚠ The axes were replaced — 2026-09-05
>
> **Twice, in one day.** `T-051` dropped `X1` reducibility · `X2`
> mechanism-vs-phenomenology · `X3` measurability for the user's list of
> trend · difficulty · impact. Those hit `C-008` — as **meta** axes they left
> `T-012`'s canonical source with nothing to aim at — and **`C-008` ⓑ was then
> chosen: restate each axis so it anchors in domain literature.** The result is
> `X1` maturity · `X2` obstruction · `X3` reach, in §The axes.
>
> **What survived both replacements:** the name-removal rule, the unit of
> division (a pole of a value axis, `T-018`), and the `T-013` procedure.
>
> **What did not:** the 21 per-pole literature rows, which belonged to the
> original poles and are not translatable to the new ones — they are in git
> history at `d68065c`. `T-015`'s comparison path also stays dead: it existed
> only because `V1` reduction had a reachable canonical author, and there is no
> reduction pole.
>
> **Still empty:** every pole's value conditions. The restatement gave `T-013`
> step ② a target; it did not run the procedure. **That is Phase 1.**

> ## This document is not a decision
>
> **The 3-axis / 6-pole assignment and the literature lists below are discussion material** → [README.md](../../README.md) §0.
>
> **The axes are now the user's call, not Takatori's** — that changed on 2026-09-05 (`T-051`, superseding `T-040`'s handover on this one row). **What has not changed is that the file is still written to be pushed against**: hearing *"not that, and this one works like so"* against a concrete draft is cheaper than asking *"what are the value axes?"* against a blank page.
>
> | In this document | Status |
> |---|---|
> | **The rule for removing names** (citations stay, attributions go) | **Decided** |
> | **Unit of division = a pole of a value axis** (`T-018`) | **Decided** |
> | **The distillation procedure** `T-013` (value condition → source → consistency) | **Decided** — inherited from BD `I-096` |
> | **The three dimensions** — trend · difficulty · impact | **Decided** (`T-051`, user) |
> | **That each is restated to anchor in domain literature** | **Decided** (`C-008` ⓑ, user) |
> | The **specific restatement** — maturity · obstruction · reach, and the six poles | **A draft.** Derived, not instructed. This is the row to push against |
> | Each pole's **value conditions** | **Empty.** Only the pole names exist |
> | The literature lists | **The per-pole tables are retired.** What remains is the roadmap-review list → §Special |

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

**Replaced twice.** `T-051` dropped the original domain axes (reducibility · mechanism · measurability) for the user's list — trend · difficulty · impact. Those ran straight into `C-008`: they are **meta axes**, so `T-012`'s canonical source of value (a review's Outlook section) had nothing to aim at, and `T-013` step ② had no target. **`C-008` ⓑ was chosen on 2026-09-05:** restate each axis so it anchors in domain literature.

### What the restatement does, and what it trades

**The move is to stop asking the meta question in the abstract and ask what the domain literature *asserts* about it.** An Outlook section never says "this topic is trending." It says *"the field is now in a position to attack X"* — which is the same dimension, stated as a claim with a locator. All three dimensions survive; the question changes from meta to domain.

| The user's dimension | Restated as | The claim it looks for in the literature |
|---|---|---|
| **trend** | **`X1` maturity** | *"this is now possible"* / *"this was posed and left"* |
| **difficulty** | **`X2` obstruction** | *"this has not been done because [named barrier]"* |
| **impact** | **`X3` reach** | *"this would carry to [other system]"* / *"this would settle [recurring dispute]"* |

> **What is traded, stated plainly.** You no longer get *"is this trending"* as a **citation measurement** from a value pole. **You do not lose it** — it moves to the supply layer, where a number comes from an API and not from an LLM ([charter.md](../charter.md) §5, `T-053`①). **Trend as a number is crawler output; trend as a value claim is domain-anchored.** The same split applies to impact: `cited_by_count` is already a field in [kb-schema.md](../kb-schema.md) §4.1.

### The axes

| Axis | The question it splits on | Pole | Direction of the value condition | `T-012` source |
|---|---|---|---|---|
| **`X1` · maturity** | Does value come from a problem the field has **just become able** to attack, or from one it **named and left**? | **`V1` frontier** | Valuable when a recently arrived capability makes it newly attackable | ① Outlook — *"now possible"* |
| | | **`V2` unfinished** | Valuable when the problem was posed in the literature and the trajectory shows it was not pursued | ③ **what was not done** |
| **`X2` · obstruction** | Is value in the problem whose obstruction is **named and physical**, or in the one whose only obstruction is that **nobody tried**? | **`V3` named obstruction** | Valuable when the literature states a specific barrier — a length scale, a timescale, an SNR limit. The value is in removing a stated barrier | ① Outlook — *"limited by"* |
| | | **`V4` unattempted** | Valuable when nothing is claimed to block it and it simply has not been done. The value is in the cheapness of a first result | ③ + absence |
| **`X3` · reach** | Does value come from a result that **transfers to another system**, or from one that **settles a dispute inside this one**? | **`V5` transfer** | Valuable when the result is claimed to carry to a different system class | ① Outlook — transfer claims |
| | | **`V6` settlement** | Valuable when it closes a definitional or framework dispute the field keeps returning to | ② trajectory — recurrence |

> **The `divergence.axis` enum becomes `maturity | obstruction | reach`** → [kb-schema.md](../kb-schema.md) §4.3.

### What this closed that was not the target

**`C-008` was the reason for the restatement. Two other things fell out of it.**

**① `C-009` closes.** The difficulty axis sat on the wrong side of [charter.md](../charter.md) §3's line — *"whether a topic is testable"* is BD's and MS's, and judging technical difficulty is judging testability. **`V3` does not judge it: it cites where the literature states the obstruction.** That is exactly the shape `C-009` said would work — *"a citation requirement rather than a prohibition"* — and the same shape `T-048` gave the challenge rule: **report what is recorded; do not argue the conclusion yourself.**

**② `T-012`③ gets used for the first time.** *"What was not done — an adjacent area left untouched"* was listed as one of the three canonical sources of value and then never assigned to anything. It is now **`V2`'s primary source** and half of `V4`'s. All three of `T-012`'s sources are now load-bearing.

**And `trajectory_check` (`T-014`) becomes runnable on four of six poles**, against zero before. `V2` (was it really dropped?), `V6` (does the dispute really recur?), `V1` (did the capability really arrive?) and `V4` (is the absence real?) are all trajectory questions. **This does not solve `Q-005`** — `V4` is an absence claim and walks straight into the ⓐ-vs-ⓑ problem — but it means the check has something to run on.

---

## Phase 1 — the test pair

**Why a pair and not one:** philosophy ⑤ (disagreement is the product) and `C-005` (the divergence schema) cannot be tested without a pair.

**`X1`'s original selection reasons are all void** (`T-051`) — they were properties of the reducibility axis. New basis:

| Axis | Why this one | Why not |
|---|---|---|
| **`X1` maturity** ← **recommended** | ① **both poles' falsifiers are runnable** — "did the capability arrive" and "was it really dropped" are both trajectory checks, so `C-003` (value has no ground truth) bites least here ② both poles read `T-012`① and ③, and **roadmap reviews are dense in exactly those** → §Special ③ it is the axis where a wrong distillation shows up fastest | — |
| **`X2` obstruction** | `V3` is the best-anchored single pole in the set — a stated barrier comes with a locator | **Asymmetric.** `V4` is an absence claim, so half the pair lands on `Q-005` with no way out |
| **`X3` reach** | `V6`'s falsifier is a clean recurrence check | `V6` needs a multi-year trajectory across many reviews. **Most expensive pair to run first** |

---

## Literature entry points

**Material for step ② of the `T-013` procedure.** Start from literature, not from names — the same reason BD `I-068` established for its axis personas.

> ### ⚠ The per-pole tables are gone
>
> The 21 rows that used to sit here were entry points for the **reducibility · mechanism · measurability** poles, and `T-051` retired those poles. **They are not translated across** — a paper that is canonical for *"reducible means valuable"* says nothing about *"the field just became able to do this."* They remain in git history at `d68065c`.
>
> **What survives is the section below**, and it survives intact: roadmap reviews were listed for **Outlook density**, not for any particular axis, and the restated axes read Outlook sections harder than the old ones did. **§Special is now the whole of this section's content, and Phase 1's first target.**

---

## Special as a source of value — roadmap reviews

`T-012` names the **Outlook section of a review** as the source of value. If so, **roadmap-format reviews are the best entry point** — they collect many authors' Outlooks in one article.

**All DOIs verified against OpenAlex on 2026-09-05**, and the open question in the old version of this table — *"check whether a newer edition exists"* — **is closed: it does.**

| Reference | DOI | Why special | Verified |
|---|---|---|---|
| Gompper et al., ***The 2025 motile active matter roadmap***, *J. Phys. Condens. Matter* | `10.1088/1361-648X/adac98` | **32 authors, open access.** Its abstract states `V1`'s value condition outright: *"with many fundamental properties … now reasonably well understood and under control, **the ground is prepared for** …"* and names five directions | ✔ |
| Gompper et al., *The 2020 motile active matter roadmap*, *J. Phys. Condens. Matter* **32** | `10.1088/1361-648X/ab6348` | 37 authors, open access. Dozens of Outlooks section by section | ✔ |
| Bechinger et al., *Active particles in complex and crowded environments*, *Rev. Mod. Phys.* **88** | `10.1103/RevModPhys.88.045006` | Open access, 3031 citations. Broad Outlook | ✔ DOI · Outlook locator not read |
| Marchetti et al., *Hydrodynamics of soft active matter*, *Rev. Mod. Phys.* **85** | `10.1103/RevModPhys.85.1143` | Ten years of active matter compressed (BD `I-068`) plus an Outlook. **Not open access** | ✔ DOI · not OA |

### The two editions are `X1`'s falsifier instrument

**This is the result of running `T-013` on `X1`** (`T-055`), and it was not anticipated when the axis was written.

Two editions of the same roadmap, five years apart, author sets overlapping (37 → 32). That gives **a locator at both ends of a trajectory claim**, which no other axis in this repo has:

| Diff direction | Reads as | Pole |
|---|---|---|
| Named as newly attackable in 2025, absent in 2020 | a capability arrived | **`V1` frontier** |
| Posed in 2020 **and posed again** in 2025 | named and left, and the recurrence survived five years | **`V2` unfinished** |
| Posed in 2020, absent from 2025 | **three branches, not two** → §Open | ambiguous |

**Why this matters beyond `X1`:** `C-003` says value has no ground truth, and `T-015`'s one cheap attack on it — asking a reachable canonical author — died with the reducibility pole. **The roadmap diff is a replacement of a different kind: cheaper, repeatable, and not `trivially_satisfied`** (`T-016`), because the roadmap's 32 authors are not this repo. It is weaker than an author's answer and it can be run more than once.

> **This table is Phase 1's first target, and the 2025 edition is the first document to read.**

---

## Open

- **`T-013` has now been run once, on `X1`** (`T-055`, 2026-09-05) → [`V1` frontier](V1-frontier.md) · [`V2` unfinished](V2-unfinished.md). **The four other poles are still names with no conditions**, and the run came back split: `V1`'s `trajectory_check` is `consistent`, `V2`'s is **`not_run`**, which is not a pass.
- **The `X1` pair is currently unfair, in the same way `X2` was rejected for being.** `V1` has a measured trajectory and `V2` has none, because `V2`'s `c1` needs the *section-level* content of the 2020 roadmap and only abstracts were read. **Both editions are open access, so this is a budget limit rather than an availability limit** — bounded, known, and unpaid.
- **`X1` produces divergence on a subset, and nothing says how large.** The two poles genuinely disagree on two classes of target and **genuinely agree on a third** (posed long ago *and* newly attackable). Agreement emits `shared`, not `divergence/`. Correct behaviour, unquantified consequence → [`V2`](V2-unfinished.md) §2.
- **`V4` unattempted is the weak pole.** Its value condition is an **absence** claim, so it lands directly on `Q-005` — an absence is either a real gap (the best product) or a distillation error (the worst failure), and nothing tells them apart automatically. **`X2` is therefore not a fair first pair**, which is why Phase 1 recommends `X1`.
- **The restated axes are more legible than the old ones, and that is a new risk.** *"Was this posed and left"* is a question an LLM will always produce a plausible answer to, and the answer is unverifiable unless the trajectory is actually searched. The old domain axes were harder to fake because they needed physics. **The guard is `T-014`'s `trajectory_check` and `T-023`'s search budget, and neither has been run.**
- **Whether three axes is right is still unargued.** `Q-004` closed the *count* question by back-deriving poles from axes. **The basis for there being exactly these three is the user's list, restated** — one dimension dropped from that list on the way (rigour → J3, `T-053`③) and two merged (hard problems + technical difficulty → `X2`, `T-051`).
- **Names are gone and the repo stays public** — decided 2026-09-04 (`T-044`). ① the topic assessments that will accumulate in the KB are unpublished research directions, so **there has to be a rule about what J1 may write, and it is unwritten** — a Phase 2 interlock with no warn mode. ② **`T-019`②'s cost is now paid off by the restatement:** the reading list used to point at the group's own output because `V1` reduction's literature overlapped it. **The new axes are not about this group's physics**, so the reading list no longer points anywhere in particular. That reason was never retracted; it dissolved as a side effect. → [README.md](../../README.md) §8
