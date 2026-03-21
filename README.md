# debug2

A Rust Cargo workspace intended to provide debugging utilities by implementing program rewrites. Part of the [portal-co](https://github.com/portal-co) ecosystem.

## Current Status

**Early scaffolding. The workspace currently has no members and does not build.**

The `Cargo.toml` defines a virtual workspace (resolver v3) with shared dependency versions declared, but `members = []` is empty. The `crates/` directory contains only a placeholder file. There is no compilable code yet.

Running `cargo build` will fail with:

```
error: manifest path contains no package: The manifest is virtual, and the workspace has no members.
```

## What This Is Intended To Be

Based on the Cargo description ("Debugging for all by rewriting") and the declared dependencies, the project is set up to work with:

- **JavaScript/SWC compiler infrastructure** via the `portal-jsc-*` family of crates (`portal-jsc-common`, `portal-jsc-swc-cfg`, `portal-jsc-swc-tac`, `portal-jsc-swc-ssa`, `portal-jsc-swc-util`) from [portal-co/jsaw-core](https://github.com/portal-co/jsaw-core). These provide control-flow graph (CFG), three-address code (TAC), and static single assignment (SSA) representations over SWC's JavaScript AST.
- **WebAssembly toolchain** via `portal-pc-waffle` from [portal-co/waffle-](https://github.com/portal-co/waffle-), a fork/extension of the Waffle Wasm IR library.
- **Compiler intermediate representation utilities**: `ssa-traits`, `cfg-traits`, `ssa-impls`, `ssa-reloop` from [portal-co/codegen-utils](https://github.com/portal-co/codegen-utils). Both stable (0.2.x) and dev (0.3.x alpha) versions are declared as aliased dependencies.
- **SWC** (`swc_ecma_ast`, `swc_ecma_parser`, `swc_ecma_codegen`, `swc_ecma_minifier`, etc.) — the Rust-based JavaScript/TypeScript compiler.
- **`portal-solutions-swibb`** from [portal-co/swibb](https://github.com/portal-co/swibb).
- **`rayoff`** from [portal-co/rayoff](https://github.com/portal-co/rayoff).
- **`id-arena`** and **`arena-traits`** for arena-allocated data structures.

The intent appears to be building debugging passes or transformations over JavaScript/Wasm program representations using rewriting techniques on SSA/CFG IRs.

## Repository

- **Remote**: https://github.com/portal-co/debug2
- **License**: GPL-3.0
- **Version**: 0.1.0 (pre-release)

## Commit History

| Commit | Message |
|--------|---------|
| initial | clone from origin |
| update | general update |
| [AI] add readme skeleton | placeholder README added |
| [AI] add readme | README written by AI |
| add rust setup | Cargo workspace scaffolding added |
| gimme more | additional workspace dependency declarations |

## Structure

```
debug2/
├── Cargo.toml       # Virtual workspace root; no member crates yet
├── crates/
│   └── _            # Placeholder file; no crates implemented yet
├── LICENSE          # GPL-3.0
└── README.md
```

## Building

There is nothing to build at this time. Once crates are added to `members` in `Cargo.toml`, standard Cargo commands will apply:

```sh
cargo build
cargo test
```

All dependencies are sourced from private/pre-release git repositories in the portal-co GitHub organization and may require network access to those repositories.
