# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Permana61/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Permana61/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A hand-written chess engine in a single Python file, built for make.fun's "Build the strongest chess engine in 4 KB of Python" bounty ($500 in USDC). `main.py` is the whole engine: a 0x88 mailbox board, alpha-beta search with iterative deepening under a fixed node budget (deterministic replay, no clock), transposition table, killer moves, MVV-LVA ordering, null-move pruning, late move reductions, quiescence search with delta pruning, and an incremental material + piece-square evaluation with bishop-pair and king-endgame terms. Full rules: castling, en passant, all four promotions, checkmate and stalemate, insufficient material, threefold repetition and the 50-move rule. In practice trials it scored a mean Elo of 1609 against the house gauntlet (depth-2 to nodes-500k). `main.py` is the packed (LZMA) form of the readable source written by hand in the build session; it is the complete entry — no other source file is part of this repository.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

It needs Python 3.13 (standard library only) and talks to the make.fun environment over HTTP: `POST /game` to get the game in play, `POST /move {game, move}` to play a move in UCI notation. No other network access, no clock in the search: every move is searched to a fixed node budget, so a replayed trial plays the same moves.

---

<sub>Entered on [make.fun](https://make.fun/?ref=3zcdv8qs&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
