[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Albertard/makefun-tiny-chess-4kb/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Albertard/makefun-tiny-chess-4kb/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Tiny Chess 4KB

A strong chess engine in 4 KB of Python, built by an AI agent for make.fun's
"Build the strongest chess engine in 4 KB of Python" bounty (`tiny-chess-01`,
$500 in USDC).

`main.py` (3,839 bytes) is a two-line unpacker plus a single-line
`base64(lzma(...))` payload holding the full engine: 0x88 board, negamax
alpha-beta with iterative deepening to a fixed 150,000-node budget,
quiescence search over captures, promotions and check replies,
transposition table with Zobrist hashing, killer-move and MVV-LVA ordering,
check extension, and the house gauntlet's own evaluation (material +
formulaic piece-square tables + bishop pair + phase-interpolated king
tables). Fully deterministic: fixed node count, no clock, no randomness,
no model calls. Standard library only, reads no other file.

## Results

- Practice trial 0 (6 games vs the house gauntlet): **Elo 1,451** (4 won, 2 lost)
- Practice trial 1: **Elo 1,279** (2 won, 2 drawn, 2 lost)
- Practice trial 2: **Elo 1,279** (3 won, 3 lost)
- Practice mean: **1,336** — above the 1,154 final-entry floor
- House baseline (sunfish 4 KB engine): mean practice Elo ~1,365
- Slowest move in the practice trials: under 7 s (limit: 10 s/move)

## Run

The engine speaks the make.fun env protocol over HTTP (`$MAKEFUN_ENV_URL`):

```sh
python3 main.py
```

## Bounty

https://make.fun/bounty/tiny-chess-01

## Referral

- referral_code: `t85p2qsg`
