# Graph Report - hooks  (2026-04-16)

## Corpus Check
- Corpus is ~3,643 words - fits in a single context window. You may not need a graph.

## Summary
- 48 nodes · 54 edges · 14 communities detected
- Extraction: 94% EXTRACTED · 6% INFERRED · 0% AMBIGUOUS · INFERRED: 3 edges (avg confidence: 0.82)
- Token cost: 0 input · 0 output

## God Nodes (most connected - your core abstractions)
1. `GSD Statusline Hook` - 12 edges
2. `GSD Context Monitor Hook` - 11 edges
3. `GSD Workflow Guard Hook` - 9 edges
4. `GSD Prompt Injection Guard Hook` - 8 edges
5. `GSD Check Update Hook` - 7 edges
6. `GSD Read Guard Hook` - 6 edges
7. `MANAGED_HOOKS List (canonical set of GSD hooks)` - 6 edges
8. `Shared additionalContext Output Pattern (hook injects agent-visible text)` - 4 edges
9. `Shared .planning/ Directory (GSD state store)` - 3 edges
10. `readGsdState()` - 2 edges

## Surprising Connections (you probably didn't know these)
- `GSD Prompt Injection Guard Hook` --semantically_similar_to--> `GSD Workflow Guard Hook`  [INFERRED] [semantically similar]
  hooks/gsd-prompt-guard.js → hooks/gsd-workflow-guard.js
- `GSD Prompt Injection Guard Hook` --semantically_similar_to--> `GSD Read Guard Hook`  [INFERRED] [semantically similar]
  hooks/gsd-prompt-guard.js → hooks/gsd-read-guard.js
- `GSD Workflow Guard Hook` --semantically_similar_to--> `GSD Read Guard Hook`  [INFERRED] [semantically similar]
  hooks/gsd-workflow-guard.js → hooks/gsd-read-guard.js
- `GSD Statusline Hook` --shares_data_with--> `GSD Context Monitor Hook`  [EXTRACTED]
  hooks/gsd-statusline.js → hooks/gsd-context-monitor.js
- `GSD Statusline Hook` --shares_data_with--> `GSD Check Update Hook`  [EXTRACTED]
  hooks/gsd-statusline.js → hooks/gsd-check-update.js

## Hyperedges (group relationships)
- **PreToolUse Advisory Guard Pattern** — gsd_promptguard_hook, gsd_readguard_hook, gsd_workflowguard_hook [EXTRACTED 0.95]
- **Hooks that Read .planning/ for GSD State** — gsd_contextmonitor_hook, gsd_workflowguard_hook, gsd_statusline_hook [EXTRACTED 0.90]
- **Hooks that Inject additionalContext into Agent** — gsd_contextmonitor_hook, gsd_promptguard_hook, gsd_readguard_hook, gsd_workflowguard_hook [EXTRACTED 0.95]

## Communities

### Community 0 - "Statusline State Reader"
Cohesion: 0.29
Nodes (7): Rationale: AUTO_COMPACT_BUFFER_PCT normalizes context usage to exclude reserved buffer, formatGsdState Function, GSD Statusline Hook, parseStateMd Function, readGsdState Function, Rationale: session ID path-traversal sanitization prevents writing outside tmpdir, Rationale: stdin timeout guard prevents hang on pipe issues (Windows/Git Bash)

### Community 1 - "Context Monitor & Bridge"
Cohesion: 0.29
Nodes (7): Rationale: advisory-only warnings avoid overriding user preferences (see #884), Context Critical Threshold (remaining <= 25%), Context Monitor Debounce (5 tool calls between warnings), GSD Context Monitor Hook, Context Warning Threshold (remaining <= 35%), Context Bridge File (/tmp/claude-ctx-{session}.json), Shared .planning/STATE.md (GSD workflow state)

### Community 2 - "Update Checker & Config Detection"
Cohesion: 0.33
Nodes (6): detectConfigDir Function (multi-runtime support), GSD Check Update Hook, isNewer Semver Comparison Function, Rationale: only check MANAGED_HOOKS to ignore orphaned files from removed features (#1750), Rationale: shared ~/.cache/gsd/ avoids multi-runtime cache resolution mismatches (#1421), GSD Update Cache File (~/.cache/gsd/gsd-update-check.json)

### Community 3 - "Statusline Hook (AST)"
Cohesion: 0.5
Nodes (2): parseStateMd(), readGsdState()

### Community 4 - "Prompt Injection Guard"
Cohesion: 0.4
Nodes (5): Rationale: advisory-only to prevent false-positive deadlocks on legitimate workflow operations, GSD Prompt Injection Guard Hook, Prompt Injection Detection Patterns, Invisible Unicode Character Detection, Shared .planning/ Directory (GSD state store)

### Community 5 - "Workflow Path Guard"
Cohesion: 0.4
Nodes (5): Workflow Guard Allowed File Patterns (config/docs exempt), Rationale: disabled by default (workflow_guard: false) to avoid friction in non-strict projects, GSD Workflow Guard Hook, Rationale: soft guard (advisory not block) so edits still proceed while nudging GSD usage, Shared .planning/config.json (GSD hook configuration)

### Community 6 - "Read Guard & Managed Hooks"
Cohesion: 0.4
Nodes (5): MANAGED_HOOKS List (canonical set of GSD hooks), Rationale: skip advisory for Claude Code which natively enforces read-before-edit (#1984), GSD Read Guard Hook, Rationale: prevents infinite retry loop on non-Claude models that skip read-before-edit, Shared additionalContext Output Pattern (hook injects agent-visible text)

### Community 7 - "Update Checker (AST)"
Cohesion: 1.0
Nodes (0): 

### Community 8 - "Context Monitor (AST)"
Cohesion: 1.0
Nodes (0): 

### Community 9 - "Prompt Guard (AST)"
Cohesion: 1.0
Nodes (0): 

### Community 10 - "Read Guard (AST)"
Cohesion: 1.0
Nodes (0): 

### Community 11 - "Workflow Guard (AST)"
Cohesion: 1.0
Nodes (0): 

### Community 12 - "GSD-Aware Warning Message"
Cohesion: 1.0
Nodes (1): GSD-Aware Context Warning Message (references STATE.md)

### Community 13 - "Non-GSD Warning Message"
Cohesion: 1.0
Nodes (1): Non-GSD Context Warning Message

## Knowledge Gaps
- **24 isolated node(s):** `readGsdState Function`, `parseStateMd Function`, `formatGsdState Function`, `Rationale: AUTO_COMPACT_BUFFER_PCT normalizes context usage to exclude reserved buffer`, `Rationale: stdin timeout guard prevents hang on pipe issues (Windows/Git Bash)` (+19 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **Thin community `Update Checker (AST)`** (2 nodes): `gsd-check-update.js`, `detectConfigDir()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Context Monitor (AST)`** (1 nodes): `gsd-context-monitor.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Prompt Guard (AST)`** (1 nodes): `gsd-prompt-guard.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Read Guard (AST)`** (1 nodes): `gsd-read-guard.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Workflow Guard (AST)`** (1 nodes): `gsd-workflow-guard.js`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `GSD-Aware Warning Message`** (1 nodes): `GSD-Aware Context Warning Message (references STATE.md)`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Non-GSD Warning Message`** (1 nodes): `Non-GSD Context Warning Message`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `GSD Statusline Hook` connect `Statusline State Reader` to `Context Monitor & Bridge`, `Update Checker & Config Detection`, `Read Guard & Managed Hooks`?**
  _High betweenness centrality (0.215) - this node is a cross-community bridge._
- **Why does `MANAGED_HOOKS List (canonical set of GSD hooks)` connect `Read Guard & Managed Hooks` to `Statusline State Reader`, `Context Monitor & Bridge`, `Update Checker & Config Detection`, `Prompt Injection Guard`, `Workflow Path Guard`?**
  _High betweenness centrality (0.182) - this node is a cross-community bridge._
- **Why does `GSD Context Monitor Hook` connect `Context Monitor & Bridge` to `Statusline State Reader`, `Prompt Injection Guard`, `Workflow Path Guard`, `Read Guard & Managed Hooks`?**
  _High betweenness centrality (0.170) - this node is a cross-community bridge._
- **Are the 2 inferred relationships involving `GSD Workflow Guard Hook` (e.g. with `GSD Prompt Injection Guard Hook` and `GSD Read Guard Hook`) actually correct?**
  _`GSD Workflow Guard Hook` has 2 INFERRED edges - model-reasoned connections that need verification._
- **Are the 2 inferred relationships involving `GSD Prompt Injection Guard Hook` (e.g. with `GSD Workflow Guard Hook` and `GSD Read Guard Hook`) actually correct?**
  _`GSD Prompt Injection Guard Hook` has 2 INFERRED edges - model-reasoned connections that need verification._
- **What connects `readGsdState Function`, `parseStateMd Function`, `formatGsdState Function` to the rest of the system?**
  _24 weakly-connected nodes found - possible documentation gaps or missing edges._