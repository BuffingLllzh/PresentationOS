# Architecture

## 1. Overview

PresentationOS uses a staged, artifact-driven architecture. Each agent performs one bounded job and produces a named artifact for the next stage.

The architecture is deliberately simple:

- files are the interface;
- Markdown and JSON are the default interchange formats;
- every stage may be reviewed by a human;
- agents do not silently rewrite upstream decisions;
- the builder consumes approved artifacts rather than interpreting the project from scratch.

## 2. System context

```text
Human owner
   │
   ├── Project brief
   ├── Source package
   ├── Reference slides
   └── Approval decisions
           │
           ▼
PresentationOS agents
           │
           ├── Structured analysis artifacts
           ├── Story and slide plan
           ├── Build specification
           └── QA report
           │
           ▼
Coding / presentation engine
           │
           ├── Editable PPTX
           ├── Rendered slide images
           └── Build logs
           │
           ▼
Human final review and delivery
```

## 3. Architectural principles

### Artifact-driven handoffs

Agents communicate through saved artifacts, not hidden conversational context. This improves repeatability, traceability, and the ability to replace one model with another.

### Single responsibility

Each agent has one primary responsibility. An agent may flag upstream problems, but it must not casually take over another agent's role.

### Deterministic structure, flexible judgment

Outputs should use predictable headings, tables, and fields. The reasoning within those fields remains adaptable to the project.

### Approval gates

The recommended gates are:

- Gate A: project brief approved;
- Gate B: design system and content inventory approved;
- Gate C: storyline approved;
- Gate D: slide mapping table approved;
- Gate E: first build approved for polish;
- Gate F: QA cleared for delivery.

### Source traceability

Every material claim, number, quote, and chart input should point to a source file and location. Unknown provenance is a QA issue.

### Editable output

The final PPTX should use native text boxes, shapes, tables, and charts where practical. Images may be used for photography, illustrations, maps, and complex visual assets, but not as a shortcut for constructing the entire slide.

## 4. Agent topology

### 01 — Design Analyst

**Purpose:** Convert selected reference slides and brand inputs into a reusable design system.

**Consumes:** reference slides, brand assets, delivery context.  
**Produces:** `design-system.md`.

### 02 — Content Analyst

**Purpose:** Extract, classify, de-duplicate, and source all relevant content.

**Consumes:** source package, project brief.  
**Produces:** `content-inventory.md` and optional structured data files.

### 03 — Story Architect

**Purpose:** Create the argument and narrative sequence for the target audience.

**Consumes:** project brief, content inventory.  
**Produces:** `storyline.md`.

### 04 — Slide Planner

**Purpose:** Translate the storyline into an executable slide-by-slide plan.

**Consumes:** storyline, content inventory, design system.  
**Produces:** `slide-mapping-table.md` and optionally JSON.

### 05 — Copy Editor

**Purpose:** Turn planned messages into concise slide-ready titles and body copy.

**Consumes:** slide mapping table, source references, tone requirements.  
**Produces:** approved slide copy embedded in the mapping table or a separate copy deck.

### 06 — Data Visualizer

**Purpose:** Specify charts and diagrams that accurately express the intended analytical relationship.

**Consumes:** slide plan, quantitative data, design system.  
**Produces:** chart specifications and diagram specifications.

### 07 — Asset Planner

**Purpose:** Plan, source, and name non-data visual assets.

**Consumes:** slide plan, design system, chart plan.  
**Produces:** `visual-asset-manifest.md` and asset files or generation prompts.

### 08 — Codex Builder

**Purpose:** Generate the editable PPTX and build artifacts.

**Consumes:** all approved upstream artifacts and assets.  
**Produces:** PPTX, slide renders, build log, unresolved issue list.

### 09 — QA Reviewer

**Purpose:** Review content, visuals, technical integrity, and editability.

**Consumes:** source package, approved plan, PPTX, slide renders, build log.  
**Produces:** `qa-report.md` with prioritized fixes.

## 5. Data flow

```text
project-brief.md
      │
      ├──────────────► Design Analyst ◄──────── reference-slides/
      │                         │
      │                         ▼
      │                  design-system.md
      │
source package ───────► Content Analyst
                                │
                                ▼
                       content-inventory.md
                                │
project brief ────────────────► Story Architect
                                │
                                ▼
                           storyline.md
                                │
content inventory + design system
                                │
                                ▼
                         Slide Planner
                                │
                                ▼
                  slide-mapping-table.md/json
                         │               │
                         ▼               ▼
                   Copy Editor     Data Visualizer
                         │               │
                         └───────┬───────┘
                                 ▼
                           Asset Planner
                                 │
                                 ▼
                           Codex Builder
                                 │
                       ┌─────────┴─────────┐
                       ▼                   ▼
                    deck.pptx         renders/
                       └─────────┬─────────┘
                                 ▼
                           QA Reviewer
                                 │
                                 ▼
                           qa-report.md
```

## 6. Artifact contracts

Every artifact must include:

- project identifier;
- artifact version;
- date or revision identifier;
- input files used;
- assumptions;
- unresolved questions;
- structured output;
- approval status.

Recommended status values:

```text
DRAFT
REVIEW_REQUIRED
APPROVED
SUPERSEDED
```

## 7. Project directory convention

```text
projects/<project-id>/
├── 00-input/
│   ├── project-brief.md
│   ├── sources/
│   ├── reference-slides/
│   ├── brand/
│   └── data/
├── 01-analysis/
│   ├── design-system.md
│   └── content-inventory.md
├── 02-story/
│   └── storyline.md
├── 03-plan/
│   ├── slide-mapping-table.md
│   ├── slide-mapping-table.json
│   ├── chart-specifications.md
│   └── visual-asset-manifest.md
├── 04-assets/
│   ├── images/
│   ├── icons/
│   ├── diagrams/
│   └── charts/
├── 05-build/
│   ├── src/
│   ├── output/
│   │   └── deck.pptx
│   ├── renders/
│   └── build-log.md
└── 06-qa/
    ├── qa-report.md
    └── approved/
```

## 8. Slide record model

A slide record is the central unit passed to the builder. It should contain:

```yaml
slide_number: 7
section: Market Opportunity
slide_type: data
objective: Prove that the addressable market is both large and expanding.
action_title: The target market is expected to exceed US$4B by 2029
key_message: Growth is driven by two measurable structural trends.
supporting_points:
  - Trend A contributes...
  - Trend B contributes...
visual:
  type: stacked-column-chart
  purpose: show total growth and segment contribution
sources:
  - file: source.pdf
    location: page 18
layout_family: chart-left-insight-right
assets: []
build_notes:
  - Use editable chart data.
  - Highlight 2029 total.
status: APPROVED
```

The machine-readable version is defined in `schemas/slide-mapping-table.schema.json`.

## 9. Error handling

Agents must not fill critical gaps by guessing. They should classify issues as:

- `BLOCKING`: work cannot continue reliably;
- `ASSUMPTION`: work can continue if the assumption is made explicit;
- `QUESTION`: human input would improve quality;
- `SOURCE_GAP`: a claim or number lacks traceability;
- `DESIGN_GAP`: a visual rule is undefined;
- `BUILD_GAP`: the requested slide cannot be built with current assets or data.

## 10. QA severity model

- **Critical:** wrong fact, wrong number, misleading chart, broken file, missing key slide, unreadable output, or confidentiality issue.
- **Major:** weak logic, unclear title, inconsistent design system, overflow, poor chart choice, or missing source reference.
- **Minor:** small spacing, punctuation, alignment, or polish issue that does not change understanding.
- **Suggestion:** optional enhancement.

## 11. Extension points

Future implementations may add:

- an orchestrator that runs agents automatically;
- YAML or JSON project configuration;
- PowerPoint generation libraries;
- theme tokens;
- automated rendering;
- visual comparison against approved references;
- schema validation;
- source citation extraction;
- deck archetype packages;
- repair agents that address QA findings.

These additions should preserve the artifact contracts defined in this document.
