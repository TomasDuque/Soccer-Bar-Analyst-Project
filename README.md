# Which European soccer leagues and clubs offer the most commercially attractive match schedules for American bars??


**Dashboard:** [Tableau Public link]   **Memo:** [docs/memo.md]

![Dashboard screenshot](dashboard/overview.png)

## Key findings
- Finding 1 with a number
- Finding 2 with a number
- Finding 3 with a number

## Data
| Source | What | Rows |
|---|---|---|
| football-data.co.uk | 2025-26 fixtures, 5 leagues | ... |
| FBref / football-data.org | Champions League fixtures | ... |
| Google Trends | US search interest, 25 clubs | ... |

## Method
1. Converted kickoff times to US Eastern time (DST-aware)
2. Scored each match by time window (see docs/assumptions.md)
3. Weighted by US fan interest
4. Tested rankings under 3 different time ranking cases

## Tools
Python (pandas), DuckDB SQL, Tableau Public

## Repository structure
(paste the folder tree)

## Limitations
- ...

## How to reproduce
1. pip install duckdb pandas requests
2. python scripts/01_download.py
3. python scripts/02_load.py
4. python scripts/03_clean.py
5. Run sql/ files in order