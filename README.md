# Brooklyn Nets 2026-27: season review, trade scenarios and a win forecast

The Nets went 20-62 in 2025-26 and rebuilt in the summer. This project reviews the team, tests free agents and seven hypothetical trades against the 2026-27 salary-cap rules, and forecasts the new season, with an honest error band and a backtest of the method.

*Written on 21 October 2026, at the start of the season. No 2026-27 results were used.*

## Headline results

| Question | Answer |
|---|---|
| How bad was 2025-26? | Worst offence in the league (108.7 per 100 possessions); 30th in shooting efficiency and 29th in turnovers; 26th on defence; net rating -10.3 |
| Forecast, current roster | **33.8 wins, give or take 8** (1 SD). The prediction market is at 26.2, so treat 33.8 as an upper-end estimate |
| Does the method work? | Backtest 2006-2026: correlation 0.79 with real team ratings, vs 0.61 for "repeat last year" |
| Free agents? | None adds more than ~1.6 wins, far inside the error band |
| Trades? | Hypothetical win-now trades add 5-8 wins on paper, mostly through minutes; selling Porter Jr. costs 4-5 wins but returns assets (not valued here) |
| Does losing buy a 2027 top pick? | No: Houston holds swap rights on Brooklyn's 2027 first (2021 Harden trade), so Brooklyn gets the less favourable of the two picks. Selling Porter pays off only through what comes back |
| Biggest lever | Rotation: handing minutes out by our ranking instead of the projected rotation is worth +6.8 wins |

## Method

For each player, last season's Box Plus/Minus (BPM) is shrunk toward -2.0 in proportion to how few minutes he played (`s = (BPM*MP + prior*K)/(MP + K)`, K = 500). Team rating = sum of `s` x minutes/48; net rating is converted to wins with a regression on all 82-game seasons since 2001. `K = 500` and prior `-2.0` were fixed before the 2026-27 forecast was made.

**Backtest:** for each season 2006-2026 (without 2020, 2021), predict team net rating from the previous season's player BPM and the actual current-season minutes. Result: RMSE 3.1 net-rating points (about 8 wins). A lower prior for young players did not improve it (kept as a sensitivity case only).

## What is in the notebook

1. 2025-26 team profile against the league
2. Player report card (impact vs salary)
3. Forecast method and backtest
4. 2026-27 forecast with variants
5. Free agents
6. Seven hypothetical trades checked against 2026-27 cap rules, plus the draft-pick picture (why tanking does not pay in 2027) and a public 2027 mock-draft top 10
7. Conclusions and limitations

## Limitations

- BPM comes from box scores; it misses defence that does not show up there and is noisy for small minute samples.
- One season of inputs; no age curves, injuries or development.
- About +-8 wins of error (1 SD). Brooklyn itself was over-predicted last year (-5.4 predicted vs -10.3 actual).
- Rotation minutes are assumed (ClutchPoints projection), not predicted.
- Contracts were scraped on 18 June 2026, before free agency and the 10 July trade. The 2026-27 roster and salaries were completed from public reports; some are unconfirmed (for example, how much of Porter Jr.'s salary is guaranteed). Partner-team payroll checks are approximate.
- Salary-matching tiers come from a 2024-25 summary and were not re-checked for 2026-27.
- Pick ownership and protections come from sources dated 2024-2025 and were not re-verified; the 2027 mock draft (nbadraftroom.com, 20 Oct 2026) is one site's view, not our evaluation.
- Trades are hypothetical: none was reported, picks are not valued, and partner willingness is not modelled.

## Data

Not redistributed here. Download from Kaggle and place in one folder:
- `sumitrodatta/nba-aba-baa-stats`: `Advanced.csv`, `Team Summaries.csv`
- `deocheng/nba-data-1946-2026`: `public.player_contracts.csv`

Cap figures: NBA.com. Salaries and rotation: ShamSports and ClutchPoints. Market win total: Kalshi.

## How to run

Open `nets_review.ipynb` in Google Colab, set `FOLDER` in the first code cell to the folder with the data, and run all cells.
