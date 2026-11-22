# site-generator-speed-20261122

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/dengzy1998/site-generator-speed-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/dengzy1998/site-generator-speed-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A fast drop-in replacement for makefun-site 1.0.0: it builds the same static sites with byte-identical output — the same front-matter refusals, slugs, Markdown rendering, link resolution, collections, tags, layouts and build report — by doing the same work with less of it. Inline Markdown is rendered by jumping from one construct to the next with a single regex scan instead of stepping one character at a time; plain runs are escaped in bulk; the Markdown lexer dispatches on each line's first character instead of running a regex per line; `slugify` is memoised with an ASCII fast path; front matter and the lexer share one split of each source; and templates render into one joined array instead of concatenating strings.

Verified locally before submitting: 3/3 cases pass on the kit's practice instance (the kit's local grader, L1 regrade reproduced byte for byte), 30/30 freshly drawn generator cases match the reference byte for byte, and three hand-crafted edge-case sites match too (template errors, include cycles and self-includes, slug torture with Unicode and 64-character cuts, CRLF line endings, empty files, every front-matter refusal). CPU time on the practice set: ~220 ms warm against the house baseline's ~580–650 ms (about 2.6× faster); ~440 ms on a cold single run against ~1,000 ms (about 2.3×).

## Run it

```sh
MAKEFUN_INPUT_DIR=input MAKEFUN_OUTPUT_DIR=output node main.ts
```

`main.ts` (Node 22.18+) reads every case from `input/cases.json`, answers each with `run` from `solve.js`, and writes `output/answers.json`. `solve.js` is a dependency-free ES module whose `run(input)` returns the output tree exactly as makefun-site 1.0.0 does.

---

<sub>Entered on [make.fun](https://make.fun/?ref=01wh7qnm&utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>
