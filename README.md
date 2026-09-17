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

## `keyprefix-raw-sendcommand/`

Debugger evidence for `keyPrefix` not being applied on the raw `sendCommand` path.

| File | Shows |
|---|---|
| `01-typed-path-injects-keyPrefix-index362.png` | Typed path builds its parser with `this._self._keyPrefix` (`index.ts:362`) |
| `02-typed-sendCommand-args-prefixed.png` | Typed path reaching `sendCommand` with `['SET','APP:typed-key','v']` |
| `03-raw-sendCommand-args-NOT-prefixed.png` | Raw path reaching the same `sendCommand` with `['SET','raw-key','v']` - no prefix, while `_keyPrefix` is `'APP:'` |
| `04-terminal-node-redis-vs-ioredis.png` | Server keys: `['raw-key','APP:typed-key']` vs ioredis `['APP:typed-key','APP:raw-key']` |
