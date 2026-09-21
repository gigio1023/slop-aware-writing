# Structural Verbosity Anti-Patterns

Document-structure-level failures that delay, fragment, or obscure an explanation. Report or repair a pattern only when it harms the page in context — these are diagnoses, not lint absolutes. Examples are English and Korean, but the reader-level patterns apply across languages when the same defect exists.

## Contents

- [Deletion-first patterns](#deletion-first-patterns) (when deletion alone repairs the passage)
- [Structure inflation](#structure-inflation)
- [Information duplication](#information-duplication)
- [Sentence-level padding](#sentence-level-padding)
- [Vocabulary escapes](#vocabulary-escapes)
- [Preservation rules](#preservation-rules) (what NOT to remove)
- [Application order](#application-order)

## Deletion-first patterns

**Self-describing intro.** A section opens with "this section discusses X" / "이 섹션에서는 X를 설명합니다". The heading already does that job — delete the line. Distinguish from a WHY sentence (see Preservation rules).

**Obvious command caption.** "다음 명령어로 의존성을 설치합니다" above `uv sync`. Caption commands only when non-obvious. Keep test: does the caption carry why, when, scope, or audience — something the command line itself does not show? Then it stays.

**Conclusion echo.** The last paragraph restates what the body said, prefixed with "정리하면 / In summary". Delete or fold into the body sentence.

**Meta prose.** "It is worth noting that", "이는 ~라는 점에서" delays the claim. State the instruction or decision directly.

## Structure inflation

**Heading inflation.** Headings shatter prose when they do not help the reader scan, navigate, or understand hierarchy. Merge a heading whose content flows more clearly as part of the surrounding section; keep a short headed block when it supports lookup, warnings, or a consistent reference shape.

**Table inflation.** A table whose rows or columns carry no real comparison or lookup structure. Use prose or a numbered list when the grid does not help the reader scan, compare, or map fields. A small table may still be the clearest form; row and column counts are not the test.

**Decorative structure.** Tables, callouts, diagrams, or nested lists that repeat simple prose without clarifying a comparison, sequence, or hierarchy.

**Bullet as paragraph.** One bullet holds several independent facts and links. Split parallel facts or return to prose when the ideas form an argument.

**Option catalog.** Every flag and environment variable interrupts the main path. Keep the options the task requires and move exhaustive lookup material to a reference section or page. A reference page may legitimately be complete.

**Numbered-index prose.** "(1) clone (2) rename (3) 구현 순으로" inside a sentence. Fold into prose or use a real list.

## Information duplication

**Restate-in-different-form.** The same facts appear once in prose and again in a table or list. Keep the clearest single form; a one-line lead-in may stay.

**Buried outcome.** The current command, decision, or supported behavior appears only after history or meta commentary. Lead with the outcome.

**False single source.** Essential context disappears from a standalone guide in favor of a link. Deduplicate volatile detail, not the information the page needs to do its job.

## Sentence-level padding

**Future/possibility padding.** "~할 수 있습니다 / will allow you to" chained onto plain facts. State the fact directly in the tense and aspect the timeline, genre, and language require; reserve modality for genuine possibility. Removing "may", "optional", "when", units, or version limits to shorten a sentence creates a false guarantee — that is a bug, not a fix.

**Scope-clarification noise.** "X는 Y가 아니다", "Z와는 별개다" answering questions no reader asked. Delete, or restate positively ("X가 다룬다"). Keep test: would the intended reader plausibly ask this, or does an instruction or boundary depend on the answer? Then it is a real boundary, not noise — declared scope limits ("NOT for X, Y") are a convention, not negative listing.

**Indirect definition.** "X는 A를 입력으로 받아 B하고 C를 측정하는 D다" can hide the defining relation inside inputs, operations, and outputs. Split or reorder only when the reader cannot recover what X is and what distinguishes it. For "핵심은 X가 아니다" openers, drop the negation only when it carries no correction or scope boundary. Preserve a meaning-bearing redefinition; apply the C-8 keep test in `korean-tells.md`.

**Governance-speak leakage.** "단일 source", "권위 문서", "본문 정의는 [doc] 단일 source" — document-architecture vocabulary leaking into prose. Readers need "어디를 보면 되는가"만: "[doc] 참고."

**Redundant emphasis labels.** "권위 출처:", "핵심:", "Note:", "Important:" prefixes stacked on statements that stand alone. Keep labels that distinguish a real warning, status, or lookup category; remove labels that add only emphasis.

**Slash stacking.** `A / B / C` chains and `X + Y` composite headings blur relationships. Prose uses commas and conjunctions; headings split per topic. Standard pairs (`input/output`, `pass/fail`) are fine.

## Vocabulary escapes

**Abstract escape.** `custom`, `various`, `다양한`, `여러`, `관련된`, `등`, `etc.` standing in for real names. Ask what the actual name is; use it, or cut the item. "추론 코드 (LangGraph, custom)" → "Agent 구현체 (Vanilla Python, LangGraph)".

## Preservation rules

Do not remove these while cleaning:

- **WHY sentences.** A one-line purpose/배경 that adds what the heading cannot ("왜 이 섹션이 존재하는가") is an anchor, not a self-describing intro. Test: remove it and see whether meaning shrinks.
- **Conversational tone in guide/recommendation sections.** "참고해보시면 좋을 것 같습니다" is more human than "[doc] 참고." in a guide. Tone matches content type: 정의/명세 = 단정, 추천/안내 = conversational. Apply hedging cleanup to spec sections only.
- **Intentional duplication.** Standalone runbooks, offline guides, and safety-critical procedures legitimately repeat context.
- **Functional repetition.** A spec restating an obligation per clause, or a contrast that corrects a common misconception, is doing work.

## Application order

Start with the useful passage the reader needs: what should become understandable, and which supplied facts establish it? Use [the worked reconstruction](revision-example.md) when the draft contains ingredients without an explanation.

1. Identify the dominant reader problem and preserve the facts, conditions, and voice needed to solve it.
2. Give the retained material a useful relationship: an example and its mechanism, a comparison and its deciding condition, or an action and its observable result. Use only supported relationships.
3. Remove or merge framing and repetition whose function the revised passage already performs. A local filler sentence may need deletion alone; a fragmented explanation may need reconnection or reordering.
4. Choose the form that exposes that relationship. Values may belong in a table while their meaning belongs in prose. Keep both when they contribute different information.
5. Re-read the result for understanding. Confirm that it answers the actual reader question without the drafting conversation and preserves the relevant WHY sentences, boundaries, register, and uncertainty.

Stop when the passage does its job. Shorter text, fewer headings, or fewer negative sentences are not independent completion criteria.
