# research-topic — the topic-selection and knowledge axis

[![licence: MIT](https://img.shields.io/badge/licence-MIT-blue.svg)](LICENSE)

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

**The goal is the three of them running as one multi-agent system** — each stage
handing the next the knowledge it needs, in a form the receiver can actually
consume. The two working repositories already run, and each already keeps a
knowledge base. **What does not exist is the exchange between them:** neither
repository references the other, so a result BD establishes is not readable by
the microscope, nor the reverse. That gap is what this repo is for. → §2.1

Drafted 2026-08-31 · status `sketch` — **no code. An idea sketch only.**

## Project status

Design documents in [`design/`](design/), and nothing else. No `src/`, no `kb/`, no tests — those directories are not empty, they do not exist.

| | |
|---|---|
| **Written** | Boundaries between the three repos · six philosophy items · an idea log of 44 ideas, 9 conflicts, 10 questions (6 still open) · **the seven exchange points, checked against the live repos** → §2.1 |
| **Drafted, expected to be replaced** | 3 value axes / 6 poles · KB formal-object schemas · literature entry points |
| **Empty** | The value conditions of every pole. Only the pole names exist |
| **Not started** | Everything in Phase 1 and after → §4 |
| **Depends on this repo** | Nothing. Both working repositories run without it |
| **Verified against the live repos** | 2026-09-05 — what each of the other two actually keeps, and where the exchange would attach → §2.1 |

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
| What the value axes are, and how many | **Decided 2026-09-05** (`T-051` · `T-054`). Three dimensions — trend · difficulty · impact — each **restated to anchor in domain literature**: `X1` maturity · `X2` obstruction · `X3` reach. Still two poles per axis | ~~Takatori (agenda 3)~~ — **the user, on both.** The *specific* restatement is derived and is still a draft to push against |
| The value conditions of each pole | **Empty.** Only the pole names exist. **Nothing blocks filling them any more** — `C-008` was the blocker and `T-054` resolved it by giving `T-013` step ② a target. **This is now the top open item** | **Takatori** (agenda 1–2) |
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
                    +-------------------------------------+
                    |           research-topic            |
                    |  survey -> topic candidates         |
                    |  personas ask questions (BD:I-050)  |
                    |  holds form . provenance . custody  |
                    +--+-------------------------------+--+
                       |                               ^
   (1) topics + falsification conditions               |
   (2) literature + conditions of validity      (4) results
   (3) rigor-axis definitions  (J3)             (5) dead ends
                       |                        (6) questions
                       v                               |
     +-----------------+--------+       +--------------+-----------+
     | Brownian-Dynamics-Agent  |       |    agentic-microscope    |
     | simulation               |       |    experiment            |
     | A1-A10 . deterministic   | <---> |    8 gates . G1-G32      |
     | gate                     |  (7)  |    BLOCKED by default    |
     +--------------------------+       +--------------------------+

   (1)-(7) are the seven exchange points -> sec 2.1

   ...................................................................
   challenge/  runs along every edge above, in BOTH directions:

     any node --- cites the TARGET entry's own falsifier ---> any node

     and the falsifier's type -- not the sender -- picks who runs it:
        a measurement -> microscope . a run -> BD . a condition -> here

   So BD and the microscope send work here too.  No owner in
   charter sec 3 changes; only the direction stops being fixed. -> sec 2.2
```

**The hypothesis:** the three axes pull each other along, forming a positive feedback loop.

**The objection this repo carries:** a positive feedback loop either diverges or confirms itself. If the three axes feed each other, **whatever bias they share gets amplified.** The loop needs damping, and the damping has to come from here — topics go out **only in a form BD and the microscope can falsify.** → [ideas.md](design/ideas.md) `C-001`

### 2.1 What is exchanged at each stage

The arrows above are the goal. What follows is what each arrow would have to
carry, and what is actually in place.

> **The `Exists today` column is read off the two live repositories on
> 2026-09-05; everything in `Missing` is unbuilt.** The two working repos have
> moved well past the snapshot [charter.md](design/charter.md) §2 was built from
> (`T-041`), so this table supersedes that one on the question of what BD keeps.

| # | Stage | The knowledge that has to cross | Exists today | Missing |
|---|---|---|---|---|
| **1** | research-topic → BD · MS | **A topic candidate in falsifiable form** — with `falsifiable_by` naming which of the two can kill it | The receiving slots exist. BD takes a case as `intake/<case>/{sketch,system.yaml,observation.yaml}` (8 cases); MS takes a research goal | **Everything upstream of them.** Nothing produces a topic. Both are fed by hand |
| **2** | research-topic → BD · MS | **A published number with its conditions of validity** — the part that appears only in the original paper | BD: `knowledge/source/papers/` — **44 distillations** carrying `doi · read_depth · provides · used_by · lab_authored`. MS: `kb/literature/` — **schema, template, and zero entries** | **The two formats do not meet.** BD has 44 entries MS cannot read; MS has an empty folder BD cannot fill. This is the sharpest gap in the system |
| **3** | research-topic → BD · MS | **Rigor-axis definitions and the form of a pass condition** (J3) | Each runs its own: BD `.claude/rules/` (4 files) + `A1`–`A10`; MS 8 gate modules + `G1`–`G32` | No shared **form**, so the same axis can be written two ways and neither notices → `T-004`'s revisit condition |
| **4** | BD · MS → research-topic | **Results and counterexamples** | Dense on both sides. BD: **227 `runs/*/record.json`** post-mortems + `l4.json`/`metrics.json`; MS: `kb/calibrations/`, `kb/decisions/` (19) | **No consumer.** Nothing reads them for topic selection |
| **5** | BD · MS → research-topic | **Dead ends** — cause, not symptom | BD already writes them: `knowledge/wiki/findings/dead-end-*.md`, with a mandatory `## Prevention` section | Custody here is **empty**, and BD's dead ends are not indexed anywhere outside BD |
| **6** | value personas → the gate | **A question plus what would close it** | **BD already implemented this** — `knowledge/wiki/questions/`: *"open questions, with what would close them."* Independent arrival at `T-008` | Two entries, BD-internal. No cross-repo question store |
| **7** | MS ↔ BD | **A number measured on one setup, reused on the other** | MS solved this *within itself*: [`docs/03-cross-system-transfer.md`](https://github.com/kyu-softmatter/agentic-microscope/blob/main/docs/03-cross-system-transfer.md) separates what transfers as-is from what needs recomputation | Nothing crosses **between** repos. The hardest row, and the one neither repo can do alone |

**Row 2 is where to start.** It is the only row where one side holds the content
and the other holds an empty slot shaped to receive it, so it can be tested
without either repo changing what it does.

### The convergence that makes row 2 tractable

The three repos independently arrived at the same rule: **a published number is
unusable without the conditions under which it holds, and it never counts as a
measurement.**

| Repo | How it says it |
|---|---|
| **research-topic** | `literature.conditions` — *"when this expression holds — the part that appears only in the original paper"* → [kb-schema.md](design/kb-schema.md) §4.1 |
| **microscope** | **Transfer conditions** is a mandatory section, and a literature value is always `assumed`, never `measured`, so **it cannot advance a verdict**. *"An entry that cannot say what would have to hold for its number to apply here is not usable, however good the paper is"* |
| **BD** | Provenance is `from_paper` · `from_knowledge` · `assumed` · `derived` plus a **tier**, and *"a derived value is recomputed and compared, never trusted as written."* The cost of getting this wrong is recorded: `T = 300 K` mislabelled as measured propagated a −4 % to −14 % error into every `τ_B` downstream |

**This is a fourth convergence, and it was not in [charter.md](design/charter.md) §2.**
It matters more than the count: §2's table established that the three agree on
*shape*, and this one shows they agree on **the field the exchange actually turns
on.** Row 2 does not need a format negotiated from scratch — both sides already
demand the same thing of a literature entry.

> **What this does not settle.** BD keeping a real knowledge base removes one of
> the three grounds for J1 (`T-003` argued a third place was needed because the
> microscope's KB is instrument-bound and BD had none). **The ground narrows
> rather than falls:** BD's `knowledge/wiki/` is simulation-bound the way MS's
> `kb/` is instrument-bound — `systems/` cards, `concepts/` in BD's own
> conventions — but `source/papers/` is not, and neither is MS's `kb/literature/`.
> **The shared layer is the literature layer, and that is exactly row 2.**
> → `Q-002`

### 2.2 Collaboration, not dispatch — challenging a claim

The seven rows above still run one way at the criteria level: definitions and
topics go down, results come up. **That is management, not collaboration.**
[charter.md](design/charter.md) §5 forbids this repo from becoming an enforcer —
but nothing in it says the other two cannot send work **here**.

**The missing primitive is already in all three repos: every KB entry carries its
own falsifier.** That is philosophy ③, and [charter.md](design/charter.md) §2
records it as one of the six things BD and the microscope arrived at
independently.

| Where | The falsifier that is already there |
|---|---|
| MS `kb/expertise/` (6) | each entry carries **the observation that would retire it** |
| MS `kb/literature/` | `## Falsification conditions` is mandatory — *"the first is always the local measurement that would replace this"* — and *"what sits in this folder is exactly **what is worth measuring next**"* |
| BD `knowledge/wiki/findings/` (23) | `## Scope / limits` — where this stops being true |
| BD `knowledge/wiki/benchmarks/` (5) | known-answer systems **already running as regression tests** |
| BD `knowledge/wiki/questions/` (2) | open questions, **with what would close them** |

**A falsifier is a work order that nobody executes yet.** Raising doubt about a
claim is asserting that its falsification condition may now be reachable;
verifying it is running that condition. And **the type of the falsifier decides
who does the work** — which is what turns the hierarchy into a graph:

| The doubt | Falsifier type | Routes to |
|---|---|---|
| the published number does not transfer to this setup | a local measurement | **microscope** |
| the claim is contradicted by what the model actually does | a run | **BD** |
| the conditions of validity were never checked against the source | literature | **research-topic** |
| the claim was used outside the scope it stated | none available | **a human** (`not_resolvable`) |

**BD and the microscope become senders.** No row of
[charter.md](design/charter.md) §3 changes — the microscope still owns instrument
values, BD still owns run provenance, this repo still holds form and custody —
but **the direction of a work order is no longer fixed.**

Three rules it has to keep.

1. **A challenge is a work order, not an argument.** It must cite the target
   entry's own falsification condition. An entry with no falsifier **cannot be
   challenged**, and that is a defect in the entry rather than a limit here. This
   is also what keeps the mechanism clear of
   [_common.md](design/personas/_common.md) §3, which forbids a persona rebutting
   another persona's *basis*: a challenge is settled by a run, a measurement or a
   search, never by the better argument.
2. **The verdict is a result, not a vote** — BD `I-052`. `upheld` / `rejected` is
   set by what the run or the search returned, and `not_run` is the default
   (`I-055`).
3. **It is bounded.** A challenge carries `resolvable_by` (`T-034`'s damping
   device), a cost, and a **depth** — a challenge against a challenge increments
   it. Without the bound the loop circulates doubt instead of topics, which is
   `C-001` wearing a new costume.

> **This is the damping the loop was missing.** §2 raises the objection that a
> positive feedback loop amplifies whatever bias the three axes share, and asks
> for damping without naming a mechanism. A channel in which **any axis can
> invalidate another axis's input** is negative feedback, and it is the first
> mechanism in this design that is one.

> **This already happens, by hand.** MS
> `kb/expertise/oil-objective-trapping-in-water` **is a challenge that was
> upheld.** A human observed on 2026-08-18 that oil objectives do trap in an
> aqueous sample; the entry records that *"that observation is correct and it
> corrected this project: lens 7 had been refusing those objectives
> outright."* It carries `evidence: measured`, `review_after: 2027-08-18` and
> `supersedes: null` — a resolution, a retirement date, and a supersession slot.
> **The mechanism is not being invented here.** What is missing is only that it
> runs inside one repository instead of between three.

**Not to be confused with `question/`.** A `question/` entry is a value persona
asking something about a **topic candidate**, and it dies when the literature
turns out to answer it. A challenge is aimed at **a claim already in the KB**, and
it dies when the claim's own falsifier is run. Different target, different death
condition. → [kb-schema.md](design/kb-schema.md) §4.2

> **Where the challengeable surface actually is.** BD's `entries/` store is 135
> entries distributed **52 `tooling` · 45 `method` · 25 `handbook` · 10 `intake`
> · 3 `paper`** — BD's own note on that table is that the tooling-to-paper gap
> *"is widening."* So most of what is recorded is *our machinery misled us*, not
> *the literature said something*. **The scientific claims worth doubting are in
> `source/papers/` (42), `wiki/findings/` (23) and `wiki/benchmarks/` (5)** — not
> in `entries/`. A challenge system pointed at the wrong store would find almost
> nothing to do.

**Where this belongs in the three jobs.** Not a fourth job — it is the half of
**J1** that the word "accumulate" leaves out. A knowledge base that only
accumulates goes stale, and BD `I-076` already named that failure: all the files
are there and search finds nothing. **Custody has to include retirement.**
[kb-schema.md](design/kb-schema.md) needs a seventh entry kind, `challenge/`, and
it is not written.

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

> **The corpus arrives after the system.** Papers and books are to be supplied
> later, so **every phase below has to be completable without them** — which is
> the order [kb-schema.md](design/kb-schema.md) §0 and `T-030` already argued for
> on independent grounds (fill before the form is fixed and you throw away what
> you filled). Two consequences.
>
> **① The supply layer's first job is ingest, not crawling.** Accepting a
> hand-supplied document is the path that exists on day one; the
> forward-citation index (Phase 3, `Q-006`) is what a corpus needs *after* it
> arrives, not what gets it there.
>
> **② A book never enters the repository.** BD already solved this — an
> `origin: handbook` entry's `source` reads
> `distillation#section ← [short-name] p.page`, so *"a claim can be walked back
> to the page it came from **without the book being in the repository**."* That
> is the contract for the books to come, and it is already running for two.

### Phase 0 — sketch (now)

| Task | Exit condition |
|---|---|
| Fix the boundaries between the three repos | [charter.md](design/charter.md) §3 is filled with no item owned twice |
| Register ideas, conflicts, questions | [ideas.md](design/ideas.md) — **register, do not resolve** |
| Read the microscope's `kb/expertise/` | ✅ **2026-09-05 — `Q-002` closes, on neither branch it offered.** The *contents* are instrument- and lab-bound (`n_medium = 1.333` for this lab's samples, this nosepiece's oil, `applies_to_systems: [current, …]`), so §2③ holds and **J1's basis survives**. But the *frontmatter* is domain-neutral — `question · source · expert · confidence · evidence · scope · applies_to_systems · review_after · supersedes`. **The form transfers although no value does, and the form is J3's business, not J1's** |
| Re-derive [charter.md](design/charter.md) §2 from the BD **remote** | ◐ **partially, 2026-09-05.** `T-041` was right: one row is now **false** — BD's knowledge base is built, not `raw` (46 wiki pages · 135 entries · 227 run post-mortems) → §2.1. The other rows are not re-derived, and §2's caveat 2 still stands |

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
| **What J1 may write into a public repo** | `T-044` · `T-019`① — the rule exists and is enforced **before the first topic assessment lands.** This repo is public, and deleting the file afterwards does not undo the disclosure → §8 |

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

**What changed on 2026-09-05:** the seven exchange points are now written down against the live repositories (§2.1), so this section is no longer choosing between three shapes in the abstract. **Row 2 is testable under option A** — BD holds 44 literature distillations, the microscope holds an empty folder built to receive exactly that, and indexing the two is reversible. Whether the remaining rows need B or C is a question about rows 3 and 7, not about all seven at once.

**But integration is open.** Three candidates:

| Option | Shape | Gains | Loses |
|---|---|---|---|
| **A. Three repos + indexing** *(current)* | This repo points at the other two | Reversible. Neither repo is touched | Risk of two sets of criteria. Cross-references are manual |
| **B. Monorepo** | All three in one | One set of criteria. References never break | **The disclosure obstacle is gone** — all three repos are public, and this one stays public by decision (§8). What is left against B is timing, not scope |
| **C. This repo as the orchestrator** | The other two as submodules, the loop runs here | The three-axis loop becomes real | This repo becomes an enforcer and violates its own structural prohibition ([charter.md](design/charter.md) §5) |

**B's obstacle was disclosure scope, not engineering — and that obstacle is gone.** `agentic-microscope` became public on 2026-08-28 after the vendor material was stripped, and **this repo is public by decision as of 2026-09-04** (§8). *"Put them in one repo and the stricter side wins"* needed two different scopes. There is one. **`C-006` is dissolved, not relaxed.** → `T-044`

**Which does not make B the answer — it exposes the quieter argument.** Disclosure was the loud objection, and it was doing the work of looking like the only one. `T-004`'s actual grounds never mentioned it: **indexing is reversible, migration is not.** Nor does the decision point below.

**The sequence, for the record.** Removing names on 2026-08-31 (`T-018` · `C-006`) took away the largest argument and moved B from impossible to discussable. `T-019`'s two remaining arguments held the ceiling there. The 2026-09-04 decision removed the ceiling **by settling the scope question, not by answering `T-019`** — both of its reasons survive as constraints on content (§8). So B is now possible on disclosure grounds and undecided on every other one.

**Decision point:** after Phase 1, once it is clear whether divergence records come out in a form BD and the microscope can actually use. Integrating before that fixes the structure without knowing what is being integrated. → `Q-008`

---

## 8. Disclosure scope — public, and what that costs

> **Decided 2026-09-04: this repository stays public.** It has been public since it was created on 2026-09-01, and an earlier draft of this section described it as private, which was never true of the repository as published. The decision settles **visibility**. It does not retract `T-019`'s two reasons — each one becomes a constraint on **content** instead, and one of them is not yet written down. → `T-044`

### The original reason for private, and how it was already removed

In the first draft a persona distilled **a named researcher's research philosophy**. That produces sentences like:

> *"To Prof. X this system would look like a problem whose answer is already known."*

**A value judgment attributed to a named researcher becomes a matter of reputation once public.** BD's roster of ~200 is entirely real people, many of them living. `agentic-microscope` could go public because its lenses were **subsystems** (optics, detection, compute), not people.

**On 2026-08-31 this was removed at the definition stage rather than the output stage** (`T-018` · `T-035`) — a persona is not an individual but a **lineage defined by a body of literature**, and the rule is **citations stay, attributions go.** [lineages.md](design/personas/lineages.md) contains no names.

### The two reasons that argued for private, and what each one becomes

`T-019`:

1. **The topic assessments that will accumulate in the KB are unpublished research directions.** Nothing to do with names. **This one is not resolved, it is relocated.** Nothing of the kind is exposed today — J1 has not started and `kb/` does not exist — so it stops being a question about who can read the repo and becomes **a rule about what J1 is allowed to write into it.** That rule does not exist yet, and **it has to before the first topic assessment lands**: in a public repo, deleting the file afterwards does not undo the disclosure.
2. **The `V1` literature of axis `X1` overlaps the group's own output.** Without naming the lineage, **the reading list points at it anyway.** So how much `T-035`'s name-stripping actually strips **has not been measured** — and staying public means carrying that cost while it stays unmeasured. Measuring it no longer gates the repository; it decides whether `V1`'s entry points need thinning.

**Therefore:**

- **A content rule for J1 is now a Phase 2 interlock**, alongside the other two ways a KB dies. It is a writing rule, not a disclosure question, so it belongs with the schema rather than here. → §4 Phase 2
- **`C-006` dissolves** (§7). Its whole force was that two repos had different disclosure scopes; all three are public and this one stays public, so there is one scope. What survives in `Q-008` is the timing argument, which never depended on visibility.
- **Consent from the people involved is a separate matter, and this decision sharpens it.** They are no longer persona targets, but the literature overlap remains and is now public **by decision rather than by oversight**. → §6 agenda 8.
- **The prohibition in [_common.md](design/personas/_common.md) matters more, not less.** *"This person would find X uninteresting"* was forbidden as attribution without a basis — reasoning that never rested on the repo being private. What has changed is only the size of the audience for a slip.

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
| [design/charter.md](design/charter.md) | Boundaries between the three repos. The evidence that two of them converged — **§2 re-derived against the live remotes 2026-09-05** | `sketch` |
| [design/ideas.md](design/ideas.md) | Idea log (`T-` · `C-` · `Q-`) | `sketch` |
| [design/kb-schema.md](design/kb-schema.md) | J1's formal objects. The answer to BD `I-133`. **Seven entry kinds — `challenge/` added 2026-09-05** | `sketch` |
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

---

## Licence

[MIT](LICENSE), settled 2026-09-04 — the same as [agentic-microscope](https://github.com/kyu-softmatter/agentic-microscope) and [Brownian-Dynamics-Agent](https://github.com/kyu-softmatter/Brownian-Dynamics-Agent). **A documentation licence would have been the more exact instrument for a repo that is currently all prose**, and it was rejected on one ground: this is a software repo that has not got its code yet (`src/` arrives in Phase 1), and with `C-006` dissolved (§7) a monorepo is now possible on disclosure grounds. Choosing differently here would rebuild a smaller version of the seam that just came down.

**Two things it does not reach.** The **literature** these documents cite — the entry points in [lineages.md](design/personas/lineages.md) are citations, and a citation carries no right over the work it points at. And the **quotations from BD's design documents**, which are translated here; those are the same author's and MIT there, so nothing is in conflict, but they are that repo's text and not this one's.

**And the thing a licence cannot settle**, stated here because §8 is the section people will not read: MIT grants reuse of these documents. **It does not grant anything about the researchers whose literature the value lineages were back-derived from.** That is a consent question, not a copyright one → §8.
