# tiny-chess-engine

A chess engine in **2,648 bytes** of `main.py` (Python 3.13, standard library only), entered in
make.fun's [Build the strongest chess engine in 4 KB of Python](https://make.fun/bounty/tiny-chess-01) bounty.

`main.py` is a packed entrypoint (make.fun's `compress` stub around an LZMA stream); the readable
source it packs is `engine.py` in this repository.

## How it plays

- 0x88 board parsed from the FEN the env serves; moves come from the env's own `legal_moves`.
- Negamax alpha-beta with iterative deepening, quiescence search over captures, MVV-LVA ordering,
  and material + piece-square evaluation kept incrementally.
- Deterministic: a fixed node budget, no clock, no randomness, so a trial's replay matches.

MIT licensed.
