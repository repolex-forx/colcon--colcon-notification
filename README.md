# Repolex Knowledge Graph of colcon/colcon-notification

RDF knowledge graph data for [colcon/colcon-notification](https://github.com/colcon/colcon-notification), parsed by [repolex](https://repolex.ai).

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
rlex download colcon/colcon-notification
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0401c0ed04e104e7693a9f697d6d4c027c338895
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 0401c0ed04e104e7693a9f697d6d4c027c338895
│           └── chunk-001.nq.gz
├── blob
│   ├── 0a4cb7d20f96ea893a41fc67a53467135e366bca.nq.gz
│   ├── 0f17157ed42b486a0c57cbffddd97987a4844e6b.nq.gz
│   ├── 326bb66d4c74f0cf8cf0dfc4e79909001f37da84.nq.gz
│   ├── 34861dbb658ca4124c9bb2ca7909528673839459.nq.gz
│   ├── 37b555be2b0ce37282f14483425f9224e021b432.nq.gz
│   ├── 3d7f0be347aee38f3326d748f598323c42e550ff.nq.gz
│   ├── 409bac4971e1f5d180e9c05d9adc40d636c01731.nq.gz
│   ├── 4272adb21421eb457649eb9a9dd587120c92cf81.nq.gz
│   ├── 443a37de80037589311d6011ded0dfbab47dd625.nq.gz
│   ├── 46576ef211d18155ae1997e26c209a97ff1ec7ec.nq.gz
│   ├── 599da6648cdddc6a77f92039dcacef39901edce7.nq.gz
│   ├── 5ba7b8a6c379b16ac6a483c2e5daaaac12500238.nq.gz
│   ├── 5e45963c382ba690b781b953a00585212b898ac5.nq.gz
│   ├── 6320088fd4dd126ab933194b2b1b388f80a78cfb.nq.gz
│   ├── 6344a81468c0d31d88911f220556ed6806c49b2b.nq.gz
│   ├── 72b33f3220f2c6e2882189eb8aa1a924cb1e0772.nq.gz
│   ├── 7fb129854299357003b3e2b3fb22c6ba6e5fc7d9.nq.gz
│   ├── 82b2dbd92bdeaa55592d3230451506ff3098fd95.nq.gz
│   ├── 9690fa3f7afbcbba03c61322a170b59f4e773d14.nq.gz
│   ├── a7f77465f3a3f171f71c9c670e2739fd8504deca.nq.gz
│   ├── acd45191295389d9e0f5de80b2ca765843ee84f7.nq.gz
│   ├── ad17860f800e3cb6eb93855ccf20a5ea337e841b.nq.gz
│   ├── b19d0fc34010160ff34b7016e7bb0ba30c7dc2d8.nq.gz
│   ├── b3e3c8d0d432d60f69b2cd4f94e4bf70d2419287.nq.gz
│   ├── b6acd8fc9b182ddc954de6a69eba8bedc4b40c63.nq.gz
│   ├── b746a8c5eb85c7d1dececfcc2532166b77e8ad88.nq.gz
│   ├── bd04210fb49f6032c3cd79559334dbe735a998ef.nq.gz
│   ├── c163ff6f098897703861d661f1f05edaffc33045.nq.gz
│   ├── c2db92100f02413693bbbc836267cbb0e0a5a529.nq.gz
│   ├── d645695673349e3947e8e5ae42332d0ac3164cd7.nq.gz
│   ├── dffe460f162da9929178a7ce342532e7ba896425.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ef7435015b961bc79f14ffa1a79ce3a208e99c21.nq.gz
│   ├── f4788bd5379283647e2ee55e37340a1228ba1eaa.nq.gz
│   └── fe0bf23fac3f3508282db0e8a86d2d770026b62b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 0401c0ed04e104e7693a9f697d6d4c027c338895.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 43 files
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

[colcon/colcon-notification](https://github.com/colcon/colcon-notification)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
