# AGENTS.md

These instructions apply to coding agents working in this repository.

## Mission

Build and maintain PresentationOS as a reliable, model-agnostic workflow for producing editable, client-ready PowerPoint presentations from structured project artifacts.

## Read first

Before changing the repository, read:

1. `README.md`
2. `VISION.md`
3. `PRD.md`
4. `ARCHITECTURE.md`
5. `WORKFLOW.md`
6. the relevant file in `agents/`

For a presentation project, also read every approved artifact in the project folder before writing slide-generation code.

## Operating rules

### 1. Do not skip the planning artifacts

Do not infer an entire deck directly from a source PDF when an approved storyline or slide mapping table exists. Treat approved project artifacts as the build contract.

### 2. Preserve traceability

Do not alter important claims or numbers without recording the change. Keep source references attached to slide records and footnotes where required.

### 3. Build editable presentations

Prefer native PowerPoint elements:

- text boxes;
- shapes;
- lines and connectors;
- tables;
- editable charts;
- grouped diagram components.

Do not turn every slide into a PNG or JPEG. Full-slide rasterization is considered a failed build unless explicitly requested for a non-editable preview.

### 4. Centralize design tokens

Do not hard-code typography, spacing, or color independently on every slide. Create reusable theme values and layout helpers derived from the approved design system.

Typical tokens include:

- slide dimensions;
- margins;
- columns and gutters;
- type sizes and weights;
- text colors;
- background colors;
- accent colors;
- corner radii;
- line weights;
- spacing scale;
- chart palette;
- source-note style.

### 5. Use layout families

Implement repeated layout families as reusable functions or components. Example families:

- cover;
- section divider;
- statement;
- text plus image;
- chart plus insight;
- comparison;
- process;
- timeline;
- portfolio grid;
- closing call to action.

### 6. Validate before claiming completion

A successful code run is not enough. A presentation build must be opened or rendered and visually inspected.

At minimum:

- verify the PPTX exists and is readable;
- render all slides to images when tooling permits;
- check for text overflow;
- check objects outside slide bounds;
- check missing fonts and assets;
- check chart data and labels;
- check slide count against the approved mapping table;
- record unresolved issues.

### 7. Never invent missing assets silently

When an image, logo, font, or dataset is missing:

- use an approved fallback when one is defined;
- otherwise create a clearly marked placeholder;
- add the issue to the build log;
- do not pretend the final asset was supplied.

### 8. Treat bilingual slides carefully

For English and Chinese decks:

- use fonts with appropriate glyph coverage;
- do not assume identical line length or text-box height;
- preserve intentional language hierarchy;
- check punctuation and line breaks visually;
- allow language-specific type-size adjustments when the design system permits.

### 9. Avoid unsupported dependencies

Prefer maintained, documented libraries. Record required system tools and package versions. Add setup instructions when introducing a new dependency.

### 10. Keep project files organized

Generated deck code belongs under the relevant project's `05-build/src/`. Outputs, renders, and logs belong in their designated directories. Do not scatter generated files across the repository root.

## Build deliverables

A standard build task should produce:

```text
05-build/
├── src/
├── output/
│   └── deck.pptx
├── renders/
│   ├── slide-001.png
│   └── ...
└── build-log.md
```

The build log must include:

- build date or revision;
- source artifacts used;
- slide count;
- dependencies;
- validation performed;
- fallbacks used;
- unresolved issues;
- recommended next action.

## Definition of done

A deck build is done only when:

- every approved slide record has been implemented or explicitly deferred;
- the PPTX opens successfully;
- text and primary graphics remain editable;
- no critical content issue is known;
- no unresolved overflow or off-slide object remains;
- required assets are present or clearly marked;
- the output has been visually reviewed;
- the build log is complete;
- the QA Reviewer can assess the result without reconstructing the process.

## Change discipline

When modifying the PresentationOS framework itself:

- keep agent responsibilities distinct;
- update templates when contracts change;
- update schemas when structured fields change;
- update documentation when workflow behavior changes;
- add or update examples for non-trivial changes;
- avoid vendor-specific assumptions unless isolated behind a clear adapter.
