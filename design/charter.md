# Boundaries — what lives here and what lives there

Drafted 2026-08-31 · status `sketch`
Related: [ideas.md](ideas.md) `T-001`–`T-006` · `T-041` · `Q-001`–`Q-003`

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
| **A knowledge base** | `I-032` — **still `raw`. Not built** | `kb/systems`, `kb/calibrations`, `kb/expertise`, `kb/decisions`, with R/W marked in the architecture | ✗ **Absent in BD** |

### What this table says

**① The top six rows converging means those six are not domain-specific.** Colloidal BD and optical microscopy reached the same shape with no common ancestor. That is the actual scope of what J3 manages — axis division, deterministic enforcement, default-failure, an attached falsifier, and where the LLM sits.

**② The bottom three did not converge, and all three lean one way.** All are present only in the microscope. Two of them — the self-review lens and the never-met detector — are BD's to import, and not this repo's business.

**③ The remaining one is this repo's business.** The microscope's `kb/` is **bound to the instrument** — `kb/systems/current.md` is "which machine this microscope actually is." BD cannot use that. So the KB needs a third place. This is the basis for J1, and **it follows independently of the user having asked for J1 first.**

> **Caveat 1 — not yet checked.** The file contents of the microscope's `kb/expertise/` were never read. If what is in there is already domain-neutral, the conclusion in §2③ weakens. → [ideas.md](ideas.md) `Q-002`
>
> **Caveat 2 — the sources this comparison used.** This table was built from `/d/BD/design/` (local, not under git) and `/d/backup/연구/agentic-microscope-prefilter.git` (a bare backup, `HEAD` = `9f4517d`). **The live repos are [Brownian-Dynamics-Agent](https://github.com/kyu-softmatter/Brownian-Dynamics-Agent) and [agentic-microscope](https://github.com/kyu-softmatter/agentic-microscope), and the microscope's name differs from the backup's.** BD's public description suggests the remote is **ahead of** the snapshot that was read, which would make this table stale. Re-deriving it from the remotes is bundled with `Q-002`. → `T-041`

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

The last row is the only place this repo parts from BD, and it is the most dangerous decision in its design.
