# tiny-chess-01 — v16n (packed)

0x88 board, negamax alpha-beta + transposition table + killer move +
MVV-LVA ordering, quiescence (captures + evasions when in check),
piece-square tables + bishop pair, PVS, iterative deepening to depth 7
with a per-opponent node budget (deterministic, no clock), null-move
pruning (R=3), and draw contempt −10 (side to move values a draw at
−10cp, so it plays on instead of settling for repetition). Move
ordering breaks score ties by move-int ascending (tuple sort).

Packed with `makefun compress` (LZMA payload, stdlib only). `main.py`
is the whole engine: 3,947 bytes as committed.

## Strength (local practice trials, 8 games each vs house engines)

- trial-0: 6W 1D 1L, Elo 1748
- trial-1: 5W 1D 2L, Elo 1598
- trial-2: 6W 0D 2L, Elo 1669
- Mean (3 trials, 24 games): Elo 1671.7 — above the 1600 bar for the
  top-50 leaderboard (16l was 1602.7, 16m was 1508.7).

## Verify

- Perft: startpos d3 = 8902; Kiwipete d1/d2/d3 = 48/2039/97862.
- Eval startpos = 0.
