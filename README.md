# xkit

`xkit` is a Go-first utility module for common collection transforms and structural text operations.

The goal is not to outsmart the standard library or imitate functional languages for their own sake. The goal is to provide a small, well-tested set of helpers that show up constantly in real software work: manipulating slices, grouping and filtering data, editing text by range, and performing the kinds of find/replace and cursor-aware operations that are usually reimplemented ad hoc in every project.

At the end of the day, we're all processing excessive signals and text which require fast, consistent, reliable parsing, processing, and manipulation. This is an attempt to aggregate and commonditize things I've have to type many times over across many projects when doing text and data structure processing. Not because they are hard but because I am lazy.

This project exists for three reasons:

1. mechanisms for implementing canonical string operations cleanly in Go
2. reusable utility module for future projects
3. release practical open source package with stable semantics, strong tests, and clear performance expectations

---

## Design goals

- **Go-first**: idiomatic naming, explicit semantics, minimal magic
- **Small surface area**: only useful, high-frequency operations
- **Composable primitives**: a few strong building blocks instead of endless one-offs
- **Clear behavior**: mutation vs copy is explicit
- **Well-tested**: table-driven tests, edge cases, benchmarks
- **Generic where it helps**: use generics for slices and maps without turning the API into abstraction soup

---

## Project status

This repository is currently in active design and implementation.

The initial release target is **v1**, which focuses on two major areas:

- `coll`: collection and slice helpers
- `textx`: structural text and string editing helpers

The intent is for `v1` to feel stable, useful, and small enough to trust.

---

## Package layout

```text
xkit/
├── coll/      # collection, slice, and map helpers
├── textx/     # text ranges, find/replace, cursor-aware string ops
└── internal/  # internal test or support utilities as needed
```

## Why this project exists

Go gives you a great standard library and now includes some useful slices and maps support. But there is still a meaningful gap between:

- raw slice manipulation with append, copy, and indexing
- higher-level operations that many real programs need repeatedly

The same is true for strings and text editing. Many projects eventually need to do things like:

- insert text at an offset
- delete or replace a range
- replace words only at real word boundaries
- edit text inside quotes or brackets
- split, chunk, partition, and group data structures in predictable ways

Those operations are common enough to deserve clean implementations, but specific enough that they often end up scattered through codebases as one-off helpers. xkit aims to centralize those into a coherent, documented module.


