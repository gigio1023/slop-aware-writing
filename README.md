# Slop-Aware Writing Skills

[![skills.sh](https://skills.sh/b/gigio1023/slop-aware-writing)](https://skills.sh/gigio1023/slop-aware-writing) ![writing](https://img.shields.io/badge/writing-EN%20%7C%20KO%20%7C%20IT%20%7C%20ZH-22684E) ![package](https://img.shields.io/badge/package-2%20portable%20skills-555) [![license](https://img.shields.io/badge/license-MIT-555)](LICENSE)

This repository publishes two related writing skills. `slop-aware-writing` handles explicit focused revision of existing prose to remove AI slop without flattening meaning or voice. `korean-clarity` repairs Korean whose sentence components, morphology, or ordinary technical wording were lost under agent-style compression.

`slop-aware-writing` treats slop as a functional writing failure: plausible completion has replaced selection, evidence, reader context, or a real point of view. It handles requested humanizing, deslop, terminology, and voice-preserving revision of existing drafts. General authoring belongs to the requested writing workflow, optionally `technical-report-writing` in agent-skills; no automatic second pass is required. It trusts the LLM's base fluency for ordinary grammar and idiom. The skill adds the diagnosis, evidence boundary, voice protection, and minimal-edit tests that general language competence does not supply reliably.

[Architecture](#architecture) · [Languages](#language-overlays) · [Evidence](#evidence-and-lineage) · [Layout](#package-layout) · [Install](#install) · [Development](#local-development)

## Architecture

| Skill | Use it for | Do not use it for |
|---|---|---|
| `slop-aware-writing` | explicit deslop, voice-preserving revision, and terminology review | grammar-only correction, translation, or ordinary chat |
| `korean-clarity` | Korean responses and artifacts with omitted sentence components, particles, endings, predicates, relations, or conventional wording | translation, AI-authorship detection, or document-level deslop by itself |

The skills have independent triggers and can be installed separately. [Composition and migration](docs/focused-revision.md) explains the boundary with the writer and sharing skills. When both apply, `slop-aware-writing` owns the evidence boundary, reader job, structure, edit authority, and voice. `korean-clarity` repairs semantic completeness only inside those constraints.

The `slop-aware-writing` `SKILL.md` is a router. It establishes the reader job, evidence boundary, edit authority, governing policy, and voice sample. It always loads the common slop diagnosis. A language overlay loads only when a candidate depends on that language or locale.

| Job | Covers | Primary reference |
|---|---|---|
| Revision | humanizing and scoped structural or context repair of an existing draft | `references/revision.md` |
| Focused pass | terminology or a language-specific slop pattern | `references/terminology.md` or one language overlay |

The common layer defines four recurring failures:

- generic completion that could fit an unrelated document;
- performed reasoning whose citations or transitions do not establish the claimed relation;
- reader displacement by templates, hidden sessions, and irrelevant detail;
- voice flattening through safe, uniform, over-polished prose.

It tests candidate spans against the reader job, evidence, deletion cost, and writer's repeated choices. It preserves facts, conditions, requirement levels, logical relations, and uncertainty. It never invents specificity.

Search snippets, copied citation lists, generated summaries, and local research notes can locate evidence. They do not inherit the authority of the original source. A cold read checks self-containment; it does not prove factual accuracy or replace representative-reader testing.

## Language overlays

| Layer | What it contributes | What it does not claim |
|---|---|---|
| English | formulaic rhetoric, unsupported `-ing` relations, inflated significance, and register flattening | a general English style guide |
| Korean | `im-not-ai` pattern families with Korean evidence, keep tests, and explicit limits | a required scan of every sentence or pattern ID |
| Italian | formulaic connectors, bureaucratic weight, translation interference, and meaning safety during repair | an Italian grammar syllabus or durable AI-tell list |
| Chinese | parallel inflation, bureaucratic scaffolding, and locale safety when normalization is in scope | general proofreading or unrequested localization |

For another language, the model uses its contextual fluency with the common diagnosis, writer sample, and governing locale guidance. During an authorized rewrite it may silently fix one obvious local error. Grammar-only proofreading does not trigger this skill, and no English checklist is translated into a new language.

`korean-clarity` is a compact semantic-clarity floor rather than a Korean grammar reference. Its optional `assets/always-on-core.md` can be copied into a supported always-on instruction surface when the user explicitly requests that setup. The skill works without the adapter.

## Evidence and lineage

The [sources and inspiration register](docs/sources-and-inspiration.md) records the inspected version, source status or license, adopted insight, scope limit, and rejected idea for every source family. It covers `fluent-korean`, `im-not-ai`, `petergyang/no-ai-slop`, the local `brain/clips` and `brain/research` notes, official language and plain-language guidance, regional Chinese standards, and research on model-assisted revision and generated prose.

[Design and lineage notes](docs/merge-notes.md) explain how the earlier skills were consolidated. The [redesign plan](docs/redesign-plan.md) is a historical record. [Evaluation prompts](docs/eval-prompts.md) contain lightweight trigger and preservation checks, not benchmark results.

## Package layout

```text
slop-aware-writing/
├── README.md
├── README.ko.md
├── LICENSE
├── docs/                   # provenance and design records; not installed
├── korean-clarity/         # Korean semantic-clarity skill
│   ├── SKILL.md
│   └── assets/             # optional always-on adapter
└── slop-aware-writing/     # document-level slop skill
    ├── SKILL.md
    └── references/         # loaded by job and language
```

The package follows the [Agent Skills format](https://agentskills.io/) and is distributed with the [Skills CLI](https://github.com/vercel-labs/skills). It contains no Codex-only or Claude Code-only workflow in the portable core.

## Install

Requires Node.js 22.20.0 or newer.

```bash
npx --yes skills add 'gigio1023/slop-aware-writing#main' \
  --skill slop-aware-writing korean-clarity \
  --agent codex claude-code \
  --global \
  --yes
```

Omit either skill name to install only the other skill. Change the agent IDs as needed. The CLI also supports `cursor`, `gemini-cli`, and `antigravity`. Omit `--global` for a project install. Verify with `npx --yes skills list --global`; update with `npx --yes skills update slop-aware-writing korean-clarity --global --yes`.

### Rename migration

An existing `clear-writing` install is not renamed in place. Install `slop-aware-writing`, verify that the new handle appears, then remove the old global handle:

```bash
npx --yes skills remove --global clear-writing --yes
```

For a project-scoped installation, omit `--global`. The published source is `gigio1023/slop-aware-writing`.

## Local development

```bash
npx --yes skills add . --list --full-depth
```

Before publishing, confirm that the command finds exactly two skills named `slop-aware-writing` and `korean-clarity`, each frontmatter name matches its folder, every linked reference or asset exists, and both READMEs describe the same package.
