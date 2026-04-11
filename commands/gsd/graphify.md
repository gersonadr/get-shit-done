---
name: gsd:graphify
description: Build a queryable knowledge graph from any folder of code, docs, images, or videos
argument-hint: "[path] [--update|--query <question>|--mode deep]"
allowed-tools:
  - Read
  - Bash
  - Grep
  - Glob
  - AskUserQuestion
---
<objective>
Turn any folder of files into a navigable knowledge graph with community detection and three
outputs: interactive HTML, GraphRAG-ready JSON, and a plain-language GRAPH_REPORT.md.

Accepts an optional path argument and flags:

- `/gsd-graphify`                  — process the current directory
- `/gsd-graphify ./src`            — process a specific folder
- `/gsd-graphify --update`         — incrementally update an existing graph
- `/gsd-graphify --query "how does auth work?"` — query the existing graph
- `/gsd-graphify --mode deep`      — thorough extraction, richer inferred edges
</objective>

<prerequisites>
graphify must be installed: `pip install graphifyy`
</prerequisites>

<process>

## Step 1 — Check installation

```bash
python3 -m graphify --version 2>/dev/null || graphify --version 2>/dev/null || echo "NOT_INSTALLED"
```

If NOT_INSTALLED, inform the user:
```
graphify is not installed. Run:

  pip install graphifyy

Then retry /gsd-graphify.
```
Stop.

## Step 2 — Parse arguments

Parse `$ARGUMENTS`:

| Pattern | Action |
|---------|--------|
| `--query <question>` | Run query mode (Step 5) |
| `--update` | Incremental update (Step 4, add --update flag) |
| `--mode deep` | Full pipeline with deep mode (Step 4) |
| `<path>` (no flags) | Full pipeline on path (Step 4) |
| (empty) | Full pipeline on current directory (Step 4) |

## Step 3 — Show banner

```
GSD > GRAPHIFY
```

## Step 4 — Build the graph

Determine the target path (default: `.`).

Run:
```bash
graphify <path> [flags]
```

On completion, check that `graphify-out/GRAPH_REPORT.md` exists:
```bash
ls -la graphify-out/
```

Display a summary:
```
Knowledge graph built.

Outputs in graphify-out/:
  GRAPH_REPORT.md  — plain-language overview, god nodes, communities
  graph.html       — interactive visualization (open in browser)
  graph.json       — GraphRAG-ready JSON for queries

---

Next steps:
  /gsd-graphify --query "how does X work?"  — query the graph
  /gsd-graphify --update                    — rebuild after code changes
  open graphify-out/graph.html              — explore visually
```

**STOP** after displaying the summary.

## Step 5 — Query mode

Extract the question from `$ARGUMENTS` (everything after `--query`).

Run:
```bash
graphify query "<question>"
```

Display the answer verbatim.

**STOP** after displaying the answer.

</process>

<success_criteria>
- graphify-out/GRAPH_REPORT.md exists after build
- graph.html and graph.json also exist
- User shown clear next steps
</success_criteria>
