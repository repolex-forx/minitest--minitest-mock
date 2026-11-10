# Repolex Knowledge Graph of minitest/minitest-mock

RDF knowledge graph data for [minitest/minitest-mock](https://github.com/minitest/minitest-mock), parsed by [repolex](https://repolex.ai).

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
rlex download minitest/minitest-mock
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f4656e5a923d8c11aa64678f2eacbfb009fc84fd
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f4656e5a923d8c11aa64678f2eacbfb009fc84fd
│           └── chunk-001.nq.gz
├── blob
│   ├── 6bf327c6b197f3f6d235497de7373db8a24170af.nq.gz
│   ├── 70aedacb12a3316f0b68062d1d22be2254a90952.nq.gz
│   ├── 8a52e2fd85fa1c35c1d9cbeed4d4b6229e37c2aa.nq.gz
│   ├── 936f8ec88e3f0cd1ee58483838aeebe80fd48e32.nq.gz
│   ├── 9c79668ecb6987bf3fc0c61da8dc66a976dea6c2.nq.gz
│   ├── b183cfa22ec88b7de0c9180bc4e8ed0ace6e52f0.nq.gz
│   ├── cace5e84dc7970ba2d284d4fae41351598304647.nq.gz
│   ├── e1535cd87d763ece9b64fe13fb69e8f574bdfc6d.nq.gz
│   └── fde506d46c6d80ba7d0ce59fa02bf5219dfe3890.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f4656e5a923d8c11aa64678f2eacbfb009fc84fd.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
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

[minitest/minitest-mock](https://github.com/minitest/minitest-mock)

---
*Parsed on 2026-11-10 by [repolex](https://repolex.ai)*
