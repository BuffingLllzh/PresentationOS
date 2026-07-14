# Product Requirements Document

## 1. Product

**Name:** PresentationOS  
**Version:** v0.1  
**Status:** Foundation specification

## 2. Objective

Create a reusable, model-agnostic workflow that converts dense source material and selected design references into a structured build package for an editable, client-ready PowerPoint presentation.

v0.1 is documentation-first. It defines the workflow, agent contracts, templates, schemas, and quality rules required for future automation.

## 3. Primary user problem

Users regularly receive long PDFs, mixed-language documents, generated copy, spreadsheets, charts, and existing presentations. They understand the general assignment, but lose time making hundreds of small decisions:

- what to keep or remove;
- what order to present ideas in;
- how many slides to create;
- what each slide should say;
- how to visualize the content;
- how to reuse a strong reference style without copying it;
- how to turn the plan into an editable deck;
- how to check the output efficiently.

## 4. Target users

- independent consultants and agencies;
- strategy, investment, and corporate-development professionals;
- startup founders;
- sales and marketing teams;
- analysts and operators producing recurring decks.

## 5. Jobs to be done

### JTBD-1: Understand source material

When I receive a large source package, I want the system to identify claims, evidence, numbers, gaps, duplication, and source locations so that I do not need to manually summarize everything before planning the deck.

### JTBD-2: Create a persuasive story

When I know the purpose and audience, I want a clear narrative sequence so that the presentation leads to a decision rather than merely repeating the source document.

### JTBD-3: Plan every slide

When the story is approved, I want a structured mapping table so that slide production becomes execution instead of repeated interpretation.

### JTBD-4: Reuse a design language

When I provide selected reference slides, I want their visual logic translated into reusable rules so that the new deck feels coherent without copying proprietary content.

### JTBD-5: Produce editable slides

When the build package is complete, I want Codex or another coding agent to generate an editable PPTX with real text, shapes, charts, and diagrams.

### JTBD-6: Review quickly

When the first draft is built, I want a prioritized QA report so that I can fix high-impact problems before spending time on polish.

## 6. In scope for v0.1

- repository documentation;
- nine agent specifications;
- agent input/output contracts;
- copyable prompt blocks;
- project and handoff templates;
- machine-readable slide mapping schema;
- example investment-deck workflow;
- Codex build rules;
- QA severity model.

## 7. Out of scope for v0.1

- a hosted application;
- automatic model orchestration;
- a graphical user interface;
- direct integration with PowerPoint or Google Slides;
- guaranteed one-click presentation generation;
- automated image generation;
- pixel-perfect reproduction of a reference deck;
- automated fact verification against external databases;
- support for every presentation archetype.

## 8. Functional requirements

### FR-1: Project brief

The system must define a standard brief containing audience, objective, decision, deck type, language, length, delivery context, brand constraints, confidentiality, and source-of-truth rules.

### FR-2: Design extraction

The Design Analyst must output a design system covering:

- visual personality;
- slide size and margins;
- grid and alignment;
- typography hierarchy;
- color roles;
- layout families;
- image treatment;
- chart conventions;
- icon and diagram conventions;
- density and whitespace;
- anti-patterns.

### FR-3: Content inventory

The Content Analyst must identify:

- source sections;
- claims;
- evidence;
- quantitative data;
- definitions;
- dependencies;
- duplication;
- contradictions;
- missing information;
- exact source locations.

### FR-4: Storyline

The Story Architect must create a narrative with:

- audience starting point;
- desired final belief or action;
- governing thought;
- chapter sequence;
- argument logic;
- transitions;
- optional appendix logic.

### FR-5: Slide mapping

The Slide Planner must output one record per slide with at least:

- slide number;
- section;
- slide type;
- action title;
- key message;
- supporting evidence;
- recommended visual;
- source references;
- layout family;
- asset requirements;
- build notes.

### FR-6: Copy editing

The Copy Editor must produce concise, audience-appropriate slide copy without changing factual meaning or inventing evidence.

### FR-7: Data visualization planning

The Data Visualizer must select chart and diagram forms based on the analytical task, not visual novelty.

### FR-8: Asset planning

The Asset Planner must define every required image, icon, logo, map, illustration, and diagram, including source, rights status, aspect ratio, and placement intent.

### FR-9: Editable build

The Codex Builder must produce editable slide objects wherever practical and must not use full-slide screenshots as the primary construction method.

### FR-10: QA review

The QA Reviewer must evaluate:

- story coherence;
- content accuracy;
- source traceability;
- numerical consistency;
- copy length;
- typography;
- alignment;
- spacing;
- color use;
- chart integrity;
- asset quality;
- editability;
- overflow and rendering errors.

## 9. Non-functional requirements

### NFR-1: Reusability

Artifacts must be reusable across projects and models.

### NFR-2: Transparency

Every agent output must state assumptions, uncertainties, and unresolved questions.

### NFR-3: Traceability

Claims and numbers must retain references to their source file and location.

### NFR-4: Modularity

Each agent must be runnable independently when its required inputs are available.

### NFR-5: Human control

The workflow must include explicit approval gates before story lock, slide-plan lock, and final delivery.

### NFR-6: Language flexibility

The system must support English, Traditional Chinese, Simplified Chinese, and bilingual decks, subject to appropriate font availability.

## 10. User workflow

1. Prepare source files and project brief.
2. Select representative reference slides.
3. Extract design system.
4. Build content inventory.
5. Define storyline.
6. Create slide mapping table.
7. Edit slide copy.
8. Plan charts, diagrams, and assets.
9. Build editable PPTX.
10. Render and review.
11. Fix critical and major issues.
12. Deliver.

## 11. Acceptance criteria for v0.1

v0.1 is complete when:

- all nine agent files exist;
- every agent includes mission, inputs, outputs, process, prompt, constraints, and success criteria;
- all core templates exist;
- the mapping-table JSON schema validates the required slide fields;
- the root documentation explains the complete workflow;
- one example demonstrates expected handoffs;
- Codex has clear repository-level build instructions;
- QA issues use a consistent severity classification.

## 12. Quality metrics for future builds

- percentage of slides with a single clear message;
- percentage of numerical claims with source references;
- number of critical QA issues per deck;
- text overflow count;
- percentage of editable charts and diagrams;
- manual time from source package to first draft;
- manual time from first draft to delivery;
- number of client revision rounds caused by structural issues.

## 13. Risks

### Risk: False confidence in generated content

Mitigation: preserve source traceability and prohibit unsupported claims.

### Risk: Design references are copied too literally

Mitigation: extract principles and layout families rather than replicating unique pages.

### Risk: Agent outputs become excessively verbose

Mitigation: use structured templates, field limits, and approval gates.

### Risk: Automation creates technically valid but visually weak decks

Mitigation: render every slide, review representative page types, and keep human taste as the final gate.

### Risk: The workflow becomes too heavy for simple decks

Mitigation: define a fast path for short, low-risk presentations in a later release.
