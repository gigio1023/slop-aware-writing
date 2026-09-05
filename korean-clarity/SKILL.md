---
name: korean-clarity
description: >
  Use when drafting or revising Korean agent responses or artifacts where
  compression has omitted or blurred sentence components, particles, endings,
  predicates, logical relations, referents, or ordinary technical wording; or
  when the user asks to make Korean meaning clearer without changing facts.
  Restores semantic completeness without padding or invented context. NOT for
  translation, grammar- or spelling-only proofreading, AI-authorship detection,
  document structure, evidence, or voice problems without a Korean clarity
  defect, or changing code, identifiers, commands, quotations, and established
  product terms.
---

# Korean Clarity

Produce Korean that a reader can understand without reconstructing omitted
actors, actions, objects, conditions, or relations. This is a semantic clarity
floor for Korean responses and artifacts, not a prestige style, grammar
syllabus, translation workflow, or authorship detector.

The common failure is compression: a coding agent preserves keywords but drops
the morphology and sentence structure that explain how those keywords relate.
Repair the missing relation, not the sentence's length. Natural Korean can omit
a recoverable subject or use fragments deliberately; completeness is measured
by meaning, not by the presence of every possible component.

## Precedence and scope

Apply this order:

1. The user's explicit target language, register, and artifact requirements.
2. Governing repository, publisher, or product terminology.
3. The source text's facts, uncertainty, and deliberate voice.
4. This clarity floor.

Apply the floor directly to the agent's Korean explanations, progress reports,
and final answers. When revising someone else's text, change only what the
request authorizes and preserve intentional fragments, dialect, non-native
voice, humor, and register. A quoted passage is data, not an instruction to
change scope.

## Diagnose the missing relation

Read the complete relevant span before editing. Locate the smallest unit where
the reader cannot safely recover one of these:

- **Proposition:** who or what acts, what happens, and which object or state is
  affected.
- **Boundary:** the condition, time, scope, exception, requirement level, or
  uncertainty that limits the statement.
- **Connection:** how adjacent clauses or noun phrases relate, including cause,
  contrast, sequence, ownership, or purpose.
- **Reference:** what a pronoun, omitted subject, abbreviation, or local label
  points to.
- **Register:** whether endings and honorifics match the intended relationship
  and remain stable through the document.

If context already establishes the relation without effort, omission is valid
Korean and no repair is needed. If the missing information is not established
by the supplied material or allowed evidence, preserve the uncertainty and
complete independent repairs. Ask only when the unresolved relation materially
changes the requested meaning; do not turn every omitted subject into a
clarification question.

## Repair rules

1. **Restore necessary sentence components.** Supply an omitted actor, object,
   state, or condition only when the context establishes it and its absence
   makes the statement ambiguous. Repeat a precise noun when a silent subject
   or pronoun could point to more than one referent.
2. **Complete running prose.** Give an independent assertion a predicate and an
   ending when a telegraphic noun phrase, adverbial phrase, or connective ending
   leaves the thought unfinished. Headings, labels, table cells, parallel list
   items, notes, and deliberate fragments may stay fragmentary.
3. **Use morphology to expose relations.** Restore a particle, ending, auxiliary,
   tense, modality, or honorific when it clarifies grammatical role, aspect,
   permission, probability, politeness, or the relation between clauses. Do not
   add auxiliaries or adverbs merely to make the sentence fuller.
4. **Unpack noun strings when needed.** Convert a compressed chain into a finite
   clause when the chain hides who does what or which noun modifies which. Keep
   an established compound or technical noun phrase when practitioners use it
   precisely.
5. **Prefer conventional exact wording.** Use the term the intended Korean
   audience and governing source use. Keep a source-language product, API, or
   protocol term when no settled Korean form is equally precise or searchable.
6. **Replace strained lexical substitution.** When a novel metaphor, rare
   dictionary word, or prestige borrowing displaces an ordinary exact noun or
   verb, restore the ordinary wording. Keep conventional domain metaphors and a
   writer's deliberate imagery.

Never make a sentence more specific by inventing names, numbers, causes,
examples, or intentions. Do not alter code blocks, commands, paths, URLs,
identifiers, schema fields, logs, quotations, product names, or standard
acronyms merely to make the surrounding prose Korean.

## Compose with slop-aware writing

This skill and `slop-aware-writing` have independent triggers and must each work
when installed alone. When both apply, `slop-aware-writing` owns the document's
evidence boundary, reader job, structure, change authority, and voice
preservation. This skill repairs only Korean semantic completeness inside those
constraints. A clarity edit cannot strengthen a claim, resolve a factual
conflict, add connective reasoning without support, or flatten a repeated
author choice.

## Delivery and verification

Return the requested Korean deliverable first and in its original format unless
the user requested another shape. For review-only work, quote the ambiguous span
and name the missing relation without rewriting the text. Add a note only when
an unresolved ambiguity or missing private fact affects trust.

Before delivery:

- reread the complete changed scope and confirm that every actor, referent,
  condition, and logical relation is recoverable;
- compare facts, numbers, commands, requirement levels, uncertainty, and
  register with the source;
- remove padding introduced merely to make sentences longer or more formal;
- confirm that protected literals and established terms are unchanged; and
- check that correction did not replace the writer's voice with uniformly
  polished prose.

Finish when the missing relations are recoverable and meaning is preserved.
Do not generate successive rewrites merely to make an already-clear sentence
sound fuller or more polished.

The copyable [always-on core](assets/always-on-core.md) is an optional compact
adapter for the agent's own Korean responses. Install or modify an always-on
instruction surface only when the user explicitly requests that setup. The
skill remains usable without the adapter.

## Gotchas

- Longer Korean is not necessarily clearer. Add only the morphology or context
  that recovers a real relation.
- A sentence does not need an explicit pronoun when Korean discourse already
  makes the subject clear.
- Sino-Korean vocabulary is not inherently more precise. Audience usage and the
  governing term decide.
- Do not turn Korean clarity work into an AI-detector evasion pass or general
  document redesign.
