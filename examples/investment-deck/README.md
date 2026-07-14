# Example — Investment Deck

This example demonstrates how PresentationOS should be used for a hypothetical investment opportunity. It is intentionally generic and contains no real company data.

## Scenario

A user receives:

- a 52-page bilingual company PDF;
- a spreadsheet containing historical financials and projections;
- selected screenshots from a presentation whose visual system the user likes;
- a request to produce a 15–18 slide investment discussion deck.

The audience is an investment committee. The desired decision is approval to proceed to detailed diligence, not final transaction approval.

## Project structure

```text
examples/investment-deck/
├── README.md
└── slide-mapping-table.example.json
```

A live project would use the complete structure from `ARCHITECTURE.md`.

## Step 1 — Project brief

Key brief decisions:

- **Audience:** investment committee members with limited sector context;
- **Decision:** approve the next phase of diligence;
- **Main concern:** growth quality and downside risk;
- **Target length:** 16 main slides plus appendix;
- **Language:** English main deck, bilingual source notes where required;
- **Design reference:** selected dark-background investment slides;
- **Non-negotiable:** every financial metric must trace to the spreadsheet or source PDF.

## Step 2 — Design system

Representative references should include:

- cover;
- section divider;
- investment-thesis page;
- market chart;
- financial chart;
- risk page;
- process or next-steps page.

The Design Analyst should extract rules such as:

- dark neutral background;
- large white action titles;
- one accent color used only for decision-critical data;
- restrained card use;
- minimal decoration;
- charts with muted context series and one highlighted series;
- compact source notes;
- wide margins and low element count.

These are example rules, not a required PresentationOS style.

## Step 3 — Content inventory

The Content Analyst should identify and source:

- company history and ownership;
- products and revenue model;
- market size and growth;
- customer concentration;
- historical revenue and EBITDA;
- projections and assumptions;
- unit economics;
- competitive differentiation;
- transaction structure;
- management claims;
- operational, market, regulatory, and financial risks;
- contradictions between marketing material and model assumptions.

Example source issue:

```text
The PDF states “over 500 customers,” while the spreadsheet lists 418 active paying customers. This must be resolved or the definition must be clarified before use.
```

## Step 4 — Storyline

Example governing thought:

> The company merits detailed diligence because it combines an attractive structural market with differentiated customer economics, but the investment case depends on validating concentration risk and forecast assumptions.

Example chapter sequence:

1. Decision and preliminary recommendation
2. Company and transaction overview
3. Market attractiveness
4. Business quality and differentiation
5. Financial performance and value creation
6. Key risks and diligence priorities
7. Recommended next step

This sequence leads with the decision and keeps risk integrated into the investment case.

## Step 5 — Slide mapping

Example main-deck sequence:

1. Cover
2. Preliminary recommendation
3. Investment case at a glance
4. Company and transaction overview
5. Product and revenue model
6. Market growth is supported by structural demand drivers
7. The target occupies an attractive position in the value chain
8. Customer economics support retention and expansion
9. Revenue growth has been strong but concentration remains material
10. Margin expansion depends on two operational levers
11. Management's forecast assumes sustained conversion improvement
12. Base, upside, and downside cases produce materially different returns
13. Three risks require focused diligence
14. Diligence plan and decision gates
15. Proposed workplan and responsibilities
16. Closing recommendation

The attached example JSON shows representative records, not a complete deck.

## Step 6 — Copy and visual planning

Example action title:

```text
Revenue has grown at 28% CAGR, but the top five customers still represent 46% of sales
```

Example visual specification:

- left: editable revenue trend with CAGR annotation;
- right: horizontal bars showing top-five concentration;
- one highlighted risk annotation;
- source notes for both datasets;
- no decorative image.

## Step 7 — Codex build package

Provide Codex with:

```text
00-input/project-brief.md
00-input/sources/company-overview.pdf
00-input/data/financial-model.xlsx
01-analysis/design-system.md
01-analysis/content-inventory.md
02-story/storyline.md
03-plan/slide-mapping-table.md
03-plan/slide-mapping-table.json
03-plan/chart-specifications.md
03-plan/visual-asset-manifest.md
04-assets/
```

Use the prompt from `agents/08-codex-builder.md`.

## Step 8 — QA priorities

For an investment deck, Critical or Major issues commonly include:

- inconsistent historical numbers between slides;
- forecast values copied from the wrong scenario;
- enterprise value and equity value confusion;
- mixed currencies or fiscal years;
- market-size definitions that change across slides;
- charts that hide downside volatility;
- unsupported claims of leadership or defensibility;
- risks described without an associated diligence action;
- a recommendation stronger than the evidence supports.

## Expected outcome

The first draft should not be treated as final. The value of PresentationOS is that the first draft is based on an approved argument and structured build contract, allowing the human owner to focus on judgment, accuracy, and the most important slides rather than reconstructing the entire deck manually.
