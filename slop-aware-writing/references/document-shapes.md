# Document Shapes

Use this page after choosing the document's primary reader job in `authoring.md`. The shapes below are selection prompts, not templates or completion checklists. Keep only the sections that help the reader act, understand, decide, or verify.

Every value, command, example, result, error, and recovery step must come from supplied material, inspected repository evidence, or verified external sources. Otherwise omit it or use a visibly fake placeholder.

## Contents

- Select by reader job
- Procedure or how-to
- Lookup or API reference
- Decision or analysis
- Architecture explanation
- Status report or decision memo
- README or contribution guide
- Structural keep tests

## Select by reader job

| Reader job | Useful shape | Usually unnecessary |
| --- | --- | --- |
| Complete a task | prerequisites, ordered actions, success signal, evidenced recovery | project history, generic benefits |
| Look up behavior | scope, names and types, constraints, defaults, errors, verified example | narrative walkthrough |
| Evaluate a choice | finding or decision, evidence, rationale, alternatives actually considered, limits | ceremonial summary, invented options |
| Understand a system | problem, boundaries, components, flow, rationale, trade-offs | component inventory without relationships |
| Review current state | outcome, material variance, evidence, next action, owner or timing when known | activity diary |
| Start or contribute | shortest supported path, checks, navigation to maintained detail | speculative setup paths, generic PR advice |

A familiar heading is not evidence that a section belongs. Select the smallest shape that makes the page complete for its reader.

## Procedure or how-to

Start with the task and any prerequisite the reader must satisfy before the first command. Order steps only when order matters. Each consequential action needs an observable success condition; add recovery only for failures supported by code, tests, issues, logs, or user-provided evidence.

Do not hide required choices behind words such as "appropriate" or "as needed." Name the rule, supported value, or decision owner when the evidence does. Do not invent a recommended value to make the procedure look complete.

## Lookup or API reference

Lead with the lookup scope and current behavior. Use stable, repeated fields for signatures, options, schemas, or commands:

- exact name and type;
- whether it is required and any verified default;
- constraints and side effects;
- errors or failure behavior;
- one verified example, or a clearly fictional placeholder when an example is still useful.

Keep prose for relationships and caveats. Use a table only when the same fields repeat across entries. Do not force an argument or tutorial arc onto a page the reader will scan nonlinearly.

## Decision or analysis

Lead with the decision, recommendation, request, or finding. Connect every material claim to a reason or source, and preserve the warrant that explains why the support fits. Record status, constraints, consequences, and unresolved limits when they affect the choice.

List alternatives only when they were actually considered. A stock "alternatives" section filled after the fact creates false process history. Likewise, do not present an inference as a settled decision or consensus.

## Architecture explanation

Name the problem and system boundary before describing components. Explain the relationships or data flow that make the design intelligible, then the rationale and material trade-offs supported by evidence. A component catalog alone is not an architecture explanation.

Use a diagram only when it makes relationships easier to understand than short prose. The surrounding text still owns the takeaway, important conditions, and accessibility context.

## Status report or decision memo

Open with the outcome or current state. Include material variance from the expected state, the evidence behind it, and the next action. Name an owner or timing only when known or required by the genre.

Distinguish completed results from attempted activity. Omit a chronological work log unless sequence itself explains a failure, migration, or decision.

## README or contribution guide

Expose the shortest supported path for the intended reader: prerequisites, setup or use, and an observable success signal. Link to the maintained owner of volatile or exhaustive detail instead of duplicating it.

Document only the repository's actual contribution flow, checks, branch rules, and release conventions. Generic instructions about forks, pull requests, commit formats, or environment files are misleading when the repository does not establish them.

## Structural keep tests

Before keeping a block, ask:

- Does this section serve the page's primary reader job?
- Does a table expose a real repeated-field comparison?
- Does the heading help navigation rather than merely label one paragraph?
- Is the example verified or unmistakably fictional?
- Is this fact maintained here, or duplicated from a better owner?
- Would deleting the rationale make the conclusion harder to evaluate?
- Does the page remain complete without narration about how the draft was made?

Delete structure that fails these tests. Preserve necessary detail even when the result is longer: brevity is not an independent objective.
