# Repolex Knowledge Graph of PyCQA/mccabe-console-script

RDF knowledge graph data for [PyCQA/mccabe-console-script](https://github.com/PyCQA/mccabe-console-script), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download PyCQA/mccabe-console-script
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 148fc6755e5b148eafa82aa3c4700b72bd035322
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 148fc6755e5b148eafa82aa3c4700b72bd035322
│           └── chunk-001.nq.gz
├── blob
│   ├── 0a774e0cff13f358b1c5c2a9a53efc8e67951dbf.nq.gz
│   ├── 4107b4f4799e257ab548f7cd251d00c4f082cd69.nq.gz
│   ├── 6214798659db3b683ccb3a5f1fd11f1cd4bec0ab.nq.gz
│   └── 8dce522c412087ff69f1d561eebfc320234b0f0f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 148fc6755e5b148eafa82aa3c4700b72bd035322.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 10 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[PyCQA/mccabe-console-script](https://github.com/PyCQA/mccabe-console-script)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
