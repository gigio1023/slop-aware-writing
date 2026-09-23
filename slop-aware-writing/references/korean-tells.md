# Korean Sentence-Level Patterns (한국어 문장 단위 패턴)

Load this evidence ledger only when a Korean-specific slop candidate survives the common diagnosis. It is not a Korean grammar syllabus or a required sentence-by-sentence scan. Use the model's ordinary Korean fluency for an obvious local correction, then use only the relevant pattern family here to test whether a repeated form is a slop defect, valid Korean, or the writer's voice.

Pattern IDs stay aligned with upstream `epoko77-ai/im-not-ai` `humanize-korean`. This file tracks upstream `main`, not its releases. The rule changes that upstream labels v2.4 to v2.7 exist only on untagged `main`; the latest releases, v2.3.1 and v2.3.2 (both 2026-08-18), changed no rules, and v2.3.2 moved the skill to `skills/humanize-korean/`. Inspected 2026-09-23 at `main` `fe02c9c` (committed 2026-09-22); the previous check was 2026-07-31 at `53e24e8`. When the two upstream files disagree, follow `ai-tell-taxonomy.md`, which upstream names as its source of truth; `empirical-validation.md` still limits A-16 to translation, for example. Quarterly maintenance: diff upstream `skills/humanize-korean/references/ai-tell-taxonomy.md` and `skills/humanize-korean/references/empirical-validation.md` on `main` against this file and carry over only ID-level changes.

Every rule carries an evidence ledger tag:

- `[AI]` group-level difference measured in an inspectable external study; never proof from one span or one document
- `[self]` upstream self-study whose texts are not public, so its figures cannot be reproduced
- `[KO]` Korean style or translation-ese evidence. Kim Jeong-woo's ["The Reality of Translationese in Modern Korean"](https://www.korean.go.kr/nkview/nklife/2012_1/22_0104.pdf) and Kim Sun-young's ["Translationese Sentences in English-Korean Translation"](https://www.korean.go.kr/nkview/nklife/2012_1/22_0105.pdf) document recurring translation patterns and context-sensitive alternatives; they do not establish universal bans or AI authorship
- `[obs]` observation-only diagnostic; never a rewrite instruction

Severity is review order, not a quality score: S1 = check first; one occurrence may merit a style review but never an authorship inference. S2 = fix when repeated (3+ or clustered); S3 = adjust only when stacked with other problems. Never traverse every ID merely because the text is Korean, and never grade a document by pattern counts or change ratio.

Upstream's v2.3 self-study compared 60 LLM documents with 60 human documents. The topics were not paired, and the human side consisted of edited prose published before 2022. The public repository records the method and results but does not include the reproduction corpus or scripts. Upstream's later measurements (2026-08-23 to 2026-09-06) added 24 topic-matched pairs, a per-model split of 60 human and 60 AI texts, a task-matched control, and a preliminary pronoun measurement; for these the repository publishes aggregate counts and a calibration script, still without the texts. Some of them reversed earlier readings: the H-1 and H-3 excess came from one model, and the missing direct quotations came from the prompts. Treat every figure as bounded evidence for the sampled models, genres, and tasks, dated to the measurement that produced it, not as a universal human/AI rate.

## Contents

- [Do-NOT list](#do-not-list) · [Measured priorities](#measured-priorities)
- [A 번역투](#a-번역투-s1s2) · [B 영어 인용](#b-영어-인용-s2) · [C 구조](#c-구조-패턴) · [D 관용구](#d-ai-관용구-s1s2) · [E 리듬](#e-리듬-s2) · [F 수식](#f-수식-중복-s2) · [G hedging](#g-hedging-s2) · [H 접속사](#h-접속사-s2) · [I 형식명사](#i-형식명사-s1s2)
- [Observation-only diagnostics](#observation-only-diagnostics)
- [Rewrite examples](#rewrite-examples) · [Self-check](#self-check)

## Do-NOT list

Never touch: code blocks, commands, file paths, URLs, API fields, environment variables, numbers, dates, versions, direct quotations, standard English acronyms (`HTTP`, `JSON`, `API`, `LLM`, `SDK`, `MCP`, `GPU`), proper nouns, product and model names. House-style rules (em-dash prohibition, workplace slang) live in `profiles.md`, not here.

## Measured priorities

Check these four early. The tags and limits determine how far each finding can travel.

| ID | Pattern | Evidence |
|---|---|---|
| C-8 | 부정 대구 "A가 아니라 B", "A인가 B인가" | `[self]` upstream reports 9.2× vs published prose, 18× vs blogs, G²=41.7 across 3 model families, and 11.8× in its 2026-08-29 task-matched control. Use only as a bounded review priority and apply the keep test below. |
| C-11 | 연결어미(-고/-며/-지만/-면서/-아서/-어서) 뒤 쉼표 | `[AI]` KatFish essay-level group rate: human 4.10% vs LLM 19.83%. This is not a single-span threshold. Under the Korean style baseline, remove an unnecessary comma but preserve quoted text and meaning-bearing punctuation. The 94.88% AUC belongs to the complete punctuation feature set. `[self]` Upstream saw revision itself add these commas (2026-08-30), so an edited sentence must not end up with more of them than the original. |
| E-5/C-12 | 문장당 쉼표 과다 | `[self]` upstream reports AI 1.5× (G²=25.5). Treat repetition as a review cue; split a long clause only when meaning survives. |
| E-1' | 장문 결핍 (100자+ 문장 부재) | `[self]` upstream reports an 11× deficit (G²=60.9). If rhythm is genuinely monotonous, join adjacent sentences without adding content. |

C-8 판정 테스트: 부정절을 지웠을 때 주장이 그대로 남으면 수사적 대구다 — 지운다. 부정절을 지우면 무엇을 바로잡는 말인지 사라지면 재정의 문장이다 — 보존한다("X는 형식이 아니라 정책이다"처럼 기존 통념을 정정하는 진술). 측정 근거는 논설·블로그 산문 기준이라, 정의를 다시 세우는 기술 문서에서는 같은 표면형이 정보를 나른다. 같은 틀이 반복돼도 각각 실제 오해를 바로잡는다면 보존한다. 반복 때문에 요점이 가려질 때만 해당 문장을 고친다. 고치는 과정에서 다른 문장에 대구를 새로 만들지 않는다. upstream의 2026-09-06 측정에서 수정본 17편은 대구 총량이 줄었지만, 원래 대구가 없던 2편의 결말과 재정의 문장에 새 대구가 생겼다. A-24의 "더 이상 A가 아니라 B"도 같은 자리에서 생긴다.

## A. 번역투 (S1~S2)

All `[KO]` unless noted. They are contextual revision cues, not a promise that applying every row improves every Korean document.

| ID | Pattern | Sev | Fix |
|---|---|---|---|
| A-1 | "~에 대해(서)" | S2 | `[KO][self]` **기본 보존**. 한 문단에 3회 이상 몰려 관계를 흐릴 때만 일부를 목적격으로 직결: "X에 대해 설명" → "X를 설명". upstream의 2026-08-29 형태소 측정에서 사람이 LLM보다 3배 더 쓴다(사람 4.39 vs LLM 1.46/1000어절) — AI-tell 아님 |
| A-2 | "~를 통해" 남발 | S2 | `[KO][self]` **맥락 판정**: 수단이나 경로를 설명하는 데 필요하면 반복돼도 보존. 관계를 흐리는 군더더기일 때만 고친다. 상류 표본에서 사람이 LLM보다 2배 더 쓴다 — AI-tell 아님 |
| A-3 | "~에 있어(서)" | S1 | "~에서", "~을 볼 때" |
| A-7 | "가지고 있다", have/make/take 직역 | S1 | 형용사·동사 환원: "강점을 가지고 있다" → "강점이 있다" |
| A-8 | 이중 피동 "되어진다" | S1 | 단일 피동 또는 능동 |
| A-9 | "~에 의해" 피동 | S2 | 행위자를 주어로: "AI에 의해 생성" → "AI가 만든" |
| A-10 | "~할 수 있다" 남발 | S2 | **기본 보존**(upstream v2.4). 원문이나 확인한 근거가 이미 확정한 절차를 불필요하게 가능형으로 완곡한 경우에만 평서·명령형으로 바꾼다. 실제 능력, 허용, 가능성, 불확실성, 필자가 고른 주장 강도는 보존. 반복을 깨려고 다른 완곡 표현으로 돌려 쓰지 않는다 |
| A-12 | "이루어지다/만들어지다" | S2 | 능동: "합의가 이루어졌다" → "합의했다" |
| A-13 | 명사 나열(조사 생략) | S2 | 조사 복원 |
| A-15 | 추상 주어 + 만능 동사("X가 Y를 보여준다") | S2 | 행위자 주어로 환원, 인지 동사는 "~에 따르면"으로 분리 |
| A-16 | 받을 대상이 맞지 않는 대명사(그/그녀/그것/그들/이것) | S1 | `[KO][self]` 번역문과 자생 한국어 산문 모두에 적용. 빈도가 아니라 대명사마다 선행 후보 수로 판정한다. 아래 A-16 판정 참조 |
| A-18 | 긴 좌향 관형절 중첩 | S2 | 문장 분리 또는 후치 동격절 |
| A-19 | 이중 조사("~에서의/~으로의") | S2 | 절로 풀기 |
| A-20 | 피동 진행 "~되고 있다/~지고 있다" 연쇄 | S2 | `[self]` 한 문단에 3회 이상 몰릴 때만 일부를 고친다. 능동형이 있으면 능동으로("증가되고 있다" → "늘고 있다"). 진행 중이라는 뜻은 유지하고 고립된 사용은 보존. upstream 2026-08-29 측정: 사람 1.38 vs AI 2.87~3.44/1000어절, 세 모델 모두 초과. 능동 진행 "~하고 있다"는 격차 없음 |
| A-21 | 범위 상승 "단순한 X를 넘어 Y" | S2 | `[self]` 넘어-구를 걷고 Y를 직접 쓴다. X가 필요한 정보면 남기되 격을 올리는 틀만 걷는다. upstream 2026-08-29 측정: 사람 60편 0건 vs AI 12건/12편(주로 Fable·GPT) |
| A-22 | 평가 술어 얹기 "~은 명확하다/분명하다" | S2 | `[self]` 논증 없이 확신만 얹은 문장이면 평가 술어를 걷고 명제를 단언한다: "정책이 실패했다는 것은 명확하다" → "정책은 실패했다". 원문의 확신이 실제로 강하면 "분명히"로 보존하고, 앞에서 논증한 결론을 맺는 자리면 유지. 무엇이 분명한지 비어 있으면 원문이 주는 내용으로만 채운다. "명확히 하다", "입장을 분명히 하다"는 대상 아님. upstream v2.7 규칙이며 사람 글과의 빈도 대조는 없다 |
| A-23 | 기반 마련 공식 "발판·토대를 마련하다", "지평을 열다" | S2 | `[self]` 결말부에서 구체 경로 없이 전망을 봉합할 때만. 그 조치가 실제로 무엇을 가능하게 하는지 원문에 있으면 그것으로 쓰고, 없으면 은유만 평서로 낮춘다("발판을 마련한다" → "여건이 갖춰진다"). 경로를 지어내지 않는다. 과거 사실("딥러닝의 토대를 놓은"), 인용, "기반을 마련", "길을 열다"는 대상 아님. upstream 표본에서 AI 직접 생성문은 0건이라 판별 신호가 아니라 막연한 전망을 고치는 문체 기준이다 |
| A-24 | "더 이상 ~ 않다/아니다" | S2 | `[self]` 한 문서에 2회 이상이거나 결말의 재정의 문장일 때만 "이제"나 변화를 서술하는 동사로 편다. 부정 명제를 긍정 단언으로 바꾸지 않는다("핵심이 아니다"를 "핵심은 X다"로 옮기면 원문에 없는 X가 생긴다). 앞 문장이 이전 상태를 밝히고 그 종료를 말하는 자리, 인용 발언, 문서 1회는 보존. upstream 표본에서 AI 직접 생성문과 인간 번역문의 빈도가 비슷해(0.16 vs 0.17) 판별 신호는 아니며, 수정본에 "더 이상 A가 아니라 B"를 새로 만드는 주입이 관측됐다 |

A-16 판정: 대명사마다 직전 두 문장에서 그 대명사가 받을 수 있는 명사구 후보를 센다. 후보가 없으면 가리키는 대상을 원문에서 확정할 수 있을 때만 명사구를 복원하고, 확정할 수 없으면 고치지 않고 표시만 한다. 후보가 하나면 영형이 자연스러운 자리이므로 대명사를 빼고 문장을 잇는다. 후보가 둘 이상이면 명사구로 되짚고, 다른 대명사로 바꾸지 않는다. 후보 판정이 불확실하면 그대로 두며, 대명사를 일정 비율 지운다는 목표는 두지 않는다(upstream v2.7은 이전의 "50~70% 삭제 후보" 목표를 폐기했다). 근거는 upstream의 2026-09-06 예비 측정이다(정규식과 직전 두 문장 창, 거친 명사구 근사, 사람 검수 없음). 총량은 인간 번역문이 AI 직접 생성문보다 2.5배 많았지만, 받을 대상 없이 쓴 비율은 AI가 13.6%로 인간 번역문의 2.2%보다 6배 높았다. 임계와 창 크기는 추정값이다.

A-4~A-6, A-11, A-14: 반복될 때만 같은 원리로 처리(상세는 upstream taxonomy). A-17('-들' 기계 부착)은 upstream이 hold — 탐지 보조로만.

## B. 영어 인용 (S2)

- B-1: 설명이 필요한 전문 용어는 첫 유효한 등장에 뜻을 붙이고 이후에는 선택한 기준 용어를 유지한다. 문헌과 코드의 English term이 기준이면 한국어 풀이를 덧붙인 뒤에도 English term을 사용한다. 일반 단어에 불필요한 영어를 병기하거나 같은 풀이를 반복하지 않는다. 이는 용어 일관성을 위한 편집 기준이며 AI 저자 판별 신호가 아니다.
- B-2: 인용부호 안이나 본문에 들어간 영어는 문서의 언어, 하우스 스타일, 독자의 이해를 해칠 때만 고친다. 직역 가능한 영어(`leverage`, `seamless`, `robust`)는 한국어를 검토하고 독자가 더 익숙한 업계 표준어(`pipeline`, `endpoint`, `runtime`)는 유지한다. 한 문서에서는 영/한 표기를 통일한다.

## C. 구조 패턴

- C-1 기계적 열거(S2): **논설·에세이 장르에서만 AI 신호**. 학술·매뉴얼·설명문의 열거는 정상 — 기본 보존.
- C-4 문단 첫 문장 요약 공식(S2): 요약이 뒤 문장을 그대로 반복해 독자의 읽기를 방해할 때만 고친다. 시작 형식에 변화를 주는 것 자체가 목적은 아니다.
- C-5 이모지(S1): 기술 문서면 전부 삭제.
- C-7 "먼저/반면/결국" 3단 공식(S2): 접속사를 줄이거나 본문에 녹인다.
- C-8, C-11: [Measured priorities](#measured-priorities) 참조.
- C-9 숫자 괄호 인덱싱 "(1)(2)(3)"(S2): 본문에 녹이거나 줄바꿈.
- C-10 콜론 부제 헤딩 "X: Y" 반복(S2): 평서 헤딩으로.

문서 구조 단위 장황함(헤딩·표 인플레이션, 자기 설명 도입부 등)은 `structure-anti-patterns.md`가 정본이다.

## D. AI 관용구 (S1~S2)

Delete-only category — **removal only, never insert** replacement clichés.

- D-1 결산 피벗("결론적으로", "정리하면", "이를 통해"): 논리를 더하지 않으면 삭제.
- D-2 "시사하는 바가 크다", "주목할 만하다": 삭제 또는 구체 결론.
- D-3 "본질적으로", "핵심적으로": 삭제. 열거 도입("크게 세 가지로") 도 삭제 후 바로 항목.
- D-4 hype 어휘(혁신적, 획기적, 강력한, 압도적): 근거가 있으면 구체 사실로, 없으면 삭제.
- D-5 의인화 추상 주어("기술이 묻는다"): 사람·기관 주어로.
- D-6 결말 공식("~할 때다"): 평서로 닫거나 삭제.
- D-8 분열문 "필요한/중요한 것은 X이다"와 "문제는/핵심은/관건은 ~이다"(S2) `[self]`: 강조 틀만 있고 정보가 없으면 주어와 서술어를 바로 잇는다: "필요한 것은 방향이다" → "방향이 필요하다". 여러 요인 가운데 하나를 실제로 가려내는 "핵심은 X다"는 보존. "필요한 것은 A가 아니라 B"처럼 C-8과 겹치면 C-8 판정도 함께 적용. upstream 2026-08-29 측정: 사람 0.09 vs AI 0.92/1000어절, 세 모델과 과업 대조에서 모두 유지.
- D-9 인과 결산 "결국 ~로 이어진다", "~에 직결된다"(S2) `[self]`: 원문이 인과 경로를 밝히면 그 경로를 쓴다. 경로가 없으면 이 결산 틀은 문서에 한 번만 남기고, 인과 주장을 지어내거나 부풀리지 않는다. 논리 결산용 "결국"이 반복되면 하나만 남기고, 결말을 다듬으면서 "결국"을 새로 넣지 않는다. upstream 측정: 사람 0.00 vs AI 0.34/1000어절, 논리 결산용 "결국"은 사람 0.34 vs AI 1.72.
- D-10 역방향 결산 "~하는 이유다"(S2) `[self]`: 도치를 풀어 순방향으로 쓴다: "…우려가 나오는 이유다" → "그래서 …우려가 나온다". "~라는 이유로"는 대상 아님. 결말을 다듬으면서 이 도치를 새로 만들지 않는다. upstream 측정: 사람 1건 vs AI 6건/6편, 세 모델 모두.
- D-11 결말부 막연한 시간어 "향후/앞으로/중장기적으로"(S2) `[self]`: 글 후반에서 시간어로 문장을 열고 시점이나 조건 없이 전망을 봉합하면, 원문에 있는 실제 시점·조건으로 바꾸거나 시간어만 지운다. 없는 시점을 지어내지 않는다. upstream 측정: 문두·후반 30% 조건에서 사람 0건 vs AI 12건/12편.
- D-12 내용 없는 반론 문패 "과제도 남아 있다", "한계도 분명하다"(S2) `[self]`: 독립 문장으로 균형만 알리고 내용은 다음 문장으로 미루면, 문패를 지우고 실제 과제를 바로 쓴다. 과제 내용을 담은 문장("안전 기준 정비도 과제로 남아 있다")은 보존. upstream 측정: 사람 0건 vs AI 8건/8편(Fable·Haiku).
- D-14 생성형 은유 겹침(S2) `[self]`: 논설·보고서에 새로 지어 얹은 개념 은유(잠식·짓누르다, 청구서·성적표, 청사진·주춧돌, 신호탄·적신호)가 겹치거나 같은 은유 어근이 문서를 관통해 세 번 이상 반복되면, 가장 효과적인 하나만 남기고 나머지는 은유가 나르는 명제를 문자 그대로 쓴다("시장을 잠식한다" → "시장 점유율을 빼앗는다"). 명제를 특정할 수 없거나 은유가 글 전체의 중심 구조면 보존. "양날의 검" 같은 굳은 관용구는 대상 아님. upstream 2026-08-29 측정: 은유 가족 합산 사람 0.34 vs AI 1.46/1000어절, 세 모델과 과업 대조에서 모두 유지. upstream의 사전 어휘 1회 발동과 감각 술어("진단은 서늘하다") 1회 교정은 필자가 고른 은유 하나를 목록만 보고 고치게 하므로 채택하지 않는다.

D-13(에세이 결말의 "어쩌면·비로소·천천히")은 에세이 장르에만 해당하고 개별 어휘가 모델에 치우쳐 있어, 필자의 목소리를 해칠 위험이 커서 싣지 않는다.

## E. 리듬 (S2)

- E-1' 장문 결핍: [Measured priorities](#measured-priorities). 인접한 짧은 문장을 연결어미("-며/-고/-는데")로 잇는다. 내용을 지어내지 않는다.
- E-2 동일 종결어미 연속 + "~한다" 편중 `[self]` (upstream: 1.8×, G²=9.5): 같은 어미의 반복 자체는 수정 사유가 아니다. 논리 관계나 의미가 가려질 때만 필요한 연결을 복구하며, 변화를 주기 위해 명사 종결이나 단문을 삽입하지 않는다. "~고 있다"는 단순 시제로 환원 가능하면 환원.
- E-3 문단 길이 균일: 각 문단의 논점과 필요한 설명량을 본다. 길이를 일부러 다르게 만들지 않는다.
- E-4 단문 일변도: 분리 때문에 논리 관계가 끊겼다면 연결한다. 절차나 간결한 설명에 쓰인 단문은 보존한다.
- E-7 경어법 혼용: 한 문서 한 격식. 기존 문서가 존댓말이면 유지.

## F. 수식 중복 (S2)

정도부사("매우/정말"), 동의어 이중 수식("중요하고 핵심적인"), "-성/-적/-화" 누적, "~적 N" 추상 체인 — 하나만 남기거나 동사·형용사로 푼다.

F-7 범용 정책동사 수렴 `[self]`: 행위를 서술할 자리마다 확대·강화·개선·확보·마련·구축과 추상 목적어의 "설계"가 반복되면, 원문이나 확인한 근거가 구체 행위를 알려 줄 때만 그 행위로 푼다. 원문이 무엇을 넓히는지 밝히면 "지원을 확대해야" → "지원 대상을 넓혀야". 구체 행위를 알 수 없으면 보존하고, 풀면서 "~해야 한다"를 늘리지 않는다. 실제 설계·구조·기준을 가리키는 기술 용례는 대상 아님. upstream 측정: 아홉 동사 합산 사람 9.3 vs AI 31.3/1만 자, 세 모델 모두 초과.

## G. Hedging (S2)

"~것이다" 미래 단정과 "~로 보인다", "~인 것으로 판단된다" 같은 추정 종결(G-1)은 **기본 보존**한다. 유보를 단정으로 바꾸면 필자가 고른 주장 강도가 바뀐다(upstream v2.4). 명세·정의 섹션에서 원문이나 확인한 근거가 이미 확정한 사실을 추정형으로 적었을 때만 단언으로 바꾸고, 반복을 깨려고 다른 추정 표현으로 돌려 쓰지 않는다. 이중·삼중 완곡(G-2)은 하나만 남기되 원문과 같은 극성과 확신도를 지킨다. 부정이 낀 완곡은 줄이면 긍정과 부정이 뒤집힐 수 있으므로 극성을 확인한 뒤에만 고치고, 협상·계약 회신처럼 완곡의 겹침이 곧 입장의 강도인 글은 보존한다. 안전 균형 어휘(G-3, "양쪽 모두", "신중하게")는 upstream이 한국어 산문 실증 부족으로 hold했으므로 수정 근거로 쓰지 않는다. 가이드·추천 섹션의 humble 표현 ("참고해보시면 좋을 것 같습니다")은 사람 글의 특징이므로 보존한다.

### 부정문의 기능

`~않는다` 자체는 결함이 아니다. 실제 부정, 금지, 미지원 범위, 불확실성을 전달하면 보존한다. 문서가 무엇을 하지 않는지 반복해서 선언하거나 독자가 제기하지 않은 반론에 답할 때는 그 설명이 필요한지 판단한다. 필요한 사실만 직접 쓰되 부정의 의미를 긍정으로 뒤집거나 조건을 삭제하지 않는다. 이 판단은 편집 기준이며 빈도나 저자 판별에 관한 주장이 아니다.

독립적인 합성 예: “이 문서는 모든 설정을 나열하지 않는다. 연결 제한을 설명한다.”에서 설정 목록이 독자의 요구가 아니라면 첫 문장을 덜어낼 수 있다. “이 설정에서는 자동 재시도를 하지 않는다”는 실제 동작을 설명하므로 보존한다.

## H. 접속사 (S2)

문두 접속사(H-1, "또한/따라서/즉/나아가")와 메타 진입(H-3, "이는/이 점에서")은 **한 문단에 3회 이상 몰릴 때만** 손대고(S2), 그때도 그 문단에서 논리를 더하지 않는 것 일부만 덜어낸다. 문서 전체를 훑어 일괄 삭제하지 않는다. 메타 진입은 앞 문장을 받아 논지를 잇는 정상적인 한국어 담화 장치이므로 기본 보존한다. `[self]` upstream의 2026-08-29 측정(사람 60편 vs AI 60편, 세 모델)에서 두 표지의 초과는 한 모델(Haiku 4.5)에서만 나왔고, 다른 두 모델은 사람 글과 구별되지 않았다. 메타 진입은 사람 글 60편 중 8편에도 있었고, 같은 날 과업 대조에서는 AI가 두 표지를 사람보다 적게 썼다. upstream은 2026-09-22 두 규칙을 fast 경로 룰북에서 뺐다.

"하지만/그러나"가 반복되면 실제 대조 관계를 점검하고, 없는 대조를 연출하는 표현만 삭제(S2).

## I. 형식명사 (S1~S2)

- I-1 "~것이다" 결말 `[KO][self]`: **맥락 판정** — 의미 없이 단정을 반복할 때만 간결하게 고치며, 필요한 설명·예측·인용은 보존. 상류 표본에서 사람이 LLM보다 2배 더 쓴다(LLM 20.4 vs 사람 43.0/1000문장) — AI-tell 아님.
- I-2 "X는 ~라는 점에 있다"(S2): "X는 ~다" 직설로.
- I-4 권고형 결말 기계 반복(S2): 필자의 권고와 의무 조건은 당위 표지째 보존한다. 병합하거나 지우거나 단정·조건·추측으로 바꾸면 요구한 일을 이미 일어난 일로 만든다(upstream v2.4). 사실을 설명하는 문장에 당위형이 잘못 붙은 경우만 평서로.
- I-5 "~이 필요하다"(주체 모호, S2): 주어와 동사로 구체화하되 문장마다 "~해야 한다"로 끝내지 않는다. upstream v2.5 측정에서 이 처방이 당위 표지를 3건에서 8건으로 늘렸다.
- I-7 무주체 판정 "~다는 분석이다/평가다"(S2) `[self]`: 앞뒤 문장에 분석 주체가 있으면 정상적인 기사 문법이므로 보존. 주체가 없으면 출처를 지어내지 않는다. 필자 자신의 판단임이 분명하면 직접 서술로 쓰고, 알 수 없으면 출처 확인이 필요하다고 표시한다(`anti-slop-core.md`의 Unsupported authority 참조). upstream 측정: 사람 0건 vs AI 5건/5편, 모두 취재·인용 과업에서만.

## Observation-only diagnostics

`[obs]` marks look-closer cues only. Report the wording problem, never infer authorship or fabricate a fix:

- `[self][obs]` 괄호 결핍 (upstream: G²=69.5) — 장식 괄호를 삽입하지 않는다. 인용을 요구하지 않은 같은 프롬프트 표본에서 나온 수치라 과업 편향 여부는 아직 검정되지 않았다
- `[self][obs]` 과거형 회피 (잠정, 장르 교란 가능)
- `[AI][obs]` 띄어쓰기 특징군 (KatFishNet 에세이 평균 AUC 79.51%) — 단일 규칙의 성능이 아니며 일부러 틀린 띄어쓰기를 추가하지 않는다

직접 인용 결핍(v2.3 표본: LLM 0.0 vs 인간 8.7/1k, G²=96.4)은 프롬프트의 산물이라 이 목록에서 뺐다. upstream의 2026-08-29 과업 대조에서 인용을 요구한 과업으로 만든 AI 글은 따옴표를 1000어절당 26.89회 써 사람 글(11.36회)보다 많았다.

## Rewrite examples

```diff
- 데이터를 정제하고, 모델을 학습시킨 다음, 결과를 검증합니다.        (C-11)
+ 데이터를 정제하고 모델을 학습시킨 다음 결과를 검증합니다.

- 경쟁력을 가지고 있다                                               (A-7)
+ 경쟁력이 있다

- **결론적으로**, ADK는 도구 루프를 자동화합니다.                     (D-1)
+ ADK는 도구 루프를 자동화합니다.
```

## Self-check

After editing: (1) 불변 정보 보존 — 명령어·경로·수치·인용·조건을 원문과 대조, (2) 각 수정의 의미 보존을 diff로 입증, (3) 장르·격식 유지, (4) 저장소 용어 일관성, (5) 새 사실·비유·예시를 추가하지 않았는지, (6) AI slop 수정이 일반 맞춤법 검사로 번지지 않았는지, (7) 수정이 원문에 없던 대구(C-8, A-24), 연결어미 뒤 쉼표(C-11), 결산 "결국"이나 "~하는 이유다"(D-9, D-10)를 새로 만들지 않았는지. 위반한 수정은 되돌린다.
