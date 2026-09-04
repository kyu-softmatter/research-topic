# The common contract for value personas

Drafted 2026-08-31 · revised 2026-08-31 (names removed) · status `sketch`
Related: [ideas.md](../ideas.md) `T-005`–`T-019` · `C-002` · `C-005` · BD `personas/_common.md`

Inherits BD's axis-persona contract with **two changes.** Everything else carries over.

| What | BD axis persona | Value persona |
|---|---|---|
| Unit of division | Rigor axes `A1`–`A10` — **one per axis** | Poles of a value axis `V1`–`V6` — **two per axis** (`T-018`) |
| Output type | A verdict | **Questions + whether conditions are met** (`T-005`) |
| Where the falsifier comes from | A code check | **Trajectory consistency of a body of literature** (`T-014`) |
| Disagreement | A bug — rebuttal forbidden | **The product — recorded as divergence** (`T-011`) |
| The other seven prohibitions | — | Inherited unchanged (§4) |

> **A persona is not an individual** (`T-018`). A `V?` is **a lineage defined by a body of literature**; that the literature belongs to real researchers shows up only as citations. Definition files **make no attribution by name** (§5). The axes and poles → [lineages.md](lineages.md).
>
> **The output schema in §2 is an example** → [README.md](../../README.md) §0. What is settled is **the five rows above and the prohibitions and procedure in §3–§5**; field names and enum values are for whoever builds this.

---

## 1. Interface

```
in     : the shared target (keywords / topic candidate / paper / system)
         + its own definition file + the supplied literature list
out    : 2-3 questions + a falsifier for each + whether its own value conditions are met
banned : modifying the target . claiming new knowledge . answers . methods . code
         . originating numbers . deciding thresholds
```

**Same as BD:** a persona is **read-only**, and it **names** criteria without enforcing them.

**Different from BD:** the output is questions, not a verdict. BD `I-050` already fixed that shape —

> *"Write only 2-3 questions. No answers, methods, or code. Each question must cite at least one of the supplied references. Name the unknown precisely enough that you would recognize the answer on sight. Do not presuppose a conclusion."*

**That instruction is used as-is.** The condition BD attached when parking the item under `I-064` — *"revive this if producing questions becomes necessary again"* — is this repo.

---

## 2. Output schema

```json
{
  "persona": "V?",
  "lineage": "...",
  "target_id": "topic-0003",
  "questions": ["q-0001", "q-0002"],
  "value_conditions": [
    { "id": "c1",
      "met": "yes | no | unknown",
      "evidence_kind": "outlook_section | trajectory | absence | none",
      "evidence": ["lit-0001"],
      "trajectory_check": {
        "claimed_direction": "...",
        "papers_found": 0,
        "verdict": "consistent | absent | contradicted | not_run"
      } }
  ],
  "escalate_to_human": false,
  "escalate_reason": []
}
```

### `met` values

| Value | Meaning |
|---|---|
| `yes` | This lineage's value condition is met — with a basis |
| `no` | Not met — with a basis |
| `unknown` | **No verdict possible.** The target has no material to judge that condition on |

**The default is not `yes`.** With no basis for a verdict, it is `unknown` (BD `I-055`).

### Fields that do not exist

- **No `value_score`.** Scalars are forbidden → [kb-schema.md](../kb-schema.md) §3. A score can be averaged, and averaging destroys divergence.
- **No `verdict`.** Settling value is the human path (`T-007` · BD `I-057`).
- **No numbers.** A persona originates none — `papers_found` is filled by the search result.

### `trajectory_check` — this repo's one immediate check

`T-014`. If a pole says "direction X is interesting," look for whether **X actually appears in that lineage's literature.**

| `verdict` | Meaning | Next |
|---|---|---|
| `consistent` | It is there | The distillation is right in that direction |
| `contradicted` | The opposite direction is there | **Distillation error.** Fix the definition file |
| `absent` | It is not there | **ⓐ distillation error or ⓑ a real gap — cannot be told apart automatically** → `Q-005` |
| `not_run` | Not checked | Not a pass |

> **`absent` returns this repo's best product (ⓑ) and its worst failure (ⓐ) as the same value.** This is the core unsolved problem. Agenda 5 (`Q-005`).

---

## 3. The one prohibition not inherited — divergence

The last prohibition in BD `_common.md` §4 is **"no rebutting another persona — a verdict vector is not a consensus."** That one is dropped.

**The vacated slot is not left empty.** Left empty, the personas produce a natural-language mass of counter-argument, which violates `T-031` (formal objects) — `C-005`.

**Specified:** not rebuttal but a **divergence record**.

| Allowed | Forbidden |
|---|---|
| Attaching opposite value to the same target | **Rebutting another persona's basis** |
| Naming the single point of divergence | Explaining the divergence as the other persona's error |
| Emitting agreed facts as `shared` | Referencing the other's definition file |

**The divergence record is written by the gate, not by a persona.** A persona emits only its own output; comparing two outputs to produce a `divergence/` entry is the gate's job (BD `I-098` — *"ordering and diagnosis belong to the gate"*).

Schema → [kb-schema.md](../kb-schema.md) §4.3. **`resolvable_by` is the damping device** — `not_resolvable` means the topic does not enter the loop and goes to the human path (`T-034` · `C-001`).

---

## 4. The seven prohibitions that are inherited

| Prohibited | Why (BD's reasoning kept) |
|---|---|
| **Modifying the target** | A persona is read-only |
| **Claiming new knowledge** | LLM-generated domain knowledge is unverifiable, and mixed into the KB it becomes the `I-133` antipattern |
| **Criteria without a citation** | Each persona's value conditions are **constants written into its definition file**, not values manufactured per target |
| **Offering answers** | `I-050` — asked for answers, an LLM will always produce something plausible, and unverifiable |
| **Offering methods or code** | Same |
| **Originating numbers** | The shared rule of both repos. Numbers come from search results and code |
| **Deciding thresholds and tolerances** | Values are domain-owned → [charter.md](../charter.md) §3 |

> **Fixing value conditions as constants is how the no-new-knowledge rule gets kept.** A persona that manufactures "this looks interesting enough" at run time is unverifiable. Same structure as what BD wrote about thresholds.

---

## 5. What goes in a definition file

Built by the `T-013` procedure.

> **① Write the value conditions first** ("what does this lineage need before it picks a problem?")
> **→ ② Find the review Outlook sections and the trajectory where those conditions show**
> **→ ③ If consistent, distill.**

This is the value counterpart of BD `I-096` (pass condition → source → author), and the order is the same for the same reason — **start from names and you end up collecting people without knowing what is being distilled.** After removing names (`T-018`) the order is unchanged: name a lineage first and then gather its literature, and it is the same failure.

| Section | Contents |
|---|---|
| **Value conditions** | `c1`, `c2`, ... one sentence each. **Constants** |
| **Sources** | Review Outlook sections (DOI + section number) · the trajectory (a list in year order) |
| **What was not done** | An adjacent area left untouched. `T-012`③ |
| **Trigger condition** | When this persona gets convened (§6) |
| **Question habits** | What **shape of question** this lineage asks — BD `I-053`'s "a different search query per persona" |

**Forbidden: sentences of the form "this person would find X uninteresting."** That is attribution without a basis — not distillation but guesswork, and it was the original reason this repo was going to be private (README §8). **The repo is public as of 2026-09-04, which makes the prohibition weigh more, not less**: the reasoning never rested on who could read the file, and now everyone can. A definition file holds only **value conditions and the locations of their basis.**

---

## 6. Trigger conditions — holding down cost

BD `I-067` held down the cost of ten axes with a per-axis trigger condition. After removing names (`T-018`) there is an upper bound here too (`Q-004` closed) — but **two poles per axis means one more axis is two more convenings.**

- Convene **once per topic** (BD `I-051`). Not once per iteration.
- The only re-convening condition is **hitting a wall**, and then "what was tried and why it failed" goes in with it.
- **If divergence is the goal, convene at least two.** Convene one and no `divergence/` exists.

---

## 7. Open

- **The number of poles** — closed as a count (`Q-004`), but the basis for three axes is a draft.
- **Telling ⓐ from ⓑ in `absent`** (`Q-005`). §2 names this as the repo's core gap.
- **The gate has no check to run on a `met` verdict.** BD ran falsifiers as code. The only thing runnable as code here is `trajectory_check`, and that measures **distillation quality**, not **whether the value judgment is right** → `C-003`.
- **Who computes `shared`.** The gate compares two persona outputs, but extracting "facts both agree on" is a natural-language comparison. That would make the gate an LLM and violate BD `I-052` (a deterministic gate).
