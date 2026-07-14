# Changelog

All notable changes to PresentationOS will be documented in this file.

## [0.1.0] — 2026-07-14

### Added

#### Product foundation

- `README.md` with project purpose, workflow, repository structure, quick start, and current status.
- `VISION.md` with product principles, success definition, and roadmap.
- `PRD.md` with scope, requirements, acceptance criteria, risks, and future quality metrics.
- `ARCHITECTURE.md` with artifact contracts, agent topology, project directories, data flow, error types, and QA severity.
- `WORKFLOW.md` with the standard and fast operating procedures and approval gates.
- `AGENTS.md` with repository-level instructions for Codex and other coding agents.

#### Specialist agents

- Design Analyst
- Content Analyst
- Story Architect
- Slide Planner
- Copy Editor
- Data Visualizer
- Asset Planner
- Codex Builder
- QA Reviewer

Each agent includes a mission, required inputs, outputs, process, copyable prompt, guardrails, success criteria, and handoff.

#### Orchestration

- `prompts/00-orchestrator.md` for managing stage status, specialist runs, approval gates, blockers, and next actions.

#### Templates

- Project Brief
- Design System
- Content Inventory
- Storyline
- Slide Mapping Table
- Chart and Diagram Specifications
- Visual Asset Manifest
- QA Report

#### Structured data

- JSON Schema for the slide mapping table.

#### Examples

- Investment-deck workflow example.
- Example machine-readable slide mapping records.

### Current limitations

- No automatic agent runner.
- No PowerPoint generation starter code.
- No rendering or visual-validation scripts.
- No packaged PowerPoint theme or component library.
- No automated source extraction or citation engine.
- No license selected.

## Next milestone — 0.2.0 Build Starter Kit

Planned scope:

- reference project directory;
- PowerPoint generation starter code;
- centralized theme tokens;
- reusable layout functions;
- chart and diagram helpers;
- asset loading and validation;
- slide rendering commands;
- technical QA checks;
- editable sample presentation;
- setup and run instructions.
