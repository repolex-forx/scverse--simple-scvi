# Repolex Knowledge Graph of scverse/simple-scvi

RDF knowledge graph data for [scverse/simple-scvi](https://github.com/scverse/simple-scvi), parsed by [repolex](https://repolex.ai).

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
rlex download scverse/simple-scvi
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3841a763d6d9e2e9a1f18c32165465a23de4f2b6
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 3841a763d6d9e2e9a1f18c32165465a23de4f2b6
│           └── chunk-001.nq.gz
├── blob
│   ├── 00ad6a6ea9418df96256615a564065e38c8332ea.nq.gz
│   ├── 024294339a217956a3e351b03434eb7da67ebcac.nq.gz
│   ├── 0a89d3a5438fdc2e82d5f762a77782af429612f6.nq.gz
│   ├── 0b6823810b58c08ac844df06d1f2ee6b5471770d.nq.gz
│   ├── 104483fe069c14e3e16793a7a6d0ff542c883cb9.nq.gz
│   ├── 17dc123c42c4c5f33deb67332a339d6f610d2052.nq.gz
│   ├── 192854ebde442a65c1e506d74e3369bc8df1c2bc.nq.gz
│   ├── 1bf39152d5e0e14d38724e23729f01e6c7958b36.nq.gz
│   ├── 1cf9e0323b50ff356b2ce3c3a94cb9af1d32715b.nq.gz
│   ├── 28bf53497a7995004175f342a331837533f110e7.nq.gz
│   ├── 2a2319b1db7d2084d11da2bf3bc40c7a3325ee27.nq.gz
│   ├── 2f0ffd7a7e0871c846a3f69e0d65096f94fedb66.nq.gz
│   ├── 2fe0ce08508c7246d98b6bf8dbc96f0921f825f5.nq.gz
│   ├── 38dc6e55643fb92f2f7578c4b53bc76a54e6dd7e.nq.gz
│   ├── 46aa14d436203d7a6fb23c0d76d46f407c230d78.nq.gz
│   ├── 521949922770e5f728058ca03f987474dedc7d00.nq.gz
│   ├── 5cad625d1a31612703f1770f7bca4d21451c21a5.nq.gz
│   ├── 69182b68ef89a312275307945896526309f2b03c.nq.gz
│   ├── 69cc50d572eb67302bee02ec3ab41703a339f626.nq.gz
│   ├── 76e4059784e08d54701cf278a498000212d90b03.nq.gz
│   ├── 7bb0bd5ee38636c2fe9d35f6c78a1b65328806b5.nq.gz
│   ├── 829e56c03f07f32950461db65f93a14babeaed12.nq.gz
│   ├── 944781302c2b5bbcce5a7870367e6d6cf2057c07.nq.gz
│   ├── 954237b9b9f2b248bb1397a15c055c0af1cad03e.nq.gz
│   ├── 9d7f197083ae7a8413fbbaa403641a74511423a2.nq.gz
│   ├── 9dfd4acb5b45aa3179c4f995461ac6bb1b8ecff9.nq.gz
│   ├── ad6f412920028041e0ef04afea6e403ad66c8006.nq.gz
│   ├── c2cd87318ad5772d309ec231f67300b9a65d81e2.nq.gz
│   ├── c5e33829650f9084ec969ce885dcef4f52cf69ce.nq.gz
│   ├── d4bb2cbb9eddb1bb1b4f366623044af8e4830919.nq.gz
│   ├── d9e79ba64848091a9bccd21dc241c61c669dad7f.nq.gz
│   ├── e3593b26b6cbbc43c3edd4b6507f1a39ad7ebeb3.nq.gz
│   ├── e425235e2eafb305328bc9364808cbcc4c1844d0.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e7b78085019d5f4fec580af56dadf043320ebb4a.nq.gz
│   ├── f3041183ae3b40a75f5043be14696a37c53ba373.nq.gz
│   └── fdba9e4f69423506c4297fe00716a7f76a684f8e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 3841a763d6d9e2e9a1f18c32165465a23de4f2b6.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 45 files
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

[scverse/simple-scvi](https://github.com/scverse/simple-scvi)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
