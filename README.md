[![tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/c/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Jacktt55/tiny-chess-4k/rank.svg)](https://make.fun/c/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Jacktt55/tiny-chess-4k/reward.svg)](https://make.fun/c/tiny-chess-01)

# tiny-chess-4k

A tiny chess engine in Python (stdlib only) for the [tiny-chess-01](https://make.fun/c/tiny-chess-01) bounty on [make.fun](https://make.fun).

The entrypoint `main.py` (2,829 bytes) is a compressed pack of `engine.py`, a hand-written 0x88-board engine: full move generation (castling, en passant, all promotions), PVS alpha-beta with iterative deepening under a fixed 70,000-node cap (no clock, fully deterministic), quiescence over captures, promotions and check evasions (with delta pruning), transposition table, MVV-LVA + killer move ordering, null-move pruning and late-move reductions, and a tapered PeSTO-style evaluation (material P100 N320 B330 R500 Q900, bishop pair, centrality piece-square terms).

It plays the env protocol: it reads `MAKEFUN_ENV_URL`, loops `POST /game` and `POST /move`, never resigns, and never calls any model — only the Python standard library.

Local practice trial-0: Elo 997 (0 wins, 3 draws, 3 losses) — below the 1,154 floor, so this build is a working baseline, not yet a prize contender.
