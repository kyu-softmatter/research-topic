# KB formal objects — J1's schema

Drafted 2026-08-31 · **revised 2026-09-05** (a seventh entry kind, `challenge/` — §2 · §4.7) · status `sketch` — **no entries are created here. Only the shape is fixed.**
Related: [ideas.md](ideas.md) `T-031` · `T-030` · `T-047`–`T-049` · `C-005` · `C-007` · `Q-010` · BD:`I-133` · BD:`I-076`

---

## 0. What this document does

> **The JSON in §4 is an example, not a decision** → [README.md](../README.md) §0.
>
> **The only settled things are the single rule in §1 and the no-scalar rule in §3.** Field names, enum values, and the number of entry kinds are for **whoever builds J1 and J3.** The examples are written out concretely because §1's rule **cannot be checked in the abstract** — "do not use natural language as state" only becomes visible as a violation once fields are actually laid down.

**No KB entries are created.** Only their shape is fixed. Accumulation comes after Phase 2.

That order looks backwards on purpose. BD's `I-075` and `I-076` already diagnosed the two ways a KB dies — ① nobody fills it ② the index goes stale, so the files are all there and search finds nothing. Filling before the form is fixed means **throwing away what was filled when the form changes.**

---

## 1. One rule

> **Natural language goes only in fields a human reads. Any field used for branching, routing, or a verdict must be a formal value.**

This is the local form of BD's `I-133` (using an LLM-written natural-language summary as state). BD found that antipattern at `MDCrow/mdcrow/agent/memory.py:119`, and the replacement it demanded was *"a formal object of the shape `{engine, config hash, seed, steps completed, checkpoint, observable, convergence state}`."*

**Where the violation will happen here is predictable** — because a value judgment is natural language to begin with. The sentence "this topic is interesting" cannot be state.

### The check

For each schema: **what code reads this field and branches on it?** If anything branches, the field must be an enum, a number, an ID, or a boolean. If only a human reads it, natural language is fine.

| Field's role | Allowed |
|---|---|
| State · verdict · routing key | Enums only |
| Identifier · reference | An ID (a string, but **not free text**) |
| The **location** of evidence | ID + coordinates (DOI, section number, table row) |
| The **content** of evidence | Natural language — a human reads it |
| A value claim | **No scalar score** → §3 |

---

## 2. Entry kinds (draft, seven)

One file per entry. The filename is the ID.

| Kind | What | Written by | Read by |
|---|---|---|---|
| `literature/` | A literature entry plus its **conditions of validity** | this repo | BD · MS · J2 |
| `rigor/` | Axis definitions, the form of pass conditions, canonical sources (J3) | this repo | BD · MS |
| `question/` | A question plus its falsifier (`T-008`) | value personas | the J2 gate |
| `divergence/` | A divergence record (`T-011` · `C-005`) | the J2 gate | humans · BD · MS |
| `topic/` | A topic candidate | J2 | BD · MS · humans |
| `dead-end/` | A dead end (`T-032`) | **BD · MS** | J2 |
| `challenge/` | Doubt against a claim already in any of the three KBs, plus the routing of its falsifier (`T-047` · `T-048`) | **any of the three** | the repo that owns the falsifier · humans |

> **`dead-end/` was the only kind written from outside. `challenge/` is the first written from *any* side** — including BD and MS writing one against an entry held here. That is the point of it. → [charter.md](charter.md) §3 *"Ownership is fixed; the direction of a work order is not"*
>
> **Six kinds accumulate and one retires.** A KB that only accumulates goes stale — BD `I-076` named the failure as *all the files are there and search finds nothing*. `challenge/` is the half of J1 that the word "accumulate" leaves out: **custody has to include retirement.**

---

## 3. Value is not a scalar

**Forbidden: `value_score: 0.7`.**

One reason. A score makes it possible to **average across personas**, and the moment you average, divergence is gone. Divergence is this repo's product (`T-010`).

BD reached the same conclusion for the same reason — *"a verdict vector is not a consensus,"* and finding 1 of its gate prototype: *"the answer to Q-016 is: do not aggregate."* **Aggregation is forbidden on verdicts in BD and on value here.**

**Instead:** a persona emits only `met: yes | no | unknown` against the **value conditions** written into its own definition file. The conditions themselves are not manufactured at run time — the same discipline as BD `_common.md` §4's "no numeric criterion without a citation," where **fixing the criteria as constants is how the no-new-knowledge rule gets kept.**

---

## 4. Draft schemas

### 4.1 `literature/`

```json
{
  "id": "lit-0001",
  "doi": "10.1103/PhysRevLett.113.028103",
  "kind": "paper | review | textbook | thesis",
  "authors": ["..."],
  "year": 2014,
  "claims": [
    { "id": "lit-0001.c1",
      "formula_ref": "eq. 7",
      "conditions": "when this expression holds -- the part that appears only in the original paper",
      "conditions_locator": "sec. III B, p. 3" }
  ],
  "outlook_section": { "present": true, "locator": "sec. V" },
  "cited_by_count": null,
  "index_source": "openalex | semanticscholar | manual",
  "retrieved": "2026-09-03"
}
```

> **`conditions` is why this entry kind exists.** As BD's `A5` section puts it: *"the expression is available anywhere, but its range of validity is in the original paper."* It is a natural-language field, but **humans and personas read it while no code branches on it**, so §1's rule is satisfied. What branches is `present` and `kind`.

### 4.2 `question/`

```json
{
  "id": "q-0001",
  "persona": "V1",
  "target_id": "topic-0003",
  "text": "the question, one sentence. Presupposes no conclusion",
  "unknown": "what the unknown is -- named precisely enough to recognize the answer on sight",
  "citations": ["lit-0001"],
  "falsifier": {
    "search_query": "...",
    "expected_authors": ["..."],
    "expected_venues": ["..."],
    "dies_if": "literature satisfying this condition exists"
  },
  "gate_verdict": "open | answered_in_kb | answered_in_literature | not_searched",
  "answered_by": null,
  "search_budget_spent": 0
}
```

> **`gate_verdict` is where BD's `I-052` is enforced** — search-result presence, not an LLM vote.
> **`not_searched` is the default, not `open`** (BD `I-055`: the default is failure).
> **Why `search_budget_spent` is recorded** (`T-023`): without it, `open` cannot be told apart from "we did not look hard enough," and then **the search budget becomes the value judgment.**

### 4.3 `divergence/` — `C-005`'s closing condition

```json
{
  "id": "div-0001",
  "target_id": "topic-0003",
  "personas": ["V1", "V2"],
  "axis": "reducibility | mechanism_vs_phenomenology | measurability",
  "conditions_met": { "V1": ["c1:no", "c3:yes"], "V2": ["c2:yes"] },
  "shared": ["facts both agree on -- a list of IDs"],
  "contested": {
    "claim": "the single point of divergence, as a sentence",
    "V1_position": "supports | opposes | unknown",
    "V2_position": "supports | opposes | unknown"
  },
  "resolvable_by": "bd_run | ms_experiment | literature | not_resolvable",
  "resolution_target": "what measurement would make the divergence stop diverging",
  "routed_to": null
}
```

> **`resolvable_by` is `T-034`'s damping device.** `not_resolvable` means the topic does not enter the loop and goes to the human path. Without this field the three-axis loop keeps circulating unfalsifiable topics (`C-001`).
> **`axis` is an enum.** Left as natural language it cannot be branched on and violates `T-031`. **The three values shown are now known to be wrong, not merely draft** — `T-051` replaced the axes on 2026-09-05 with **trend · difficulty · impact**, so the enum reads `trend | difficulty | impact` once [lineages.md](personas/lineages.md) is rewritten. It is left as-is here because **the poles' value conditions are empty and `C-008` blocks the procedure that would fill them**, and renaming an enum whose members have no definitions buys nothing. Settle it in Phase 1 after seeing two real cases.

### 4.4 `topic/`

```json
{
  "id": "topic-0003",
  "keywords": ["..."],
  "questions": ["q-0001", "q-0002"],
  "divergences": ["div-0001"],
  "falsifiable_by": "bd_run | ms_experiment | both | neither",
  "state": "candidate | routed | in_progress | concluded | dead",
  "dead_end_ref": null,
  "human_signoff": null
}
```

> **A topic with `falsifiable_by: neither` does not go on the automatic path** (`T-034`).
> **While `human_signoff` is `null`, "this has value" is recorded nowhere** (`T-007` · BD `I-057`).

### 4.5 `rigor/` — J3

```json
{
  "id": "rigor-A5",
  "name": "thermodynamic consistency",
  "pass_conditions": [
    { "id": "E8",
      "question": "the pass condition, one sentence",
      "form": "identity | inequality | comparison_to_analytic | declaration | declaration_plus_compatibility",
      "canonical_source": ["lit-0001"],
      "threshold_owner": "bd | ms",
      "implemented_in": { "bd": "A5.E8", "ms": null } }
  ]
}
```

> **`threshold_owner` is where [charter.md](charter.md) §3's boundary table is enforced.** This repo holds the `form` and the `canonical_source`, and **does not hold values.**
> **The `form` value list was back-derived from BD's ten axes.** `declaration_plus_compatibility` is what BD `_common.md` §7 found — a criterion that only takes a declaration misses the case where what was declared cannot carry the goal, so it needs a paired compatibility criterion. **In BD only `A10.T1b` implements this; `A2`, `A4`, and `A7` have no pair.** J3 is where that gap should be held as a table.

### 4.6 `dead-end/`

Uses BD's `I-077` template unchanged — what was tried / what diverged / **which hypotheses were excluded** / which remain / what to do differently.

```json
{
  "id": "de-0001",
  "topic_id": "topic-0003",
  "origin": "bd | ms",
  "tried": "...", "diverged": "...",
  "hypotheses_excluded": ["..."], "hypotheses_remaining": ["..."],
  "cost": { "gpu_hours": 0, "instrument_hours": 0 }
}
```

> **`hypotheses_excluded` is the whole value.** BD's own reason, unchanged: *"'it did not work under these conditions' is information bought with GPU time, and unrecorded, the next session spends that money again."*

### 4.7 `challenge/` — `T-047`'s formal object

```json
{
  "id": "chal-0001",
  "target": { "repo": "bd | ms | research-topic",
              "entry": "knowledge/source/papers/2005-pantina-furst-bending-coefficient.md",
              "claim": "which claim in it -- an ID or a section locator" },
  "raised_by": "bd | ms | research-topic",
  "doubt_kind": "conditions_not_met | superseded_by_measurement
                 | contradicted_by_run | scope_exceeded | never_verified",
  "falsifier_cited": "the target's own falsification condition, quoted by locator",
  "resolvable_by": "bd_run | ms_experiment | literature | not_resolvable",
  "routed_to": "bd | ms | research-topic | human",
  "state": "raised | routed | declined | running | upheld | rejected | unknown",
  "resolved_by": null,
  "depth": 0,
  "cost": { "gpu_hours": 0, "instrument_hours": 0, "search_budget_spent": 0 }
}
```

**`falsifier_cited` is what makes this a work order rather than an argument** (`T-048`). It is **mandatory**, and it must point into the target, not into the challenger. Consequences worth stating because they look like bugs:

- **An entry with no falsifier cannot be challenged.** That is a defect in the entry — philosophy ③ says every judgment carries the check that would overturn it — and not a gap here.
- **A challenge may not cite a new basis.** Doing so is `T-048`'s prohibited move and reintroduces `C-005`: a natural-language mass of counter-argument in the slot [personas/_common.md](personas/_common.md) §3 vacated.

### `state` — and where it is not deterministic

| Value | Set by | Deterministic |
|---|---|---|
| `raised` · `routed` | the gate, from `doubt_kind` → `resolvable_by` → `routed_to` | ○ — a lookup table |
| `declined` | **the receiving repo.** By [charter.md](charter.md) §3, values and budget are BD's and MS's, so a challenge **must be refusable** | ○ |
| `running` | the receiving repo | ○ |
| `upheld` · `rejected` | **the result.** A run's number, a measurement, or search-result presence — never a vote (BD `I-052`) | ○ **for `bd_run` and `ms_experiment`** |
| `unknown` | no verdict reachable | ○ |

> **⚠ `resolvable_by: literature` is the hole, and it is `C-007`.** The other two routes resolve on code producing a number. This one resolves on **someone reading the paper**, which is an LLM reading and therefore the thing `I-052` forbids of a gate. **It is the same problem as [personas/_common.md](personas/_common.md) §7's "who computes `shared`"** — appearing twice, solved neither time. The partial escape that keeps the gate deterministic is to let this repo resolve only **presence or absence of a locator** (does the cited section exist; does it state the condition) and emit `unknown` otherwise. **That is checkable and it answers a weaker question than the challenge asked.** Not adopted — recorded as the cost of each option in `C-007`.

**`depth` and `cost` are the bound** (`T-049` · `Q-010`). A challenge against a challenge increments `depth`. Without it the loop circulates doubt instead of topics, which is `C-001` in a new costume. **`cost` is recorded for the same reason `T-023` records `search_budget_spent`:** unrecorded, the budget stops being a budget and becomes the retirement decision.

**`not_resolvable` goes to the human path**, exactly as in §4.3. Same damping device (`T-034`), same reason.

> **Not the same as `question/`.** A `question/` entry is a value persona asking about a **topic candidate**, and it dies when the literature turns out to answer it. A `challenge/` is aimed at **a claim already in a KB**, and it dies when that claim's own falsifier is run. **Different target, different death condition** — and the field that separates them is `falsifier_cited`, which a `question/` does not have and cannot borrow.

---

## 5. The search index

**Entry files are canonical; the index is derived.** No code path exists for editing the index by hand.

BD `I-076`: *unless the index is refreshed at the end of every cycle, the next session cannot find the knowledge written this one — the state where all the files are there and search does not work.* So the refresh is a hook, not a document (Phase 2).

**BD `I-053`'s two-layer separation carries over** — persona definition files and the search corpus stay separate, and perspective separation is produced not by separate stores but by **a different search query per persona.** Consequence: a large corpus **costs nothing in context** (it is an index, not context). That is why the corpus is not trimmed (BD `I-069`).

---

## 6. Open

- **The value list for `divergence.axis`** — settle after two real cases in Phase 1.
- **Whether `literature.conditions` being natural language is actually safe.** If a persona reads that field and decides on it, that is routing. Check in Phase 1 whether it is read only or branched on.
- **Who issues entry IDs.** Sequential numbers collide under parallel writes.
- **Detecting when `rigor/` drifts from BD's and MS's real files.** Hand-maintained `implemented_in` goes stale — the same failure BD named for the index.
- **`challenge/`'s literature route has no deterministic resolver** — `C-007`. Two of three routes resolve on a result; the third resolves on a reading. **The largest unclosed item in this document**, and it is the same problem as *"who computes `shared`"*.
- **A challenge has no cost ceiling and no declined-forever state** — `Q-010`. A falsifier that is never run is indistinguishable from one that failed, so `declined` needs to either expire or retire, and neither is specified.
- **Which store a challenge may point at.** BD's `entries/` is 135 entries but only **3** are `paper`-origin; the scientific claim surface is `source/papers/` (42) and `wiki/findings/` (23) → `T-045`④. **Pointed at the wrong store, the mechanism finds nothing to do**, and that is a targeting decision, not a schema one.
