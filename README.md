[![tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/c/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Jacktt55/tiny-chess-4k/rank.svg)](https://make.fun/c/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Jacktt55/tiny-chess-4k/reward.svg)](https://make.fun/c/tiny-chess-01)

# tiny-chess-4k

A chess engine in 4,004 bytes of Python (stdlib only) for the [tiny-chess-01](https://make.fun/c/tiny-chess-01) bounty on [make.fun](https://make.fun).

`main.py` is a compressed pack of `engine.py` (kept out of the snapshot): an original 0x88-board engine with full legal move generation (castling, en passant, all promotions), negamax alpha-beta with iterative deepening under a fixed 65,000-node cap (no clock, fully deterministic), quiescence search over captures/promotions with check evasions and delta pruning, transposition table, MVV-LVA + killer move ordering, check extensions, null-move pruning, and a tapered piece-square evaluation (material P100 N320 B330 R500 Q900, bishop pair, centrality and advancement terms).

It plays the env protocol: reads `MAKEFUN_ENV_URL`, loops `POST /game` and `POST /move`, never resigns, never calls any model. Movegen verified by perft (start position and kiwipete through depth 3: 8,902 / 97,862 nodes exact).

Local practice trial-0: Elo 1364 (3 wins, 1 draw, 2 losses) — beats depth-2, depth-3 and nodes-100k, draws depth-4, loses to nodes-250k and nodes-500k. Above the 1,154 final floor.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>