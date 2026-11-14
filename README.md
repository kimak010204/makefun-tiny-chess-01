# tiny-chess-01 — v16l (packed)

0x88 board, negamax alpha-beta + transposition table + killer move +
MVV-LVA ordering, quiescence (captures + evasions when in check),
piece-square tables + bishop pair, PVS, iterative deepening to depth 7
with a per-opponent node budget (deterministic, no clock), null-move
pruning (R=3), and draw contempt −10 (side to move values a draw at
−10cp, so it plays on instead of settling for repetition).

Packed with `makefun compress` (LZMA payload, stdlib only). `main.py`
is the whole engine: 4,095 bytes as committed.

## Strength (local practice trials, 8 games each vs house engines)

- trial-0: 6W 1D 1L, Elo 1748
- trial-1: 4W 2D 2L, Elo 1530
- trial-2: 5W 0D 3L, Elo 1530
- Mean (3 trials, 24 games): Elo 1602.7 — above the 1600 bar for the
  top-50 leaderboard (incumbent 16c was 1599).

## Verify

- Perft: startpos d3 = 8902; Kiwipete d1/d2/d3 = 48/2039/97862.
- Eval startpos = 0.
