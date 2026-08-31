# 가치 관점 명단 — 데이터

작성: 2026-08-31 · 상태: `sketch`
관련: [ideas.md](../ideas.md) `T-009` · `T-012` · `T-013` · `Q-003` · `Q-004` · BD `design/personas-roster.md`

## 이 문서의 위치

[ideas.md](../ideas.md)는 **아이디어 로그**, 이 문서는 **데이터**다. BD `personas-roster.md`와 같은 관계.

**출처:** BD 명단 ~200명 중 소프트매터·액티브매터 계보만. **새로 발굴한 이름은 없다** — BD 명단이 이미 넓다(`I-069`).

---

## 규칙

BD roster의 규칙을 승계한다.

- **이름을 지우지 않는다.** 태그만 바꾼다.
- 한 사람이 여러 곳에 중복 등장할 수 있다.
- 소속은 이동이 잦다. **증류 단계에서는 소속이 아니라 논문 목록으로 확정한다.**
- `[지정]` = 사용자가 직접 지목한 사람 (BD roster 표기 승계).

**이 문서에만 있는 규칙 — 가장 중요하다:**

> **가치 주장을 쓰지 않는다. 근거의 위치만 쓴다.**
>
> 금지: *"이 사람은 최소모형이 아니면 시시하다고 본다."*
> 허용: *"가치 조건의 원전 후보 — RMP 85 (2013) §VIII Outlook."*

이유 둘. ① 그 문장은 근거 없는 귀속이고 실명 연구자에게 붙으면 명예의 문제가 된다 (README §7). ② 페르소나 계약 §4의 **"새 지식 주장 금지"** 를 명단이 먼저 위반하면 아래 단계 전체가 오염된다.

**확인 상태 표기:** `✔` = BD roster에 이미 실려 있어 사용자가 확인한 문헌 · `?` = **이 세션에서 제시했고 미확인.** Phase 1에서 DOI로 확정한다.

---

## 태그 — BD 태그를 재사용하지 않는다

`Q-003`의 잠정 답이다. BD의 `distill`/`index`/`coverage`는 **방법론 원전 여부**로 배정됐고(`I-096`), 가치 관점의 배정 기준은 다르다(`T-013`). **같은 사람이 방법 원전이면서 가치 관점의 증류 대상은 아닐 수 있다.**

| 태그 | 용도 | 규모 |
|---|---|---|
| `pair` | Phase 1의 **의견 갈리는 쌍** 후보 | 2~6 |
| `distill` | 가치 조건 증류 대상 | 미정 (`Q-004`) |
| `index` | 검색 인덱스에만. 저자 필터로 소환 | 나머지 |
| `ground-truth` | **본인에게 물어볼 수 있는 사람** | 1 |

> **`ground-truth`가 1명인 것이 `C-003`의 전부다.** 가치 페르소나에는 정답지가 없고, 예외는 물어볼 수 있는 한 사람뿐이다 (`T-015`).

---

## Phase 1 — 의견 갈리는 쌍 후보

**1개가 아니라 쌍이 필요한 이유:** 철학 ⑤(상충이 산출물)와 `C-005`(분기 스키마)는 한 쌍이 없으면 시험할 수 없다.

| # | 분기 축 (후보) | 한쪽 | 다른쪽 | 비고 |
|---|---|---|---|---|
| **P1** | **환원성** — 액티브를 열역학적 양으로 환원할 수 있는가가 가치의 조건인가 | Brady · **Takatori** 계보 (swim pressure) | Dogic 계보 (액티브 네마틱·창발 상태) | **한쪽이 `ground-truth`다** → §태그. 쌍의 검정력이 가장 높다 |
| **P2** | **기제 vs 현상론** — 미시 기제를 규명해야 가치인가, 최소모형으로 상태도를 얻으면 되는가 | Golestanian · Anderson 계보 (phoretic 기제) | Cates · Tailleur 계보 (ABP 최소모형) | 문헌 표면에 분기가 잘 드러난다 |
| **P3** | **측정 가능성** — 재지 못하는 양을 이론적으로 정의하는 것에 가치가 있는가 | Furst · Grier 계보 (미세유변학·추적) | Cates 계보 | BD `A1` ↔ `A6`의 긴장과 같은 모양 (BD roster A6 절 각주) |

> **P1 권고.** 쌍의 한쪽이 `ground-truth`면 **증류 결과를 본인에게 대조할 수 있고**, 그러면 `C-003`을 쌍 하나에 대해서는 우회한다. P2·P3은 그 대조 경로가 없다.
> 확정은 Takatori 상의 안건 3 (`Q-004`).

---

## 액티브매터 — 이론 · 최소모형 계보

| 태그 | 이름 | 소속 | 가치 원전 후보 | 확인 |
|---|---|---|---|---|
| `ground-truth` `pair` `distill` | **Sho Takatori** `[지정]` | Stanford University | Takatori·Yan·Brady, *PRL* 113 (2014) — `A5.E8` 원전 ✔ · Takatori & Brady, *Curr. Opin. Colloid Interface Sci.* (2016) 리뷰 `?` | ✔/? |
| `pair` `distill` | John Brady `[지정]` | Caltech | Brady & Bossis, "Stokesian Dynamics", *Annu. Rev. Fluid Mech.* 20 (1988) ✔ | ✔ |
| `pair` `distill` | Michael Cates | University of Cambridge | Cates & Tailleur, "Motility-Induced Phase Separation", *Annu. Rev. Condens. Matter Phys.* 6 (2015) `?` · Tailleur & Cates, *PRL* 100 (2008) ✔ | ✔/? |
| `distill` | M. Cristina Marchetti | UC Santa Barbara | Marchetti et al., "Hydrodynamics of soft active matter", *Rev. Mod. Phys.* 85 (2013) — **§Outlook** ✔ | ✔ |
| `distill` | Hartmut Löwen | Universität Düsseldorf | Bechinger·di Leonardo·Löwen 외, *Rev. Mod. Phys.* 88 (2016) `?` · ten Hagen·Löwen, *JPCM* 23 (2011) ✔ | ✔/? |
| `index` | Julien Tailleur | MIT | ✔ (Cates와 짝) | ✔ |
| `index` | Sriram Ramaswamy | Indian Institute of Science, Bangalore | Marchetti RMP 공저 ✔ | ✔ |
| `index` | Ramin Golestanian | MPI-DS Göttingen | Golestanian·Liverpool·Ajdari (2005, 2007) ✔ | ✔ |
| `index` | Thomas Speck | Universität Düsseldorf | — | — |
| `index` | Étienne Fodor | University of Luxembourg | Fodor et al. (2016) ✔ | ✔ |
| `index` | Cesare Nardini | CEA Saclay | — | — |
| `index` | Christina Kurzthaler | MPI-PKS, Dresden | — | — |
| `index` | Udo Seifert | Universität Stuttgart | 확률열역학 — 가치 조건이 방법 조건과 겹칠 위험 (`Q-003`) | ✔ |

---

## 액티브매터 — 실험 · 창발 계보

| 태그 | 이름 | 소속 | 가치 원전 후보 | 확인 |
|---|---|---|---|---|
| `pair` `distill` | **Zvonimir Dogic** `[지정]` | UC Santa Barbara | Needleman & Dogic, *Nat. Rev. Mater.* 2 (2017) `?` — 리뷰이므로 Outlook 있을 가능성 높음 | ? |
| `distill` | Clemens Bechinger | Universität Konstanz | *Rev. Mod. Phys.* 88 (2016) 제1저자 `?` | ? |
| `distill` | Steve Granick | UMass Amherst | "Brownian yet non-Gaussian" ✔ · BD `A1`·`A10` 걸침 | ✔ |
| `index` | Jérémie Palacci | IST Austria | Palacci et al., *PRL* 105 (2010) ✔ | ✔ |
| `index` | Denis Bartolo | ENS de Lyon | BD `A1`·`A6` 걸침 ✔ | ✔ |
| `index` | Nikta Fakhri | MIT | — | — |
| `index` | Peer Fischer | Universität Heidelberg / MPI Stuttgart | ✔ | ✔ |
| `index` | Ayusman Sen | Penn State University | ✔ | ✔ |
| `index` | Julia Yeomans | University of Oxford | Doostmohammadi 외, "Active nematics", *Nat. Commun.* 9 (2018) `?` | ? |
| `index` | Sujit Datta `[지정]` | Caltech | BD `A10` `distill` ✔ | ✔ |

---

## 소프트매터 · 콜로이드 · 계면

| 태그 | 이름 | 소속 | 가치 원전 후보 | 확인 |
|---|---|---|---|---|
| `pair` `distill` | Eric Furst `[지정]` | University of Delaware | Furst & Squires, *Microrheology* (Oxford, 2017) ✔ — **텍스트북이라 Outlook이 약할 것** | ✔ |
| `pair` `distill` | David Grier `[지정]` | New York University | Crocker & Grier (1996) ✔ | ✔ |
| `distill` | Bum Jun Park `[지정]` | 경희대학교 | BD `A2` `distill` ✔ | ✔ |
| `distill` | Jan Vermant | ETH Zürich | BD `A2` `distill` ✔ | ✔ |
| `distill` | Kathleen Stebe | University of Pennsylvania | BD `A2` `distill` ✔ | ✔ |
| `distill` | Sharon Glotzer `[지정]` | University of Michigan | BD `A5`·`A9` 걸침 ✔ | ✔ |
| `index` | Patrick Doyle `[지정]` | MIT | 사용자가 *"잘 모르겠는 분야"*로 넣은 사람 (BD roster) ✔ | ✔ |
| `index` | Eric Weeks | Emory University | ✔ | ✔ |
| `index` | Wilson Poon | University of Edinburgh | ✔ | ✔ |
| `index` | Todd Squires | UC Santa Barbara | BD `A1`·`A3`·`A10` 걸침 ✔ | ✔ |
| `index` | L. Gary Leal `[지정]` | UC Santa Barbara | ✔ | ✔ |
| `index` | Eric Shaqfeh `[지정]` | Stanford University | ✔ | ✔ |
| `index` | Frank MacKintosh `[지정]` | Rice University | BD `A6` `distill` ✔ | ✔ |
| `index` | Daan Frenkel | University of Cambridge | ✔ | ✔ |
| `index` | Marjolein Dijkstra | Utrecht University | ✔ | ✔ |
| `index` | Vinothan Manoharan | Harvard University | BD에서 축 미배정 — *"실험⇄시뮬 정량 대조"* ✔ | ✔ |

---

## 가치 원전으로서 특별한 것 — 로드맵 리뷰

`T-012`가 가치의 원전을 **리뷰의 Outlook 절**로 지목했다. 그렇다면 **로드맵 형식 리뷰가 최상급 진입점**이다 — 여러 저자의 Outlook을 한 편에 모아 놓은 것이기 때문이다.

| 문헌 | 왜 특별한가 | 확인 |
|---|---|---|
| Gompper 외, *The 2020 motile active matter roadmap*, *J. Phys. Condens. Matter* 32 (2020) | **수십 명의 Outlook이 절 단위로 분리되어 실려 있다.** 저자별 가치 조건 추출에 구조가 이미 맞다 | `?` — 최신판 존재 여부도 함께 확인 |
| Marchetti 외, *Rev. Mod. Phys.* 85 (2013) | 액티브 매터 10년치의 압축 (BD `I-068`의 표현) + Outlook | ✔ |

> **이 표가 Phase 1의 첫 착수 대상이다.** 인명에서 시작하지 않는다 — BD `I-068`이 축 페르소나에서 이미 확인한 것과 같은 이유로, 가치 페르소나도 **문헌에서 시작한다.**

---

## 미배정 · 미결

- **`distill` 배정은 전부 초안이다.** `T-013` 절차(가치 조건 → 원전 → 정합)를 한 번도 돌리지 않았다. 현재 배정은 **BD 태그와 계보 인상에 의한 대용품**이다.
- **`Q-003` 미해소** — 위 태그축이 BD 태그와 독립인지, 아니면 실제로는 상관이 높은지 데이터가 없다. Seifert 행이 그 위험의 실례다 (방법 원전이자 가치 관점 후보).
- **`Q-004` 미해소** — `distill`이 현재 15명. BD가 10축으로 이미 많다고 지적받았고(`I-151`) 이건 그보다 많다.
- **`?` 표시 문헌 전부 미확인.** DOI 확정이 Phase 1의 첫 작업이며, **이 세션에서 제시한 리뷰 목록을 근거로 설계를 진행하지 않는다.**
- **Furst 행의 각주가 `T-012`의 반례 후보다** — 텍스트북(*Microrheology*)은 방법의 정전이지만 Outlook이 약하다. 즉 **방법 원전이 잘 갖춰진 사람이 오히려 가치 원전이 부족할 수 있다.** `T-012`가 예측하는 것과 정합하지만, 그러면 `distill` 배정이 계보 인상에 의존하게 된다.
