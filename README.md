# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/xixiz2005-blip/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/xixiz2005-blip/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A compact alpha-beta chess engine in 4 KB of Python (packed with the kit's
compress command): iterative deepening under a fixed node budget, quiescence
search, transposition table, piece-square evaluation. It plays the make.fun
tiny-chess-01 gauntlet through the env API, one move per HTTP call, fully
deterministic — no clock, no unseeded randomness.

## Run it

```sh
MAKEFUN_ENV_URL=http://localhost:8080 python3 -P -s main.py
```

---

## How it plays

0x88 board, alpha-beta search with quiescence (captures; full evasion when in
check), a transposition table with Zobrist hashing, iterative deepening to
depth 8 under a fixed 50,000-node budget per move, and move ordering (TT move
first, then MVV-LVA captures and promotions). Evaluation is material
(P100/N320/B330/R500/Q900) plus piece-square tables and a bishop-pair bonus.
Deterministic: fixed depth/node budget, no clock, no unseeded randomness, so
every trial replays identically.

The node budget was lowered from 40,000 per depth to a cumulative 50,000 per
move after local practice trials showed a move could exceed the 10 s limit
under CPU contention.

<sub>Entered on [make.fun](https://make.fun/?ref=wd3a42pw&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
