# node-redis issue screenshots

Screenshots referenced by node-redis issue/PR reports.

## `xrange-count-zero/`

Debugger evidence for `XRANGE`/`XREVRANGE` dropping `{ COUNT: 0 }`.

| File | Shows |
|---|---|
| `01-breakpoint-hit-XRANGE-ts-29.png` | Breakpoint hit on `XRANGE.ts:29`; `options = {COUNT: 0}`, `args = (2) ['-', '+']` |
| `02-stepped-past-if-args-unchanged.png` | After stepping past the `if`, `args` is still `(2) ['-', '+']` |
| `03-control-count-2-args-pushed.png` | Control: `COUNT: 2` takes the branch, `args = (4) ['-', '+', 'COUNT', '2']` |
| `04-terminal-ab-mismatch.png` | Terminal A/B: typed `3 entries` vs raw wire `null` |
