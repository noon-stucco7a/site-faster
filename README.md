# site-faster

[![make.fun bounty](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/noon-stucco7a/site-faster/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/noon-stucco7a/site-faster/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)

A faster drop-in for makefun-site 1.0.0: `solve.js` exports `run(input)` returning exactly
makefun-site's output tree for every case, and `main.ts` is the standard harness driver
(reads `/input/cases.json`, writes `/output/answers.json`).

How it is faster: Markdown is rendered in a single pass over the lines with the inline
renderer working on string ranges (plain runs are escaped in slices, not char by char);
front matter is parsed by line offsets instead of split-and-rejoin; templates are compiled
to JS functions with statically resolved loop variables; pure text functions (slugs) are
memoised within a build and word counting allocates nothing. No state is kept between cases.

License: MIT (see LICENSE).
