# kdl-schema (ARCHIVED)

> ## ⚠️ This repository has moved
>
> All packages from `kdl-schema` were absorbed into **[chronista-club/chronista-hub](https://github.com/chronista-club/chronista-hub)** as `packages/*` on **2026-04-25**, following the monorepo consolidation strategy.
>
> Active development continues there. This repo is kept as a historical reference (archived = read-only).
>
> ### New locations
>
> | Old | New |
> |---|---|
> | `chronista-club/kdl-schema/packages/kdl-parser` | `chronista-club/chronista-hub/packages/kdl-parser` |
> | `chronista-club/kdl-schema/packages/codegen-ts` | `chronista-club/chronista-hub/packages/codegen-ts` |
> | `chronista-club/kdl-schema/packages/codegen-zod` | `chronista-club/chronista-hub/packages/codegen-zod` |
> | `chronista-club/kdl-schema/packages/codegen-surql` | `chronista-club/chronista-hub/packages/codegen-surql` |
> | `chronista-club/kdl-schema/packages/codegen-rust` | `chronista-club/chronista-hub/packages/codegen-rust` |
> | `chronista-club/kdl-schema/packages/cli` | `chronista-club/chronista-hub/packages/cli` |
>
> Hub root scripts: `bun run gen | gen:ts | gen:zod | gen:surql` (all in chronista-hub now).
>
> Reference: [chronista-hub PR #7](https://github.com/chronista-club/chronista-hub/pull/7) absorbed all packages on 2026-04-25.

---

KDL spec → TypeScript / Zod / Rust / SurrealQL codegen tool for the Chronista ecosystem.

## 何

`.kdl` で記述されたスキーマから、 各言語・各 stack の型定義 / validator / migration を自動生成する codegen tool。 Chronista Hub の World Tree spec (`chronista-hub/docs/spec/world-tree.kdl`) を第一の consumer とする。

## 設計原則 (memory: `config-dsl-pattern-learnings.md`)

- **KDL を spec primary** — data-code 分離、 host-language DSL 勝利則
- **Emit targets**: TypeScript interface / Zod schema / Rust struct / SurrealQL DEFINE 文 (+ 将来 Python / Ruby)
- **Single source of truth** — 1 KDL file から多 target 生成、 drift 検出 CI も範囲に含める

## Status

- **Phase 0** — 独立 repo 切り出し ([CREO-123](https://linear.app/chronista/issue/CREO-123) 相当)
- **Phase 1** — baseline scaffold (本 commit)
- **Phase 2** (後続) — KDL parser + AST ([CREO-123](https://linear.app/chronista/issue/CREO-123))
- **Phase 3** (後続) — TS + Zod emit ([CREO-124](https://linear.app/chronista/issue/CREO-124))
- **Phase 4** (後続) — Rust + SurrealQL emit ([CREO-125](https://linear.app/chronista/issue/CREO-125))

## Development

```bash
bun install
bun run typecheck
bun run check
bun test
```

## Workspace layout (想定)

```
kdl-schema/
└── packages/
    ├── kdl-parser/      (future: KDL → AST)
    ├── kdl-codegen-ts/  (future: AST → TypeScript)
    ├── kdl-codegen-zod/ (future: AST → Zod schema)
    ├── kdl-codegen-rust/  (future: AST → Rust struct)
    └── kdl-codegen-surql/ (future: AST → SurrealQL DEFINE)
```

## Related

- Upstream spec: [`chronista-club/chronista-hub`](https://github.com/chronista-club/chronista-hub) — 本 tool の primary consumer
- Design memory (creo-memories 内): `config-dsl-pattern-learnings.md` / `chronista-repo-topology.md`

## License

TBD
