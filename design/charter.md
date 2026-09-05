# Boundaries — what lives here and what lives there

Status `sketch`
Drafted 2026-08-31 · **§2 revised 2026-09-05** (re-derived against the live remotes; `Q-002` closed, a fourth convergence added) · **§3 · §5 revised 2026-09-05** (challenge direction)
Related: [ideas.md](ideas.md) `T-001`–`T-006` · `T-041` · `T-045`–`T-050` · `C-007` · `Q-001`–`Q-003` · `Q-010`

---

## 1. Why a third repo

There is one reason not to put this inside either existing repo. **BD and the microscope are each the enforcer for their own domain, and if criteria shared by both live in one of them, the other has to import them.** With no settled direction of import, two sets of criteria appear.

That alone is a weak basis for a new repo. The real basis is §2.

---

## 2. What the two repos converged on independently — the evidence for J3

Built by comparing BD's `design/` against the microscope's `README.md` and `.claude/agents/`. Neither repo references the other.

| What | BD | microscope | Converged |
|---|---|---|---|
| **Unit of perspective** | Rigor axes `A1`–`A10` | 8 subsystem lenses | ○ Both divided **by axis, not by person** |
| **Who enforces a verdict** | `gate.md` — a deterministic gate | `compute/gate.py` + hard gates `G1`–`G32` | ○ |
| **Default** | `I-055` — the default is failure, not passing | `BLOCKED` is the default; it names the missing input | ○ |
| **What a judgment carries** | `I-065` — the check that would overturn it (a falsifier) | Each `kb/expertise/` entry carries its own falsifier | ○ |
| **Where the LLM sits** | Personas name the criteria; code settles them | The subagent supplies only the half with no closed form, and **originates no number** | ○ |
| **A self-review lens** | None | Lens 6 (validity) reviews the other lenses' verdicts, so it is called last | ✗ Absent in BD |
| **Detecting that the committee never met** | None | `G27` looks at nothing else | ✗ Absent in BD |
| **A knowledge base** | ~~`I-032` — still `raw`. Not built~~ **Superseded 2026-09-05.** BD has one: `knowledge/wiki/` (46 pages), `knowledge/source/` (42 papers + 2 books), `knowledge/entries/` (135 JSON), plus 227 run post-mortems | `kb/systems`, `kb/calibrations`, `kb/expertise`, `kb/decisions`, `kb/literature` (schema only, **0 entries**) | **○ — the row flipped.** Both have one, **and neither can read the other's** |
| **A published number is not a measurement** | Provenance `from_paper` · `assumed` · `derived` + a **tier**; a derived value is recomputed, never trusted as written | A literature value is always `assumed`, never `measured`, so **it cannot advance a verdict**; `## Transfer conditions` is a mandatory section | ○ **The fourth convergence — found 2026-09-05** |

### What this table says

**① The top six rows converging means those six are not domain-specific.** Colloidal BD and optical microscopy reached the same shape with no common ancestor. That is the actual scope of what J3 manages — axis division, deterministic enforcement, default-failure, an attached falsifier, and where the LLM sits.

**② Two of the bottom rows did not converge, and both lean one way.** The self-review lens and the never-met detector are present only in the microscope. Both are BD's to import, and not this repo's business.

**③ The knowledge-base row flipped on 2026-09-05, and J1's basis narrowed rather than fell.** When this table was built, BD had no KB, and *"BD cannot use the microscope's, because it is bound to the instrument"* was the whole argument for a third place. BD now has one. **Both halves of the original claim survive checking, and they no longer add up to the same conclusion:**

- The microscope's `kb/expertise/` was read on 2026-09-05 (`Q-002`). Its **contents** are instrument- and lab-bound — `n_medium = 1.333` for this lab's samples, this nosepiece's oil, `applies_to_systems: [current, …]`. BD cannot use them, as claimed.
- **BD's KB is simulation-bound in exactly the same way** — `wiki/systems/` cards, `concepts/` written in BD's own conventions. The microscope cannot use those either.

**So the two KBs are symmetric, not asymmetric, and that is a stronger basis for a third place than the original — but for a smaller thing.** What is *not* bound on either side is the literature layer: BD's `source/papers/` (42) and the microscope's `kb/literature/` (**0 entries, schema built and waiting**). **That intersection is J1's real scope.** → [README.md](../README.md) §2.1 row 2

**④ The fourth convergence is about a field, not a shape.** Rows 1–6 establish that the two repos agree on *how a system like this is put together*. The new row is different in kind: they agree on **what a literature entry must carry before anything may consume it** — the conditions under which the published number holds, and the rule that it never counts as a measurement. **The other six rows say an exchange is possible; this one says what the exchange is made of.**

> **Caveat 1 — checked 2026-09-05, and it closed on neither branch.** `Q-002` asked whether the microscope's `kb/expertise/` is domain-neutral, expecting §2③ to be either confirmed or weakened. The **contents** are not neutral (§2③ holds), but the **frontmatter is** — `question · source · expert · confidence · evidence · scope · applies_to_systems · review_after · supersedes`, with an evidence vocabulary of `measured` / `confirmed_default` / `assumed` and a rule about which of them may advance a verdict. **No value transfers and the whole form does.** That makes `kb/expertise/` evidence for **J3**, which owns the form of a pass condition (§3), and not the counter-evidence against J1 the question was looking for. → `Q-002` **closed**
>
> **Caveat 2 — partially re-derived 2026-09-05, and still not safe to trust.** This table was built from `/d/BD/design/` (local, not under git) and `/d/backup/연구/agentic-microscope-prefilter.git` (a bare backup, `HEAD` = `9f4517d`). **`T-041` predicted the remotes were ahead, and they are** — the knowledge-base row was false and is now rewritten, and one row was missing entirely. **But only the rows this session had reason to check were checked.** The other rows still rest on the snapshot, so a row here agreeing with a row there is not yet evidence that it agrees with the live repository. → `T-041`

---

## 3. The boundary table — who owns what looks shared

Same shape as the axis boundary table in BD `personas/_common.md` §5, and it inherits the same principle: **detection and diagnosis are separated.**

| Subject | Owner | The other repos |
|---|---|---|
| **The definition of a rigor axis** (what the axis asks) | **research-topic** | BD and MS hold their own domain instances |
| **The form of a pass condition** (what counts as checkable) | **research-topic** | BD and MS write their conditions in that form |
| **The value of a pass condition** (thresholds, tolerances) | **BD** / **MS**, each | research-topic **does not set values** |
| **The canonical-source list** | **research-topic** | BD and MS cite only |
| **Conditions of validity drawn from a source** ("when does this expression hold?") | **research-topic** | BD writes them into the registry's `conditions` field |
| **Topic candidates** | **research-topic** | BD and MS receive them as targets to test |
| **Whether a topic is testable** | **BD** / **MS** | research-topic emits; it does not judge testability itself |
| **Failures and dead ends** | **research-topic** (custody) | BD and MS write them (BD `I-077` template) |
| **Instrument state, calibrations** | **MS** | Does not come here |
| **Run provenance, seeds, engine versions** | **BD** | Does not come here |

> **Boundary principle:** research-topic holds **form and provenance**, and holds neither **values** nor **execution**.
> Holding values would make this repo the channel through which BD's own "no numeric criterion without a citation" gets violated on its behalf.

### Ownership is fixed; the direction of a work order is not

**Every row above stays as written.** What this table does *not* say, and was read as saying, is that work only ever travels one way.

It does not. A KB entry carries a falsifier, a falsifier is a check nobody has run, and **the type of the falsifier decides which repo can run it** — a local measurement goes to MS, a run goes to BD, an unchecked condition of validity comes back **here**. So BD and MS **send work to this repo** without any owner in the table changing. → [README.md](../README.md) §2.2 · `T-047`

| | Owner (unchanged) | May raise a challenge against it |
|---|---|---|
| A published number's conditions of validity | **research-topic** | **BD · MS** — when the number does not reproduce |
| A threshold's value | **BD** / **MS** | **research-topic** — when the cited source does not support it |
| Whether a topic is testable | **BD** / **MS** | **research-topic** — only by citing a dead-end record, never by judging testability itself |

**The last row is the one to watch.** `T-034`'s damping depends on this repo not deciding testability, and a challenge is the nearest thing to deciding it. The line: **a challenge may report that BD or MS already recorded this route as dead; it may not argue that a route is dead.**

---

## 4. Nothing migrates

BD's `design/personas/*.md` reference `ideas.md` `I-` numbers densely in their prose. Move the files and all of those references break.

**Decision (the reversible one):** do not move them. This repo holds **the canonical schema and the source registry**; BD's and MS's existing files stay where they are. What is needed is for this repo to **index** the two.

The grounds are BD `I-057` — a boundary is drawn at *is it reversible and checkable*. Indexing is reversible; migration is not.

**Revisit when:** BD and MS start writing the pass conditions of the same axis **in different forms.** At that point the form really has diverged and a canonical copy is needed.

---

## 5. What this repo does not do — structural prohibitions

| Prohibited | Why |
|---|---|
| **Originating numbers** | The shared rule of both repos. The LLM does not make numbers |
| **Deciding thresholds and tolerances** | §3. Values are domain-owned |
| **Running simulations or experiments** | This is not an enforcer |
| **Settling a topic's value** | Settling value is irreversible. Human path (BD `I-057`) |
| **Using natural language as state** | BD `I-133` antipattern. J1 dies exactly here → [kb-schema.md](kb-schema.md) |
| **A persona rebutting another persona** | ...**this one is not inherited.** → [personas/_common.md](personas/_common.md) §3 |
| **Settling a challenge whose falsifier it cannot run** | `T-048`. This repo may **route** a challenge and may resolve one whose falsifier is a literature check. `upheld` on a run or a measurement is BD's and MS's to set. Resolving those here would make this repo an enforcer, which is the same objection that rules out option C (→ [README.md](../README.md) §7) |

The rebuttal row is the only place this repo parts from BD, and it is the most dangerous decision in its design. **The row below it is where that danger reappears in a new place** — a challenge is the one mechanism in this design through which this repo touches another's verdict, and the only thing keeping it from being enforcement is that **the falsifier, not this repo, says who resolves it.**
