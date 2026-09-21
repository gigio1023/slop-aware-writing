# Complete Explanation Examples

Use for Korean passages whose words are individually familiar but whose relations are hard to recover. All cases here are independently synthetic. The English guidance explains the editorial decision; the Korean examples demonstrate the requested language. These are semantic repairs, not a document template or an instruction to lengthen every answer.

## From noun strings to a recoverable mechanism

**Supplied meaning:** a client receives an upload response after durable enqueue. A worker updates a separate search index later. ID lookup can read the stored file before keyword search can find it.

**Compressed draft:** “업로드 완료 후 검색 미반영 가능. 저장과 인덱스 분리, worker 후속 처리.”

**Grammatical but thin:** “업로드가 완료되어도 검색에 반영되지 않을 수 있다. 저장과 인덱스가 분리되어 있고 worker가 나중에 처리한다.”

The second version adds endings, but “처리한다” still leaves the operation and affected object vague. A reader can miss what the upload response actually establishes.

**Complete explanation:**

> 업로드 응답은 파일 저장과 indexing job의 durable enqueue가 끝났다는 뜻이다. ID lookup은 저장된 파일을 바로 읽지만, keyword search는 worker가 나중에 갱신하는 별도 index를 조회한다. 그래서 업로드가 성공한 직후에는 ID로 파일을 조회할 수 있어도 keyword search 결과에는 아직 나타나지 않을 수 있다.

The clauses retain one file as their referent and explain which operation reads which store. The final sentence derives the visible difference from those supplied relations. No missing timing estimate or failure cause is invented. For an expert status table, a shorter label could be sufficient; this repair is for explanatory prose.

## Terms and a calculation in the same explanation

**Supplied meaning:** the arithmetic mean of 6 and 10 is 8; both values carry equal weight. The intended reader is learning the term.

**Detached wording:** “Arithmetic mean, 동일 가중치, 합 나누기 관측 수. 결과 8.”

**Complete explanation:**

> Arithmetic mean(산술평균)은 관측값을 더한 뒤 관측값의 개수로 나눈 값이다. 관측값이 6과 10이면 `(6 + 10) / 2 = 8`이다. 이 계산에서 두 관측값의 가중치는 각각 1/2이다.

The term, operation, operands, and result are linked by ordinary Korean syntax. The gloss helps at first use; the established English term remains the same afterward. In a shorter passage, the last sentence can be omitted if equal weighting is already understood. A separate policy paragraph announcing that English terminology will be used adds nothing to this relation.

## Negation with an identifiable scope

**Supplied meaning:** after a timeout, this client makes no automatic retry; the caller must submit a new request to try again.

**Ambiguous draft:** “실패 이후 진행하지 않는다. 필요하면 다시 처리한다.”

**Complete explanation:**

> 이 client는 timeout이 발생하면 자동으로 재시도하지 않는다. 다시 시도하려면 호출자가 새 요청을 보내야 한다.

The negative ending carries actual behavior. The repair identifies the failure condition, responsible component, and actor for the next attempt. Replacing the passage with “호출자가 요청을 보낸다” would lose both the condition and the absence of automatic retry.

A grammatical sentence such as “이 문서는 모든 사례를 설명하지 않는다” has a different question: whether the document needs that scope statement. That selection belongs to the authorized writing or revision task. Korean clarity repairs meaning when it is unclear; it does not delete a clear statement just because it contains negation.

## Use the examples proportionally

Recover only relations supplied by context. A technical term may need a definition for a beginner and none for an expert. Repeating a precise noun may help when two referents compete; repeating every subject makes ordinary Korean cumbersome. Keep the reader's register and the writer's intentional phrasing. The result should express the supported thought naturally, with no extra claim added to make the prose appear complete.
