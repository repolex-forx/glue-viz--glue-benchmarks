# Repolex Knowledge Graph of glue-viz/glue-benchmarks

RDF knowledge graph data for [glue-viz/glue-benchmarks](https://github.com/glue-viz/glue-benchmarks), parsed by [repolex](https://repolex.ai).

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
rlex download glue-viz/glue-benchmarks
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5af97115b6951e97ce21c386f5a6918acc188fb1
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5af97115b6951e97ce21c386f5a6918acc188fb1
│           └── chunk-001.nq.gz
├── blob
│   ├── 499ab53b506bf90650b4a50529ab083b655c24f3.nq.gz
│   ├── 599e661c083d32e602c09bee077734247fa5259b.nq.gz
│   ├── 60bb53c401384bd736c9942d58eac0cbddafe0bd.nq.gz
│   ├── 639ae5e8989d66936083977bef009e0b63e679b8.nq.gz
│   ├── 6ff887d241e427ebb1c60acbdfb8069bdb370764.nq.gz
│   ├── 8b0a7b8de1f1c18c9e9c5d913aab387f981cef82.nq.gz
│   ├── 8b137891791fe96927ad78e64b0aad7bded08bdc.nq.gz
│   ├── cc9ee944e3bdec464205d55e8150780146b45bf2.nq.gz
│   └── fea2474732b9c62104770fff13b0b91ba165d9e8.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5af97115b6951e97ce21c386f5a6918acc188fb1.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 15 files
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

[glue-viz/glue-benchmarks](https://github.com/glue-viz/glue-benchmarks)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
