# KB 형식 객체 — J1의 스키마

작성: 2026-08-31 · 상태: `sketch` — **항목을 채우지 않는다. 형식만 정한다.**
관련: [ideas.md](ideas.md) `T-031` · `T-030` · `C-005` · BD:`I-133` · BD:`I-076`

---

## 0. 이 문서가 하는 일

> **§4의 JSON은 결정이 아니라 예시다** → [README.md](../README.md) §0.
>
> **확정된 것은 §1의 규칙 하나와 §3의 스칼라 금지뿐이다.** 필드 이름·열거형 값·항목 종류의 수는 **J1·J3를 구축하는 사람이 정한다.** 예시를 구체적으로 쓴 이유는 §1의 규칙이 **추상적으로는 지켜지는지 확인할 수 없기** 때문이다 — "자연어를 상태로 쓰지 말라"는 필드가 실제로 놓여 봐야 위반이 보인다.

**KB 항목을 만들지 않는다.** 어떤 모양이어야 하는지만 정한다. 항목 축적은 Phase 2 이후다.

이 순서가 반대로 보이는 것은 의도다. BD `I-075`·`I-076`이 KB가 죽는 두 경로를 이미 진단해 뒀다 — ① 아무도 안 채운다 ② 인덱스가 낡아서 파일은 다 있는데 검색이 안 된다. 형식을 정하기 전에 채우면 **형식이 바뀔 때 채운 것을 버려야 한다.**

---

## 1. 단 하나의 규칙

> **자연어는 사람이 읽는 필드에만 둔다. 분기·라우팅·판정에 쓰이는 필드는 형식 값이어야 한다.**

BD `I-133`(LLM이 쓴 자연어 요약을 상태로 사용)의 이 레포판이다. BD가 그 안티패턴을 발견한 자리는 `MDCrow/mdcrow/agent/memory.py:119`였고, 요구된 대체물은 *"`{엔진, 설정 해시, 시드, 진행 스텝, 체크포인트, 관측량, 수렴 상태}` 형태의 형식 있는 객체"* 였다.

**이 레포에서 위반이 일어나는 자리는 예측 가능하다** — 가치 판단이 원래 자연어이기 때문이다. "이 주제는 흥미롭다"는 문장은 상태가 될 수 없다.

### 검사

각 스키마에 대해: **어떤 코드가 이 필드를 읽고 분기하는가?** 분기한다면 그 필드는 열거형·수·ID·불리언이어야 한다. 사람만 읽는다면 자연어 허용.

| 필드 성격 | 허용 |
|---|---|
| 상태 · 판정 · 라우팅 키 | 열거형만 |
| 식별자 · 참조 | ID (문자열이나 **자유 텍스트가 아니다**) |
| 근거의 **위치** | ID + 좌표 (DOI · 절 번호 · 표 행) |
| 근거의 **내용** | 자연어 허용 — 사람이 읽는다 |
| 가치 주장 | **스칼라 점수 금지** → §3 |

---

## 2. 항목 종류 (초안 6종)

각 항목은 파일 하나. 파일명이 ID.

| 종류 | 무엇 | 누가 쓰나 | 누가 읽나 |
|---|---|---|---|
| `literature/` | 문헌 항목 + **성립 조건** | 이 레포 | BD · MS · J2 |
| `rigor/` | 엄밀성 축 정의 · 통과 조건의 형식 · 원전 (J3) | 이 레포 | BD · MS |
| `question/` | 질문 + falsifier (`T-008`) | 가치 페르소나 | J2 게이트 |
| `divergence/` | 분기 기록 (`T-011` · `C-005`) | J2 게이트 | 사람 · BD · MS |
| `topic/` | 주제 후보 | J2 | BD · MS · 사람 |
| `dead-end/` | 막다른 길 (`T-032`) | **BD · MS** | J2 |

> **`dead-end/`만 쓰는 쪽이 밖이다.** 이 레포는 보관만 한다. → [charter.md](charter.md) §3

---

## 3. 가치는 스칼라가 아니다

**금지: `value_score: 0.7`.**

이유는 하나다. 점수를 내면 **여러 페르소나의 점수를 평균할 수 있게 되고**, 평균하는 순간 분기가 사라진다. 그런데 분기가 이 레포의 산출물이다 (`T-010`).

BD가 같은 이유로 같은 결론에 도달해 있다 — *"판정 벡터는 합의가 아니다"*, 그리고 게이트 시제품의 발견 1: *"Q-016의 답은 집계하지 않는다"*. **집계 금지가 BD에서는 판정에, 여기서는 가치에 걸린다.**

**대신:** 페르소나는 자기 정의 파일에 박힌 **가치 조건**들에 대해 `met: yes | no | unknown`만 낸다. 조건 자체는 실행 시점에 만들지 않는다 (BD `_common.md` §4의 "인용 없는 수치 기준 금지"와 같은 방식 — 조건을 상수로 박는 것이 지식 주장 금지를 지키는 방식이다).

---

## 4. 스키마 초안

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
      "conditions": "이 식이 언제 성립하는가 — 원 논문에서만 나오는 것",
      "conditions_locator": "§III B, p. 3" }
  ],
  "outlook_section": { "present": true, "locator": "§V" },
  "cited_by_count": null,
  "index_source": "openalex | semanticscholar | manual",
  "retrieved": "2026-09-03"
}
```

> **`conditions`가 이 항목의 존재 이유다.** BD `A5` 절이 명시한 것 — *"식은 어디서나 구하지만 유효 범위는 원 논문에 있다."* 자연어 필드지만 **사람과 페르소나가 읽고 코드가 분기하지 않으므로** §1 규칙에 걸리지 않는다. 분기하는 것은 `present`·`kind`뿐이다.

### 4.2 `question/`

```json
{
  "id": "q-0001",
  "persona": "V1",
  "target_id": "topic-0003",
  "text": "질문 한 문장. 결론을 전제하지 않는다",
  "unknown": "무엇이 미지수인가 — 답을 보면 알아볼 수 있을 만큼 지목",
  "citations": ["lit-0001"],
  "falsifier": {
    "search_query": "...",
    "expected_authors": ["..."],
    "expected_venues": ["..."],
    "dies_if": "이 조건을 만족하는 문헌이 나오면 이 질문은 죽는다"
  },
  "gate_verdict": "open | answered_in_kb | answered_in_literature | not_searched",
  "answered_by": null,
  "search_budget_spent": 0
}
```

> **`gate_verdict`가 BD `I-052`의 집행 지점이다** — LLM 투표가 아니라 검색 결과 유무.
> **`not_searched`가 기본값이다.** `open`이 아니다 (BD `I-055` 기본값은 실패).
> **`search_budget_spent`를 기록하는 이유** (`T-023`): 이게 없으면 `open`이 "정말 없다"인지 "덜 찾았다"인지 구분이 안 되고, **검색 예산이 곧 가치 판정**이 된다.

### 4.3 `divergence/` — `C-005`의 해소 조건

```json
{
  "id": "div-0001",
  "target_id": "topic-0003",
  "personas": ["V1", "V2"],
  "axis": "reducibility | novelty_of_state | measurability | generality | mechanism_vs_phenomenology",
  "conditions_met": { "V1": ["c1:no", "c3:yes"], "V2": ["c2:yes"] },
  "shared": ["둘이 동의하는 사실 — ID 목록"],
  "contested": {
    "claim": "갈리는 지점 하나. 문장",
    "V1_position": "supports | opposes | unknown",
    "V2_position": "supports | opposes | unknown"
  },
  "resolvable_by": "bd_run | ms_experiment | literature | not_resolvable",
  "resolution_target": "무엇을 재면 갈리는 것이 갈리지 않게 되나",
  "routed_to": null
}
```

> **`resolvable_by`가 `T-034`의 감쇠 장치다.** `not_resolvable`이면 루프를 돌지 않고 사람 경로로 간다. 이 필드가 없으면 3축 루프가 반증 불가능한 주제를 계속 순환시킨다 (`C-001`).
> **`axis`는 열거형이다.** 자연어로 두면 분기가 안 되고 `T-031`을 위반한다. 값 목록은 **Phase 1에서 실례 2개를 보고 정한다** — 지금 정하면 근거 없이 정하는 것이다.

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

> **`falsifiable_by: neither`인 주제는 자동 경로에 올리지 않는다** (`T-034`).
> **`human_signoff`가 `null`인 동안 "가치 있다"는 어디에도 기록되지 않는다** (`T-007` · BD `I-057`).

### 4.5 `rigor/` — J3

```json
{
  "id": "rigor-A5",
  "name": "열역학적 정합성",
  "pass_conditions": [
    { "id": "E8",
      "question": "통과 조건 한 문장",
      "form": "identity | inequality | comparison_to_analytic | declaration | declaration_plus_compatibility",
      "canonical_source": ["lit-0001"],
      "threshold_owner": "bd | ms",
      "implemented_in": { "bd": "A5.E8", "ms": null } }
  ]
}
```

> **`threshold_owner`가 [charter.md](charter.md) §3 경계표의 집행 지점이다.** 이 레포는 형식(`form`)과 원전(`canonical_source`)을 갖고, **값은 갖지 않는다.**
> **`form`의 값 목록은 BD의 열 축에서 역산했다.** `declaration_plus_compatibility`는 BD `_common.md` §7이 발견한 것 — 선언만 받는 기준은 선언된 것이 목표를 담지 못하는 경우를 놓치므로 짝이 되는 양립성 기준을 갖는다. **BD에서는 `A10.T1b`만 구현돼 있고 `A2`·`A4`·`A7`은 짝이 없다.** J3가 이 결손을 표로 들고 있어야 할 자리다.

### 4.6 `dead-end/`

BD `I-077`의 템플릿을 그대로 쓴다 — 무엇을 시도했나 / 무엇이 어긋났나 / **배제한 가설** / 남은 가설 / 다음에 다르게.

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

> **`hypotheses_excluded`가 값어치의 전부다.** BD가 적어 둔 이유 그대로 — *"이 조건에서는 안 됐다"는 GPU 시간으로 산 정보이고, 안 남기면 다음 세션이 같은 돈을 다시 쓴다.*

---

## 5. 검색 인덱스

**항목 파일이 정본이고 인덱스는 파생물이다.** 인덱스를 손으로 고치는 경로를 만들지 않는다.

BD `I-076`: *매 사이클 끝에 인덱스를 갱신하지 않으면 이번에 쓴 지식을 다음 세션이 못 찾는다 — 파일은 다 있는데 검색이 안 되는 상태.* 그래서 갱신은 훅이고 문서가 아니다 (Phase 2).

**BD `I-053`의 2층 분리를 승계한다** — 페르소나 정의 파일과 검색 코퍼스를 분리하고, 관점 분리는 저장소가 아니라 **페르소나마다 다른 검색 쿼리**로 만든다. 딸린 결과: 코퍼스가 커도 **컨텍스트 비용이 없다**(인덱스이지 컨텍스트가 아니므로). 그래서 명단을 지금 줄이지 않는다 (BD `I-069`).

---

## 6. 미결

- **`divergence.axis`의 값 목록** — Phase 1의 실례 2개를 보고 정한다.
- **`literature.conditions`가 자연어인 것이 정말 안전한가.** 페르소나가 이 필드를 읽고 판단하면 그건 라우팅이다. 읽기만 하는지 분기하는지 Phase 1에서 확인.
- **항목 ID 발급 주체.** 순번이면 병렬 기입에서 충돌한다.
- **`rigor/`가 BD·MS의 실제 파일과 어긋날 때의 탐지.** `implemented_in`이 손으로 관리되면 낡는다 — BD `I-076`이 인덱스에 대해 말한 것과 같은 실패.
