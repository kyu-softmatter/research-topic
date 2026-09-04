# research-topic — the topic-selection and knowledge axis

> [!IMPORTANT]
> **IDEA SKETCH / CONCEPT DOCUMENT**
>
> This repository is a design proposal for the third axis of a three-part
> system. It contains design documents only — **no code, no knowledge-base
> entries, and no running pipeline.** The value axes, schemas and literature
> lists written out here are **discussion material, not decisions**;
> construction is to be done by someone else (§5), and all of it is subject to
> change. What is fixed and what is open is separated in §0.

The third axis. It supplies [agentic-microscope](https://github.com/kyu-softmatter/agentic-microscope) (experiment) and [Brownian-Dynamics-Agent](https://github.com/kyu-softmatter/Brownian-Dynamics-Agent) (simulation) with **what to work on**, and takes back what those two produce **as knowledge**.

Drafted 2026-08-31 · status `sketch` — **no code. An idea sketch only.**

## Project status

Design documents in [`design/`](design/), and nothing else. No `src/`, no `kb/`, no tests — those directories are not empty, they do not exist.

| | |
|---|---|
| **Written** | Boundaries between the three repos · six philosophy items · an idea log of 33 ideas, 6 conflicts, 9 open questions |
| **Drafted, expected to be replaced** | 3 value axes / 6 poles · KB formal-object schemas · literature entry points |
| **Empty** | The value conditions of every pole. Only the pole names exist |
| **Not started** | Everything in Phase 1 and after → §4 |
| **Depends on this repo** | Nothing. Both working repositories run without it |

The nearest thing to a deliverable is the 2026-09-03 discussion (§6), whose purpose is to make the four rows of §0 fillable by the person who will build this.

---

## 0. What these documents are — read this first

> **This repo is an idea sketch. Nothing is built, and J1/J3 will be built by Prof. Sho Takatori directly** (§5).
>
> So the documents below hold **three different kinds of thing, and reading them as one kind is the mistake to avoid.**

| Status | What | Where |
|---|---|---|
| **Decided** | The **boundaries** between the three repos · the **six philosophy items** · what this repo **does not do** | [charter.md](design/charter.md) · §3 · §9 |
| **Registered only** | Ideas, conflicts, open questions. **Not resolved** | [ideas.md](design/ideas.md) |
| **Discussion material** | Value-axis assignments · schema fields · literature lists. **Not decisions** | [lineages.md](design/personas/lineages.md) · [kb-schema.md](design/kb-schema.md) · [_common.md](design/personas/_common.md) |

**The third row is the easy one to misread.** The schemas and axis assignments are written out concretely **not because they are settled**, but so that the discussion has something specific to push against. The `T-013` procedure has never been run once, and much of the literature is unverified by DOI.

**What the builder is expected to change:**

| What | Current state | Who decides |
|---|---|---|
| What the value axes are, and how many | 3 axes / 6 poles — **a draft**, standing in for the real thing | **Takatori** (agenda 3) |
| The value conditions of each pole | **Empty.** Only the pole names exist | **Takatori** (agenda 1–2) |
| The fields of the KB's formal objects | Example JSON. Only the principle is fixed | **Takatori** (J1 · J3) |
| The form of a rigor axis's pass conditions | A draft back-derived from BD's `A1`–`A10` | **Takatori** (J3, agenda 6) |

**The only things that should not be changed are the six philosophy items in §3 and the boundary table in [charter.md](design/charter.md) §3** — both were either inherited from the two existing repos or derived from where those two independently converged, so they are not this repo's to change alone.

---

## 1. The three jobs

| # | Job | Product | Consumer |
|---|---|---|---|
| **J1** | **Accumulate the knowledge base** | KB entries as formal objects + a search index | BD · microscope |
| **J2** | **Select scientific topics** | Topic candidates in falsifiable form, with the basis for their value | BD · microscope · a human |
| **J3** | **Manage the definitions of rigor** | Axis definitions · the form of pass conditions · the canonical-source registry | BD · microscope |

**J3 is BD's `I-066` lifted one level.**

```
research-topic   = the source of criteria     what the rigor axes are, the form of a pass condition, the canonical sources
BD · microscope  = the enforcers              each runs those axes as code in its own domain
```

Definitions here, enforcement there. **This is not a migration** — BD's `A1`–`A10` and the microscope's `G1`–`G32` stay where they are. What comes here is only **the part the two repos arrived at independently**. → [charter.md](design/charter.md)

---

## 2. The three-axis loop

```text
                      +---------------------------------+
                      |        research-topic           |
                      |                                 |
                      |  keywords -> survey -> topics   |
                      |  value personas ask questions   |
                      |  (questions, not verdicts.      |
                      |   BD:I-050)                     |
                      +----+-------------------+--------+
                           |                   ^
              topic + falsification conditions |  KB writes
                           |                   |  dead ends
              +------------+------+     +------+----------+
              v                   v     |                 |
   +---------------------+  +---------------------+        |
   |  BD agent           |  |  agentic-microscope |        |
   |  simulation         |  |  experiment         |--------+
   |  A1-A10 verdicts    |  |  8 lenses / 32 gates|
   +----------+----------+  +----------+----------+
              |                        |
              +-----------+------------+
                          v
              results . counterexamples . dead ends
```

**The hypothesis:** the three axes pull each other along, forming a positive feedback loop.

**The objection this repo carries:** a positive feedback loop either diverges or confirms itself. If the three axes feed each other, **whatever bias they share gets amplified.** The loop needs damping, and the damping has to come from here — topics go out **only in a form BD and the microscope can falsify.** → [ideas.md](design/ideas.md) `C-001`

---

## 3. Philosophy

Six items. The first four are inherited from the two existing repos; the last two originate here.

### ① The default is failure, not passing — inherited

BD `I-055`, and the microscope's `BLOCKED`. With no basis for a verdict, there is no pass. Here that reads: **the default for "this topic has value" is "unknown," and no code path exists that moves to "yes" without a basis.**

### ② The LLM does not originate numbers — inherited

BD: personas name the criteria, code settles them. Microscope: the subagent supplies only the half of a judgment that has no closed form, and originates no number. Two repos reached the same rule independently. Same here — a value persona says **where to look**, and the search result says **what is there.**

### ③ Every judgment carries the check that would overturn it — inherited

BD `I-065`, and the per-entry falsifiers in the microscope's `kb/expertise/`. Here that reads: **each question carries "if this already has an answer, where would it be?"** Without it a literature survey has no stopping condition, and then **the search budget becomes the value judgment.** → `T-008` · `T-023`

### ④ Natural language is not state — inherited

BD's `I-133` antipattern. **This is exactly where J1 dies.** KB entries are formal objects of the shape `{topic, source, conditions of validity, falsification condition, state}` — not summaries written by an LLM.

### ⑤ In rigor, disagreement is a bug; in value, disagreement is the product — new

BD divided by **axis rather than by person** on the grounds that *"different axes give orthogonal verdicts, so conflict never arises in the first place"* (`I-067`).

**Value is not orthogonal.** A theory/minimal-model lineage holding that something is uninteresting because it does not reduce to a dimensionless group, and an experiment/emergence lineage holding that it is interesting because a new state shows up in the lab, **are true of the same system at the same time.**

So this repo inherits seven of BD's eight prohibitions and drops one: **"no rebutting another persona."** In its place it fixes the form — not rebuttal but a **divergence record**: when two personas attach opposite value to the same target, **the point of divergence itself becomes a KB entry.** Topics with large divergence are the first-rank candidates.

**Structural consequence:** BD has **one persona per axis** (orthogonality is the goal); here there are **two per axis — the two poles** (disagreement is the goal). Convene one pole and no divergence exists. → `T-018`

**This is the most dangerous decision in the repo.** → `C-002` · `C-005`

### ⑥ The canonical source of value is not a textbook — new

BD's `I-068` moved the distillation entry point from names to 27 textbooks, on the grounds that *"a school's pass criteria are written down explicitly in the textbooks."* **Value has no such grounds** — "what is interesting" is not written in textbooks.

Where it is written, in three places:

| Source | What it gives |
|---|---|
| **The Outlook / Open questions section of a review** | What that lineage holds to be still unsolved |
| **The trajectory of the body of work** (in time order) | What that lineage actually picks |
| **What was not done** | An adjacent area left untouched — the most valuable signal, and the hardest to read |

The third is this repo's best product and **is indistinguishable from a distillation error.** → `Q-005`

---

## 4. The plan

Phases are ordered, and each carries its **exit condition**. A phase without one does not end.

### Phase 0 — sketch (now)

| Task | Exit condition |
|---|---|
| Fix the boundaries between the three repos | [charter.md](design/charter.md) §3 is filled with no item owned twice |
| Register ideas, conflicts, questions | [ideas.md](design/ideas.md) — **register, do not resolve** |
| Read the microscope's `kb/expertise/` | `Q-002` closes — J1's basis is either confirmed or weakened. **Cheapest item on the list** |
| Re-derive [charter.md](design/charter.md) §2 from the BD **remote** | `T-041` — the table was built from a local snapshot that is probably behind |

### Phase 1 — prototype the two poles of one axis

**Why a pair and not one:** philosophy ⑤ (disagreement is the product) and `C-005` (the divergence schema) **cannot be tested without a pair.** Same method BD used when two worked examples validated its design.

**Choosing the axis is not this repo's call** (§0) — agenda 3.

| Task | Exit condition |
|---|---|
| Pick one axis and fix its **two poles** | One real case exists where the two poles attach opposite value to the same system |
| Write each pole's value conditions | Per `T-013` — value conditions → review Outlook and trajectory → check consistency |
| Draft the divergence-record schema | The closing condition for `C-005` |
| Run the trajectory check once | `T-014` — does a pole's claim match the actual trajectory of its literature? |

### Phase 2 — interlocks (**before** any KB content)

**The order looks backwards on purpose.** BD's `I-075` and `I-076` already diagnosed the two ways a KB dies — ① nobody fills it (recording is always the last step and always the skipped one) ② the index goes stale, so **the files are all there and search finds nothing.** This repo *is* the KB, so both failures are fatal.

| Task | Exit condition |
|---|---|
| `capture-gate` — block session exit with no record | One week in warn mode, then blocking |
| Force the search index to refresh | A cycle cannot end without an index refresh |
| Settle the KB formal-object schema | [kb-schema.md](design/kb-schema.md) — zero places where a natural-language field is used as state |

### Phase 3 — the J2 pipeline

| Task | Exit condition |
|---|---|
| Keywords → literature survey | Inherit BD `I-080` (author-adjacent, then system-adjacent) and `I-082` (citation graph) |
| Wire up a forward-citation index | `Q-006` — OpenAlex / Semantic Scholar. **J2 cannot run at all without this** |
| The question gate | BD `I-052` — a question's fate is decided by whether a search returns anything, not by an LLM vote |
| Emit topic candidates | The output is in a form BD and the microscope **can falsify** (`T-034`, damping) |

### Phase 4 — integration

→ §7.

### Not in the plan yet

- **Retrospective validation of value.** `C-003` — whether a topic was worth doing is known years later. The topic scorecard (`T-033`) is the only grounding, and **early in the loop there is none.** This is not deferred; there is no answer yet.

---

## 5. People and roles

| Axis | Participants |
|---|---|
| **BD agent** ([repo](https://github.com/kyu-softmatter/Brownian-Dynamics-Agent)) | Dr. Takuya Kobayashi · Saksham Malik |
| **agentic-microscope** ([repo](https://github.com/kyu-softmatter/agentic-microscope)) | Kyu Hwan Choi · Saksham Malik |
| **research-topic** — KB · rigor definitions (J1 · J3) — **built directly** | Prof. Sho Takatori · Kyu Hwan Choi |
| **Overall management** | Kyu Hwan Choi |
| **Funding · advising** | Prof. Sho Takatori |

### Why there is no lead column

Everyone named in a row is a participant in that axis, and how the work divides inside it is theirs to settle rather than this document's to assign. The table records **who is on which axis** — nothing about seniority, and nothing about who reports to whom.

It also carries no commitment status. An earlier draft tagged every row with one, which was the right hedge while the rows were a proposal. They are not a proposal now.

### Where the roles overlap — a structural warning

**If the person authoring J3 (the rigor definitions) is also a canonical-source author of a value lineage, the one automatic check in `T-014` weakens.**

`trajectory_check` — does a lineage's value claim match the actual trajectory of its literature? — carries information **only when the value conditions were back-derived from the literature independently.** Written directly, the check approaches guaranteed-pass and its information content drops.

**This shape is already named.** BD `personas/_common.md` §8:

> *If a benchmark's input overlaps the model's input, that check is guaranteed to pass and carries zero information.* → `trivially_satisfied: true`

**Removing names (`T-018`) cut this risk sharply** — a persona is no longer a specific individual, so the overlap is not structural. **It did not disappear:** the `V1` (reduction pole) literature of axis `X1` contains his own canonical papers.

**The split:**

| What | Who | Why |
|---|---|---|
| **J3 — the rigor definitions** (axes · the form of pass conditions · conditions of validity from the sources) | **Authored directly** | Rigor is **strictly better** authored by the authority. No overlap problem |
| **`V1`'s value conditions** | **Back-derived from literature independently** | His answers are used as a **held-out** comparison only |

**So there are now two reasons, not one, to write the `V1` control draft before Thursday:** ① so the discussion is a test (§6) ② to avoid `trivially_satisfied`. → `T-016`

### Saksham Malik spans two axes

**This is the real pressure behind the integration question (`Q-008`).** The cost of two sets of criteria has been abstract so far; with a person on both repos, **a person pays it** — learning the same thing twice in two formats. It may pull §7's decision point earlier.

---

## 6. Discussion with Prof. Sho Takatori — 2026-09-03 (Thu)

**Two reasons this discussion is part of the design.**

**① Handing over construction.** J1 and J3 get built directly by him (§5). This repo is a sketch, so the first purpose of the discussion is **to make the four rows of §0's "what the builder is expected to change" fillable.**

**② The only cheap attack on `C-003`.**

> **A value lineage has no ground truth** — there is no way to check whether the distillation is right. The exception is **a lineage whose canonical-source author can be asked.**

The canonical sources of `A5.E8` (swim pressure, *PRL* **113**, 2014) and `A6` (nonequilibrium quantification) sit in the `V1` (reduction pole) literature of axis `X1`. **So for exactly one of the six poles a comparison path exists.** The distillation method itself gets tested on one case; the other five poles have no such path.

### Agenda — in priority order

| # | Item | IDs | Why it has to be him |
|---|---|---|---|
| **1** | **"What does a problem need before you pick it?"** — can the value conditions be stated explicitly? | `T-013` · `C-003` | The answer key for distillation. Comparable against what the literature yields |
| **2** | **Test philosophy ⑥** — is it true that value lives in review Outlooks and work trajectories? Do his own choices actually show up in those two places? | `T-012` | If this is false, all of Phase 1 collapses |
| **3** | **What actually divides active matter** — **throw away** the 3-axis / 6-pole draft in [lineages.md](design/personas/lineages.md) and set it again | `Q-004` · philosophy ⑤ | The real dividing lines inside a field are not on the surface of its literature. **§0's first two rows get filled here** |
| **4** | **`C-004` — how do you tell "nobody asked" from "nobody asked because it is boring"?** | `C-004` · `T-007` | This is senior tacit knowledge itself. No automation path is visible |
| **5** | **`Q-005` — distillation error, or a real gap?** | `Q-005` · `T-014` | When a pole says X is interesting but X is absent from its literature |
| **6** | **Review the pass conditions of rigor axes `A5` and `A6`** — existing BD output, checked by the canonical author | BD `A5` · `A6` | **The actual starting point for building J3.** The `conditions` field of the source registry comes from here |
| **7** | **`Q-009` — will he take J1/J3, and what happens with funding?** | `Q-009` · §5 | Authoring J1/J3 and the funding line rest on the same person. **What stays valid if declined is not written down** |
| **8** | **Is removing names enough?** — lineages replaced individuals, but `V1`'s literature overlaps the group's own output, so **the reading list points anyway** | `T-019` · §8 | The real ceiling on disclosure. Feeds directly into the `C-006` integration call |

### To prepare beforehand

- **A draft of `V1`'s (reduction pole) value conditions**, back-derived from literature alone. The control for agenda 1. **It has to exist before asking, or there is no comparison.**
- Two or three **candidate axes** for agenda 3 — on the assumption they get discarded.
- The BD `A5` and `A6` persona files (existing output, something real to show). Material for agenda 6.

> **Careful:** ask agenda 1–2 first and the answer drags the design with it. **Walking in without the control draft turns the test into dictation.**
>
> **Agenda 3 is the opposite** — the axis assignment is not this repo's to decide (§0), so the draft is not defended. It is carried in **to be thrown away.**

---

## 7. Integration with the two existing agents — under consideration

**The current decision is "index, do not merge"** (`T-004`). The grounds are BD `I-057` — a boundary is drawn at *is it reversible and checkable*. Indexing is reversible; migration is not.

**But integration is open.** Three candidates:

| Option | Shape | Gains | Loses |
|---|---|---|---|
| **A. Three repos + indexing** *(current)* | This repo points at the other two | Reversible. Neither repo is touched | Risk of two sets of criteria. Cross-references are manual |
| **B. Monorepo** | All three in one | One set of criteria. References never break | Turns on §8. **All three repos are public today**, so the disclosure conflict as written does not bind — and it returns in full the moment this one goes private |
| **C. This repo as the orchestrator** | The other two as submodules, the loop runs here | The three-axis loop becomes real | This repo becomes an enforcer and violates its own structural prohibition ([charter.md](design/charter.md) §5) |

**B's obstacle is disclosure scope, not engineering — and the premise it was argued on has changed.** `agentic-microscope` became public on 2026-08-28 after the vendor material was stripped, and **this repo is public too** (§8), so the "put them in one repo and the stricter side wins" argument has nothing to bite on today.

**That is not the obstacle being resolved; it is the obstacle being unsettled.** `T-019`'s two reasons for keeping this repo private were never retracted (§8), so if they are acted on, B goes straight back to impossible and the microscope goes private again. **Deciding B therefore means deciding §8 first**, not the other way round.

**Removing names on 2026-08-31 lowered that obstacle** (`T-018` · `C-006`) — with no attribution by name, the largest argument is gone. **But `T-019`'s two remaining arguments mean B has not become possible.** It has become discussable.

**Decision point:** after Phase 1, once it is clear whether divergence records come out in a form BD and the microscope can actually use. Integrating before that fixes the structure without knowing what is being integrated. → `Q-008`

---

## 8. Disclosure scope — an unsettled constraint

> **Correction, 2026-09-04.** This section used to read *"Why private — an irreversible constraint"* and concluded *"this repo **stays private**."* **That was never true of the repository as published** — `research-topic` has been public since it was created on 2026-09-01. The reasoning below is kept because it was not retracted; what changed is that it no longer describes the state of the repo.

### The original reason for private, and how it was already removed

In the first draft a persona distilled **a named researcher's research philosophy**. That produces sentences like:

> *"To Prof. X this system would look like a problem whose answer is already known."*

**A value judgment attributed to a named researcher becomes a matter of reputation once public.** BD's roster of ~200 is entirely real people, many of them living. `agentic-microscope` could go public because its lenses were **subsystems** (optics, detection, compute), not people.

**On 2026-08-31 this was removed at the definition stage rather than the output stage** (`T-018` · `T-035`) — a persona is not an individual but a **lineage defined by a body of literature**, and the rule is **citations stay, attributions go.** [lineages.md](design/personas/lineages.md) contains no names.

### The two reasons that argued for private, and where each one now lands

`T-019`:

1. **The topic assessments that will accumulate in the KB are unpublished research directions.** Nothing to do with names. **Nothing of this kind is exposed today** — J1 has not started and `kb/` does not exist — so this reason is about what may be *written*, not about what is currently readable. It becomes live the moment the first topic assessment lands.
2. **The `V1` literature of axis `X1` overlaps the group's own output.** Without naming the lineage, **the reading list points at it anyway.** So how much `T-035`'s name-stripping actually strips **has not been measured** — and it is public and unmeasured now, which is the part that cannot be deferred.

**Therefore:**

- **This is an open decision, not a settled one.** Either the repo goes private, or `T-019`'s two reasons are rewritten as content rules for what J1 is allowed to put in a public KB. **Reason 1 has to be settled before the first topic assessment is written; reason 2 is already in effect.**
- Point 2 was the **ceiling** on relaxing `C-006` (§7), and it still is. What has changed is that the ceiling is no longer enforced by the repo's visibility.
- **Consent from the people involved** is still a separate matter, and a sharper one now: they are no longer persona targets, but the literature overlap remains and is publicly readable. → §6 agenda 8.
- **The design documents have not been swept.** [ideas.md](design/ideas.md) (`T-019` · `C-006` · `T-043`), [lineages.md](design/personas/lineages.md) and [_common.md](design/personas/_common.md) still say this repo is private. Those entries are dated log records, so they read correctly as history — but nothing in them points here.

---

## 9. What this repo does not do

| Not done here | Done where |
|---|---|
| Running or judging simulations | BD |
| Proposing instrument settings, running experiments | microscope |
| Originating numbers | Nowhere (philosophy ②) |
| Setting thresholds and tolerances | BD and the microscope, each for itself. Values are domain-owned |
| Settling a conclusion ("this topic has value") | A human. Irreversible judgments are not on the automatic path (BD `I-057`) |

---

## 10. Documents

| Document | Contents | Status |
|---|---|---|
| [design/charter.md](design/charter.md) | Boundaries between the three repos. The evidence that two of them converged | `sketch` |
| [design/ideas.md](design/ideas.md) | Idea log (`T-` · `C-` · `Q-`) | `sketch` |
| [design/kb-schema.md](design/kb-schema.md) | J1's formal objects. The answer to BD `I-133` | `sketch` |
| [design/personas/_common.md](design/personas/_common.md) | The common contract for value personas | `sketch` |
| [design/personas/lineages.md](design/personas/lineages.md) | Value lineages, 3 axes / 6 poles, plus literature entry points. **No names** | `sketch` |
| `src/` | Does not exist | — |

---

## Reference convention

IDs from other repos carry a prefix: `BD:I-050` · `MS:G27`. This repo's own IDs are `T-` (idea), `C-` (conflict), `Q-` (open question).

Quotations from BD's design documents are translated; the Korean originals are findable by ID in that repo.

**Indexing targets** (`T-004` — index, do not migrate):

| Prefix | Repo | Visibility |
|---|---|---|
| `BD:` | https://github.com/kyu-softmatter/Brownian-Dynamics-Agent | public |
| `MS:` | https://github.com/kyu-softmatter/agentic-microscope | public |

`Q-007` (what does this repo point at for BD) is **closed** — both repos are on GitHub, so references pin commit SHAs. Local paths are not used.
