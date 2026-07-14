# Workflow

This document describes the recommended end-to-end operating procedure for a PresentationOS project.

## 1. Choose the operating mode

### Standard mode

Use all nine agents for client-facing, investment, executive, or high-risk presentations.

### Fast mode

Use Project Brief → Content Analyst → Story Architect → Slide Planner → Codex Builder → QA Reviewer for short, low-risk internal decks. The Design Analyst may be replaced by an existing approved design system.

## 2. Initialize the project

Create the project directory described in `ARCHITECTURE.md` and copy the templates into the appropriate folders.

Use a short, stable project identifier:

```text
client-topic-yyyy-mm
```

Example:

```text
acme-growth-strategy-2026-07
```

## 3. Complete the project brief

The project owner must define:

- who will see the deck;
- what they already know;
- what they should believe, decide, or do afterward;
- presentation type;
- expected length;
- delivery setting;
- language;
- deadline;
- brand constraints;
- confidentiality level;
- source-of-truth files;
- known sensitive claims or numbers.

Do not begin story design without a minimally complete brief.

**Gate A:** Project brief approved.

## 4. Prepare the source package

Place all inputs in `00-input/` and normalize filenames.

Recommended naming:

```text
source-01-company-profile.pdf
source-02-financial-model.xlsx
source-03-market-research.pdf
reference-01-cover.png
reference-02-data-slide.png
brand-logo-primary.svg
```

Avoid names such as `final-final-v3-new.pdf`.

Record which source is authoritative when files conflict.

## 5. Extract the design system

Run the Design Analyst on a representative set of reference slides.

Select examples that cover distinct layout families, such as:

- cover;
- section divider;
- text-led argument;
- data chart;
- comparison;
- process;
- portfolio or case-study page;
- closing page.

Do not provide fifty visually similar slides. Five to twelve well-chosen examples are usually more useful.

Save the result to:

```text
01-analysis/design-system.md
```

## 6. Build the content inventory

Run the Content Analyst on every authoritative source.

The output must distinguish:

- facts;
- claims;
- opinions;
- assumptions;
- quantitative data;
- quotes;
- duplicated content;
- contradictions;
- gaps;
- content suitable only for the appendix.

Save the result to:

```text
01-analysis/content-inventory.md
```

**Gate B:** Design system and content inventory reviewed.

## 7. Design the story

Run the Story Architect.

A good storyline should answer:

1. What is the central question?
2. What is the governing thought?
3. What must the audience understand first?
4. What evidence changes their mind?
5. What decision or action follows?

The storyline should not yet contain detailed slide layouts.

Save the result to:

```text
02-story/storyline.md
```

**Gate C:** Storyline approved.

## 8. Create the slide mapping table

Run the Slide Planner.

Each slide record must have:

- a clear role in the story;
- an action title;
- one primary message;
- limited supporting evidence;
- a proposed visual form;
- source references;
- a layout family;
- build notes.

Save both formats when possible:

```text
03-plan/slide-mapping-table.md
03-plan/slide-mapping-table.json
```

**Gate D:** Slide mapping table approved.

## 9. Finalize copy

Run the Copy Editor only after the plan is stable.

Priorities:

1. action titles;
2. lead statements;
3. chart annotations;
4. body copy;
5. footnotes and sources.

The Copy Editor must not add unsupported facts.

## 10. Specify charts and diagrams

Run the Data Visualizer.

For each visual, define:

- analytical question;
- recommended form;
- data fields;
- category order;
- units;
- comparison baseline;
- emphasis;
- annotation;
- source;
- accessibility risks;
- build instructions.

Avoid choosing a chart merely because it looks impressive.

## 11. Plan visual assets

Run the Asset Planner.

Every asset should have a purpose and a filename before the builder starts. Mark licensing or ownership status explicitly.

Save the manifest to:

```text
03-plan/visual-asset-manifest.md
```

Place approved assets in `04-assets/`.

## 12. Assemble the build package

Before invoking Codex, confirm that the following are present:

```text
[ ] project brief
[ ] source files
[ ] design system
[ ] content inventory
[ ] storyline
[ ] approved slide mapping table
[ ] approved slide copy
[ ] chart and diagram specifications
[ ] visual asset manifest
[ ] required fonts or approved fallbacks
[ ] output and QA requirements
```

## 13. Build the deck

Run the Codex Builder.

The build process should:

1. inspect all inputs;
2. report blockers;
3. create a theme and layout primitives;
4. build slides from the approved mapping table;
5. use editable objects;
6. add source footnotes where required;
7. save the PPTX;
8. render slides to images;
9. report unresolved issues.

**Gate E:** First build approved for QA and polish.

## 14. Review the deck

Run the QA Reviewer against both the PPTX and rendered images.

Review in this order:

1. critical factual and numerical issues;
2. story breaks and missing evidence;
3. slide titles and visual hierarchy;
4. overflow and rendering failures;
5. inconsistent charts, typography, and spacing;
6. low-priority polish.

Save the report to:

```text
06-qa/qa-report.md
```

## 15. Repair and re-review

Fix issues by severity. Re-render affected slides after every structural or layout change.

Do not mark an issue resolved without checking the actual output.

**Gate F:** No open critical issues; major issues accepted or resolved.

## 16. Deliver and archive

The delivery package should include:

- final PPTX;
- optional PDF export;
- final source package or data appendix when required;
- QA report or internal sign-off;
- asset rights notes;
- a record of approved assumptions.

Archive superseded artifacts rather than silently overwriting them when traceability matters.

## Recommended human review focus

Human time is most valuable on:

- the opening sequence;
- the governing thought;
- section transitions;
- the most important data slides;
- claims involving risk, money, or reputation;
- the closing recommendation;
- overall visual taste.
