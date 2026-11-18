# Project Brief: When Should US Bars Show European Soccer?

**Author:** [Tomas Duque]
**Date:** [11/16/2026]

## Stakeholder

A US sports-bar owner deciding which European leagues and clubs to promote, and when, to bring in customers during normally quiet hours.

## Decision

Which matches to advertise, staff for, and build promotions around.

## Main question

Which European leagues and clubs produce the most matches in commercially valuable US time slots, weighted by American fan interest, and which time windows offer bars the best chance to draw customers during normally quiet hours?

## Sub-questions

1. How are kickoff times (US Eastern time) distributed across leagues and competitions?
2. Which leagues put the most matches in weekend late-morning and weekday afternoon windows?
3. Which clubs combine high US fan interest with bar-friendly kickoff times?
4. When do big matches clash with each other, and when does one stand alone?
5. How sensitive are the rankings to my scoring assumptions?

## Scope

**In scope**

- Leagues: Premier League, La Liga, Serie A, Bundesliga, Ligue 1
- Competition: UEFA Champions League
- Season: 2025-26
- US fan interest for about 25 of the most popular clubs in the US

**Out of scope**

- US TV and streaming rights
- Actual bar sales or attendance
- Domestic cup competitions
- Bar licensing hours (noted as a limitation)

## Time windows and scores

All times are US Eastern time. These scores are assumptions and are tested in the sensitivity analysis.

| Window | Days | Time (ET) | Value score | Reason |
|---|---|---|---|---|
| Weekend late morning | Sat-Sun | 10:00am-1:00pm | 3 | Brunch crowd; normally quiet |
| Weekday afternoon | Mon-Fri | 2:00pm-4:30pm | 3 | Fills dead hours before happy hour |
| Weekend early morning | Sat-Sun | 7:00am-10:00am | 2 | Die-hard fans only; licensing may limit |
| Weekend afternoon | Sat-Sun | 1:00pm-5:00pm | 1 | Bars already fairly busy |
| Weekday daytime | Mon-Fri | Before 2:00pm | 0 | Most people are at work |

## Metrics

- **Matches per window:** count and percentage of each league's matches in each window
- **Schedule value:** sum of window value scores for a league or club
- **US interest score:** Google Trends interest, rescaled across batches using an anchor club
- **Club opportunity score:** schedule value x US interest score
- **Clash count:** high-interest matches kicking off within 30 minutes of each other

## Data sources

| Source | Data |
|---|---|
| football-data.co.uk | 2025-26 fixtures with kickoff times, 5 leagues |
| FBref (via soccerdata) or football-data.org | Champions League fixtures |
| Google Trends (United States) | Relative search interest by club |

## Deliverables

- Python scripts for downloading, loading, and cleaning the data
- SQL analysis files, one per sub-question
- Tableau Public dashboard
- One-page recommendation memo
- GitHub repository with README

## Timeline

| Day | Work |
|---|---|
| 1 | Set up, brief, collect data |
| 2 | Load and clean |
| 3 | SQL analysis |
| 4 | Sensitivity check, finalize findings |
| 5 | Dashboard |
| 6 | Memo and README |
| 7 | Buffer, publish, resume |
