# itrace

[![Crates.io](https://img.shields.io/crates/v/itrace.svg)](https://crates.io/crates/itrace)
[![Docs.rs](https://docs.rs/itrace/badge.svg)](https://docs.rs/itrace)
[![Rust](https://img.shields.io/badge/rust-1.85%2B-orange.svg)](https://www.rust-lang.org)
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](LICENSE)

A configurable **columnar terminal tracer** for Rust.

> **Scope note** — this crate was built for personal use in my own projects.
> It has no ambition to become a widely adopted library: there are far more
> mature and feature-rich crates in the Rust ecosystem for structured logging
> (e.g. [`tracing`], [`log`], [`env_logger`]).  Maintenance is best-effort.
> That said, you are of course welcome to use it if it fits your needs.

Define any number of named columns with individual ANSI colours and widths using
the `#[itracer]` proc-macro attribute.  A typed entry-builder is generated
automatically — one method per column — so call sites are concise and
refactor-safe.  Optionally integrates with [`tracing_subscriber`] as a drop-in
event formatter (feature `tracing`).  Log levels and colours can be tuned at
runtime without recompiling via a TOML file in `~/.config/itrace/` (feature
`tracer-file`).

## Output format

```
 I  14:49:55.743834Z     myapp      eu-west-1    node-01    Server started
 ^  └──────────────┘  └─────────┘  └─────────┘  └───────┘  └────────────┘
 │      timestamp       col 1        col 2         col 3       message
 │
 └─ level badge (1 char, coloured background)
    I = green   W = orange   E = red   D = blue   T = pink
```

- The **level badge** and **timestamp** are always present.
- All other columns are user-defined.
- Columns whose value is not supplied render as blank spaces, preserving
  alignment of the columns that follow.
- Extra `key=value` pairs can be appended after the message.

## Quick start

Add to `Cargo.toml`:

```toml
[dependencies]
itrace = { version = "0.1", features = ["derive"] }
```
... TODO!

## Minimum Supported Rust Version

**1.85** (Rust 2024 edition).

## License

Licensed under the [BSD 3-Clause license](LICENSE).
