# Project Brief: Which European Club Should a DC Bar Adopt?

**Author:** Tomas Duque
**Date:** 11/18/2026

## Stakeholder

A DC-based sports-bar owner who wants to adopt one European soccer club as the bar's featured club, to bring in extra customers and sales: filling normally quiet hours, and drawing bigger, higher-spending crowds when matches fall at popular times.

## Decision

Which European club the bar should adopt as its featured club to sponsor and build promotions around.

## Main question

Which European clubs offer a DC bar the most commercially attractive combination of bar-friendly kickoff times, reliable extra matches, and local fan interest, and is there one clear choice or a shortlist?

## Sub-questions

1. How are kickoff times (Eastern time) distributed across leagues and competitions?
2. Which leagues, competitions, and clubs put the most matches in high-value time windows (as scored below)?
3. Which clubs reliably play extra matches in European competitions and domestic cups year after year, and which only did so recently?
4. Which clubs combine high DC-area fan interest with bar-friendly kickoff times and reliable extra matches?
5. Does one club clearly lead on opportunity score, or are several clubs close enough that the owner should choose from a shortlist?
6. How sensitive are the rankings and the shortlist to my scoring assumptions?

## Scope

**In scope**

- Clubs: about 25 of the most popular clubs from the Premier League, La Liga, Serie A, Bundesliga, and Ligue 1 only
- European competitions: UEFA Champions League, Europa League, Conference League
- Domestic cups: FA Cup, EFL Cup, Copa del Rey, Coppa Italia, DFB-Pokal, Coupe de France (only matches involving clubs on my list)
- Kickoff-time analysis: 2025-26 season (the most recent complete season)
- European and cup participation history: 2021-22 to 2025-26 (five seasons; 2021-22 is the Conference League's first season)
- Fan interest measured in the Washington, DC metro area, with the US as a whole for comparison
- US viewership of each competition, as context for the memo (not part of the score)

**Out of scope**

- Clubs from leagues outside the five above, even if they play in European competitions
- US TV and streaming rights
- Actual bar sales or attendance
- DC alcohol licensing hours (noted as a limitation)

## Time windows and scores

All times are US Eastern time. Scores are normalized from 0 to 1, where 1.00 = a prime slot for the bar. They reflect two things: how many fans can come, and how much they're likely to spend. They are assumptions and are tested in the sensitivity analysis.

| Window | Days | Time (ET) | Value score | Reason |
|---|---|---|---|---|
| Weekend late morning | Sat-Sun | 10:00am-1:00pm | 1.00 | Brunch crowd; fills a normally quiet slot |
| Weekend afternoon | Sat-Sun | 1:00pm-5:00pm | 1.00 | Most fans are free; later in the day, so higher drink and food spending |
| Weekday afternoon | Mon-Fri | 2:00pm-6:30pm | 0.67 | Mostly European and midweek matches; fills dead hours and runs into happy hour |
| Weekend early morning | Sat-Sun | 7:00am-10:00am | 0.50 | Dedicated fans only; DC licensing may limit early service |
| Weekday daytime | Mon-Fri | Before 2:00pm | 0.17 | Most people are at work |
| Other times | Any | Any time not listed above | 0.00 | Few matches; outside the bar's target hours |

Note: in the fall, weekend afternoons compete with US college football (Saturdays) and the NFL (Sundays) for screens and crowds. This is not in the score but is noted as a limitation.

## How the score works

A club's season has three parts:

1. **League matches:** guaranteed every season (38, or 34 in 18-team leagues). Scored from their actual 2025-26 kickoff times.
2. **European matches:** not guaranteed. Instead of using only 2025-26, I use the club's **average number of European matches per season over the last five seasons**. A club that plays in the Europa League every year gets reliable credit; a club that reached the Champions League once gets less.
3. **Domestic cup matches:** also not guaranteed, and handled the same way as European matches (five-season average).

For parts 2 and 3, each expected match is scored with the **average window value for that competition**, calculated from 2025-26 kickoff times. This works because each competition plays in fairly consistent time slots (for example, European matches on weekdays).

**Expected schedule value** = league value + (expected European matches x competition window value) + (expected cup matches x competition window value)

**Note on formats:** the Champions League, Europa League, and Conference League changed format in 2024-25 and now have more group-stage-style matches than before. When averaging older seasons, I count seasons played and stage reached, not only raw match totals, and note this in the assumptions file.

## Metrics

- **Matches per window:** count and percentage of each league's, competition's, and club's matches in each window
- **Competition window value:** average window value score per match for each competition
- **European consistency:** seasons in any European competition out of the last five (e.g., 5/5 vs 1/5)
- **Expected extra matches:** five-season average of European and domestic cup matches per season
- **Expected schedule value:** see "How the score works". Because window scores run from 0 to 1, it reads as **equivalent prime-slot matches per season** (e.g., 30.5 = worth as much as 30.5 matches in a prime slot).
- **Fan interest score:** Google Trends interest for the DC metro area, rescaled across batches using an anchor club
- **Club opportunity score:** expected schedule value x fan interest score
- **Lead margin:** how far the top club's opportunity score is ahead of the next club, as a percentage

## Decision rule

- **One clear choice:** if the top club's opportunity score is at least 25% higher than the second club's, recommend that club.
- **Shortlist:** otherwise, recommend every club within 25% of the top score, and let the owner choose using factors the data can't capture (personal preference, existing customers, local supporters' groups).
- The 25% threshold is an assumption and is tested at 15% and 35% in the sensitivity analysis.

## Data sources

| Source | Data |
|---|---|
| football-data.co.uk | 2025-26 league fixtures with kickoff times, 5 leagues |
| FBref (via soccerdata) or football-data.org | 2025-26 European and domestic cup fixtures with kickoff times (check each competition's coverage) |
| FBref (via soccerdata), club pages, or UEFA | European and domestic cup participation, 2021-22 to 2025-26 |
| Google Trends (Washington, DC metro area and United States) | Relative search interest by club |
| Broadcaster press releases and sports media reports | US viewership figures by competition (context only) |

## Known limitations

- Five seasons of history is a reasonable guide but not a guarantee. A club's European qualification and cup runs can change quickly with results, finances, or a new manager.
- Kickoff patterns come from one season (2025-26); TV scheduling can shift slots in future seasons.
- Google Trends measures search interest, not how many fans would actually come to a bar.
- US viewership figures are published for some competitions and matches but not consistently, so they are used as context, not in the score.
- TV availability and DC licensing hours are not included.
- Weekend afternoon value may be lower in the fall, when soccer competes with college football and the NFL.
- All matches in a window get the same score; big matches such as derbies are not valued higher (a possible extension).

## Deliverables

- Python scripts for downloading, loading, and cleaning the data
- SQL analysis files, one per sub-question
- Tableau Public dashboard
- One-page recommendation memo
- GitHub repository with README

## Timeline

| Day | Work |
|---|---|
| 1 | Set up, brief, collect league fixtures and Google Trends data |
| 2 | Collect European and cup fixtures and five-season participation history |
| 3 | Load and clean |
| 4 | SQL analysis |
| 5 | Sensitivity check, finalize findings; start dashboard |
| 6 | Finish dashboard; memo and README |
| 7 | Buffer, publish, resume |