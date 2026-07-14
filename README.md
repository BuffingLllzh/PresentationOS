# PresentationOS

> An AI-assisted operating system for turning dense source material into clear, editable, client-ready presentations.

PresentationOS is a reusable workflow for building professional decks from PDFs, documents, spreadsheets, research, and reference presentations. It separates **thinking**, **planning**, **design extraction**, **production**, and **quality assurance** into focused agents so that AI does not jump straight from a long document to a messy slide deck.

## Why this exists

Most AI presentation workflows fail for the same reasons:

- the source material is not prioritized before slide creation;
- the story is not designed before layouts are generated;
- visual references are copied loosely instead of translated into rules;
- too much text is placed on each slide;
- charts and diagrams are treated as decoration rather than evidence;
- the final deck is difficult to edit;
- no structured QA pass checks content, numbers, hierarchy, or alignment.

PresentationOS fixes this by using a staged production pipeline.

## Core principle

**Do not ask one model to understand the source, write the story, design every slide, generate assets, and review its own work in one step.**

Instead, use specialized agents with explicit inputs and outputs:

1. Design Analyst
2. Content Analyst
3. Story Architect
4. Slide Planner
5. Copy Editor
6. Data Visualizer
7. Asset Planner
8. Codex Builder
9. QA Reviewer

## Workflow

```text
Source files + project brief
          │
          ▼
  01 Design Analyst ───────► Design System
          │
  02 Content Analyst ──────► Content Inventory
          │
  03 Story Architect ──────► Storyline
          │
  04 Slide Planner ────────► Slide Mapping Table
          │
  05 Copy Editor ──────────► Final Slide Copy
          │
  06 Data Visualizer ──────► Chart & Diagram Plan
          │
  07 Asset Planner ────────► Visual Asset Manifest
          │
  08 Codex Builder ────────► Editable PPTX
          │
  09 QA Reviewer ──────────► QA Report + Fix List
```

## Repository structure

```text
PresentationOS/
├── README.md
├── VISION.md
├── PRD.md
├── ARCHITECTURE.md
├── WORKFLOW.md
├── AGENTS.md
├── agents/
│   ├── 01-design-analyst.md
│   ├── 02-content-analyst.md
│   ├── 03-story-architect.md
│   ├── 04-slide-planner.md
│   ├── 05-copy-editor.md
│   ├── 06-data-visualizer.md
│   ├── 07-asset-planner.md
│   ├── 08-codex-builder.md
│   └── 09-qa-reviewer.md
├── templates/
│   ├── project-brief.md
│   ├── design-system.md
│   ├── content-inventory.md
│   ├── storyline.md
│   ├── slide-mapping-table.md
│   ├── visual-asset-manifest.md
│   └── qa-report.md
├── schemas/
│   └── slide-mapping-table.schema.json
└── examples/
    └── investment-deck/
        └── README.md
```

## Quick start

### 1. Create a project folder

```text
projects/client-project/
├── 00-input/
│   ├── source.pdf
│   ├── reference-slides/
│   └── project-brief.md
├── 01-analysis/
├── 02-story/
├── 03-plan/
├── 04-assets/
├── 05-build/
└── 06-qa/
```

### 2. Complete the project brief

Copy `templates/project-brief.md` into the project folder. Define:

- audience;
- decision or action required;
- presentation type;
- target length;
- language;
- delivery format;
- brand and design constraints;
- claims that require exact sourcing.

### 3. Run agents in order

Use the prompt in each `agents/` file. Save every output as a project artifact. Do not skip directly to the builder unless the deck is extremely simple.

### 4. Give Codex the build package

The minimum build package is:

- original source files;
- project brief;
- design system;
- storyline;
- slide mapping table;
- approved slide copy;
- chart and diagram plan;
- visual asset manifest.

Codex should create an editable `.pptx`, not a collection of slide screenshots.

### 5. Review and iterate

Run the QA Reviewer. Fix all critical issues before polishing secondary slides.

## Supported deck types in v0.1

- Investment and transaction decks
- Startup pitch decks
- Corporate profiles
- Product and solution presentations

The architecture is intentionally generic enough to support strategy decks, proposals, reports, training decks, and board presentations later.

## Non-negotiable output rules

- One slide, one primary message.
- Slide titles should communicate the conclusion, not merely name the topic.
- Important numbers must be traceable to a source.
- Charts must be editable whenever practical.
- Text must remain editable.
- No full-slide screenshots as a shortcut.
- Reference decks provide design rules, not content to copy.
- The final human reviewer owns taste, accuracy, and client suitability.

## Status

Current target: **v0.1 — Foundation and agent specifications**.

## License

No license has been selected yet. Add one before encouraging external reuse or contributions.
