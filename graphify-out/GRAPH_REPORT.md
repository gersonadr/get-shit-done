# Graph Report - agents  (2026-04-11)

## Corpus Check
- 29 files · ~64,274 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 126 nodes · 162 edges · 15 communities detected
- Extraction: 89% EXTRACTED · 11% INFERRED · 0% AMBIGUOUS · INFERRED: 18 edges (avg confidence: 0.69)
- Token cost: 0 input · 0 output

## God Nodes (most connected - your core abstractions)
1. `GSD Verifier Agent` - 13 edges
2. `GSD Plan Checker Agent` - 13 edges
3. `GSD Phase Researcher Agent` - 11 edges
4. `GSD Planner Agent` - 10 edges
5. `GSD Intel Updater Agent` - 9 edges
6. `GSD Eval Planner Agent` - 8 edges
7. `GSD UI Auditor Agent` - 8 edges
8. `GSD UI Checker Agent` - 6 edges
9. `GSD AI Researcher Agent` - 6 edges
10. `CLAUDE.md (Project Instructions)` - 6 edges

## Surprising Connections (you probably didn't know these)
- `GSD Doc Verifier Agent` --semantically_similar_to--> `GSD Verifier Agent`  [INFERRED] [semantically similar]
  agents/gsd-doc-verifier.md → agents/gsd-verifier.md
- `GSD Assumptions Analyzer Agent` --semantically_similar_to--> `GSD Phase Researcher Agent`  [INFERRED] [semantically similar]
  agents/gsd-assumptions-analyzer.md → agents/gsd-phase-researcher.md
- `GSD UI Checker Agent` --semantically_similar_to--> `GSD Plan Checker Agent`  [INFERRED] [semantically similar]
  agents/gsd-ui-checker.md → agents/gsd-plan-checker.md
- `Calibration Tier (full_maturity / standard / minimal_decisive)` --semantically_similar_to--> `Claim Provenance (VERIFIED / CITED / ASSUMED tagging)`  [INFERRED] [semantically similar]
  agents/gsd-advisor-researcher.md → agents/gsd-phase-researcher.md
- `GSD Code Reviewer Agent` --semantically_similar_to--> `GSD UI Auditor Agent`  [INFERRED] [semantically similar]
  agents/gsd-code-reviewer.md → agents/gsd-ui-auditor.md

## Hyperedges (group relationships)
- **Plan Phase Quality Loop (Planner → Plan Checker → Revision Gate)** — gsd_planner, gsd_plan_checker, concept_revision_gate, artifact_plan_md [INFERRED 0.90]
- **Research-to-Planning Pipeline (Phase Researcher → RESEARCH.md → Planner → PLAN.md)** — gsd_phase_researcher, artifact_research_md, gsd_planner, artifact_plan_md [EXTRACTED 0.95]
- **AI Integration Agent Cluster (Framework Selector → AI Researcher → Eval Auditor → AI-SPEC)** — gsd_framework_selector, gsd_ai_researcher, gsd_eval_auditor, artifact_ai_spec_md [INFERRED 0.85]
- **AI Integration Phase Pipeline (Domain Research → Eval Planning → AI-SPEC)** — gsd_domain_researcher, gsd_eval_planner, gsd_eval_planner_ai_spec_md, gsd_domain_researcher_ai_spec_1b, orchestrator_gsd_ai_integration_phase [EXTRACTED 0.95]
- **Post-Execution Audit Triad (Security + Validation + UI Review)** — gsd_security_auditor, gsd_nyquist_auditor, gsd_ui_auditor, gsd_executor_summary_md [INFERRED 0.80]
- **Code Review and Fix Pipeline (Review → Fix → Commit)** — gsd_code_reviewer, gsd_code_fixer, gsd_doc_writer_review_md, gsd_code_fixer_review_fix_md, concept_3tier_verification [EXTRACTED 0.90]

## Communities

### Community 0 - "Shared Planning Artifacts"
Cohesion: 0.14
Nodes (26): Codebase Analysis Documents (.planning/codebase/), CONTEXT.md, PLAN.md, RESEARCH.md, ROADMAP.md, VERIFICATION.md, Claim Provenance (VERIFIED / CITED / ASSUMED tagging), CLAUDE.md (Project Instructions) (+18 more)

### Community 1 - "Code Review & Fix Pipeline"
Cohesion: 0.18
Nodes (12): 3-Tier Fix Verification Strategy, Atomic Per-Task Commit Protocol, GSD Code Fixer Agent, REVIEW-FIX.md (Code Fixer Output), GSD Code Reviewer Agent, REVIEW.md (Code Reviewer Output), GSD Executor Agent, /gsd-code-review Workflow (+4 more)

### Community 2 - "AI Eval & Domain Research"
Cohesion: 0.21
Nodes (12): Domain Rubric Ingredients, AI Eval Dimensions by System Type, GSD Domain Researcher Agent, ai-evals.md Reference (Domain Researcher), AI-SPEC.md Section 1b (Domain Context), GSD Eval Planner Agent, ai-evals.md Reference, AI-SPEC.md (Eval Planner Output) (+4 more)

### Community 3 - "Research & Discussion Phase"
Cohesion: 0.22
Nodes (11): Research Files (.planning/research/), SUMMARY.md (Research), Calibration Tier (full_maturity / standard / minimal_decisive), Context7 MCP Documentation Tool, Discuss Phase Orchestrator, Discuss Phase Assumptions Mode, New Project Orchestrator, GSD Advisor Researcher Agent (+3 more)

### Community 4 - "AI Integration Orchestration"
Cohesion: 0.24
Nodes (10): AI-SPEC.md, EVAL-REVIEW.md, AI Evals Reference (ai-evals.md), AI Frameworks Reference (ai-frameworks.md), AI Integration Phase Orchestrator, Eval Review Orchestrator, AI Systems Best Practices (Section 4b: Pydantic / Async / Prompt / Context / Cost), GSD AI Researcher Agent (+2 more)

### Community 5 - "UI Audit & Component Safety"
Cohesion: 0.24
Nodes (10): 6-Pillar UI Audit Framework, Registry Safety Vetting Gate, shadcn Initialization Gate, GSD UI Auditor Agent, UI-REVIEW.md (UI Auditor Output), GSD UI Researcher Agent, UI-SPEC.md (UI Researcher Output), /gsd-ui-phase Orchestrator (+2 more)

### Community 6 - "Security & Nyquist Auditing"
Cohesion: 0.22
Nodes (10): ASVS Levels (Security Standard), Nyquist Validation Gap Filling, SUMMARY.md (Executor Output), GSD Nyquist Auditor Agent, VALIDATION.md (Nyquist Output), GSD Security Auditor Agent, SECURITY.md (Security Auditor Output), Threat Model (PLAN.md block) (+2 more)

### Community 7 - "Intel Index Maintenance"
Cohesion: 0.22
Nodes (9): Intel File Schemas (files/apis/deps/stack/arch), GSD Intel Updater Agent, apis.json (Intel Output), arch.md (Intel Output), deps.json (Intel Output), files.json (Intel Output), Intel Files (.planning/intel/), stack.json (Intel Output) (+1 more)

### Community 8 - "Roadmap & Coverage Planning"
Cohesion: 0.29
Nodes (7): 100% Requirement Coverage Validation, Goal-Backward Thinking Methodology, GSD Roadmapper Agent, REQUIREMENTS.md (Roadmapper I/O), ROADMAP.md (Roadmapper Output), STATE.md (Roadmapper Output), /gsd-new-project Orchestrator

### Community 9 - "UI Pre-Execution Gate"
Cohesion: 0.5
Nodes (4): UI-SPEC.md, UI Spec Quality Dimensions (Copywriting / Color / Typography / Spacing / Registry Safety), UI Phase Orchestrator, GSD UI Checker Agent

### Community 10 - "Scientific Debugging"
Cohesion: 0.5
Nodes (4): Scientific Method Debugging Approach, GSD Debugger Agent, common-bug-patterns.md Reference, /gsd-debug Command

### Community 11 - "Integration Verification"
Cohesion: 0.67
Nodes (3): Cross-Phase Integration Verification, Milestone Auditor, GSD Integration Checker Agent

### Community 12 - "User Profiling"
Cohesion: 0.67
Nodes (3): GSD User Profiler Agent, 8 Behavioral Dimensions (User Profiling), user-profiling.md Reference

### Community 13 - "Documentation Writing"
Cohesion: 0.67
Nodes (3): Doc Tooling Adaptation (Docusaurus/VitePress/MkDocs), GSD Doc Writer Agent, /gsd-docs-update Workflow

### Community 14 - "Doc Verification"
Cohesion: 1.0
Nodes (2): Docs Update Workflow, GSD Doc Verifier Agent

## Knowledge Gaps
- **60 isolated node(s):** `Discuss Phase Orchestrator`, `Discuss Phase Assumptions Mode`, `UI Phase Orchestrator`, `Milestone Auditor`, `Docs Update Workflow` (+55 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **Thin community `Doc Verification`** (2 nodes): `Docs Update Workflow`, `GSD Doc Verifier Agent`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Context7 MCP Documentation Tool` connect `Research & Discussion Phase` to `Shared Planning Artifacts`, `AI Integration Orchestration`?**
  _High betweenness centrality (0.078) - this node is a cross-community bridge._
- **Why does `GSD AI Researcher Agent` connect `AI Integration Orchestration` to `Research & Discussion Phase`?**
  _High betweenness centrality (0.053) - this node is a cross-community bridge._
- **Why does `GSD Phase Researcher Agent` connect `Shared Planning Artifacts` to `Research & Discussion Phase`?**
  _High betweenness centrality (0.052) - this node is a cross-community bridge._
- **Are the 2 inferred relationships involving `GSD Verifier Agent` (e.g. with `CONTEXT.md` and `GSD Doc Verifier Agent`) actually correct?**
  _`GSD Verifier Agent` has 2 INFERRED edges - model-reasoned connections that need verification._
- **Are the 2 inferred relationships involving `GSD Phase Researcher Agent` (e.g. with `PLAN.md` and `GSD Assumptions Analyzer Agent`) actually correct?**
  _`GSD Phase Researcher Agent` has 2 INFERRED edges - model-reasoned connections that need verification._
- **What connects `Discuss Phase Orchestrator`, `Discuss Phase Assumptions Mode`, `UI Phase Orchestrator` to the rest of the system?**
  _60 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Shared Planning Artifacts` be split into smaller, more focused modules?**
  _Cohesion score 0.14 - nodes in this community are weakly interconnected._