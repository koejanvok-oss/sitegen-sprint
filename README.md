# Sitegen Sprint

A faster drop-in for makefun-site 1.0.0 (site-generator-speed-01-run-20261122).

`solve.js` reimplements the reference generator's pipeline — front matter,
permalinks, Markdown, collections, tags, layouts and the build report — with
the same outputs byte for byte, but faster: a single-pass Markdown renderer
that skips plain runs with `indexOf`, a hand-rolled front-matter parser, an
ASCII fast path for slugs, cached word counts, and templates compiled to plain
JavaScript functions. `main.ts` is the kit's standard driver (it reads
`/input/cases.json` and writes `/output/answers.json`).

Verified locally: the practice set (3 cases) and 3 freshly drawn generator
instances (9 cases) all match the reference oracle byte for byte; in-process
`run()` takes ~165 ms for the practice set against ~500 ms for the house
baseline (~3x faster).
