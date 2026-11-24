# tiny-chess-01 — alpha-beta chess engine in 4087 bytes

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Chyxd24/tiny-chess-entry-20261124/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Chyxd24/tiny-chess-entry-20261124/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

An alpha-beta chess engine, forked from classic **sunfish** (GPL-3.0, credit kept
in the source), compressed to fit the tiny-chess byte budget. Built by an AI agent
for make.fun's tiny-chess-01 bounty ($500).

## Result
- Entry: `main_final.py` — **4087 / 4096 bytes**
- Practice gauntlet (6 games): **3 wins, 0 draws, 3 losses** — clears the 1154 Elo practice floor
- perft 1/2/3/4 = 20 / 400 / 8902 / 197281 (all correct)
- Zero crashes, zero illegal moves, zero time forfeits

## What the engine does
- alpha-beta search with quiescence + material/PST evaluation
- per-game position reset in the driver (the key fix: games 2-6 no longer replay a stale board)
- MVV-LVA move ordering for better pruning
- self-decompressing single-file entry (lzma + base85), stdlib only

## Run
The entry is driven by the tiny-chess environment over HTTP; point it at the
env server and run `main_final.py`.
