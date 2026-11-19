# Assumptions

Every judgment call in this project, why I made it, and how I test it. Update this file whenever I make a new decision.

**Last updated:** 11/18/2026

## 1. Time-window scores

All times are US Eastern time. Scores are normalized from 0 to 1: **1.00 = a prime slot** (the most valuable time for the bar), and 0 = no value. A club's schedule value is therefore its number of **equivalent prime-slot matches**. Scores reflect the bar's goal: bring in extra customers and sales, both by filling quiet hours and by drawing bigger, higher-spending crowds at popular times.

| Window | Days | Time (ET) | Score | Reason |
|---|---|---|---|---|
| Weekend late morning | Sat-Sun | 10:00am-1:00pm | 1.00 | Brunch crowd; fills a normally quiet slot |
| Weekend afternoon | Sat-Sun | 1:00pm-5:00pm | 1.00 | Most fans are free; later in the day, so higher drink and food spending |
| Weekday afternoon | Mon-Fri | 2:00pm-6:30pm | 0.67 | Mostly European and midweek matches; fills dead hours and runs into happy hour |
| Weekend early morning | Sat-Sun | 7:00am-10:00am | 0.50 | Dedicated fans only; DC licensing may limit early service |
| Weekday daytime | Mon-Fri | Before 2:00pm | 0.17 | Most people are at work |
| Other times | Any | Anything not listed above | 0.00 | Few matches; outside the bar's target hours |

**Rule for every scenario:** the most valuable window scores 1.00, and the others are scored relative to it.

- **Why:** My judgment of typical bar traffic and spending, not measured data.
- **Known gaps:** In the fall, weekend afternoons compete with college football and the NFL. All matches in a window score the same; big matches such as derbies are not valued higher.
- **To verify in Step 5:** which competitions actually fill the weekday afternoon window (expected: mostly European matches). Update the reason if the data says otherwise.
- **Tested by:** A quiet-hours-focused scenario and a spending-focused scenario (Step 6, test 1).
- **Result:** _To be filled in after Step 6._

## 2. Decision rule threshold

- **Assumption:** One club is a "clear choice" if its opportunity score is at least 25% higher than the second club's. Otherwise, every club within 25% of the top score forms the shortlist.
- **Why:** A gap smaller than 25% could easily come from the scoring choices rather than a real difference.
- **Tested by:** Rerunning at 15% and 35% (Step 6, test 2).
- **Result:** _To be filled in after Step 6._

## 3. History window for European and cup matches

- **Assumption:** Expected European and cup matches per season = average over the last five seasons (2021-22 to 2025-26).
- **Why:** Adopting a club is a multi-season decision, so reliability matters more than one season. Five seasons is long enough to show a pattern and starts with the Conference League's first season (2021-22).
- **Tested by:** Rerunning with the last three seasons (Step 6, test 3).
- **Result:** _To be filled in after Step 6._

## 4. Fan interest measure

- **Assumption:** Google Trends search interest in the Washington DC (Hagerstown MD) metro area represents local fan interest.
- **Why:** The bar is in DC, so local interest matters more than national. Search interest is the best free, comparable measure available.
- **Anchor club for rescaling batches:** _[club name, chosen in Step 2]_
- **Search type:** The club's topic (labelled "Football club"), not plain text.
- **Tested by:** Rerunning with United States interest (Step 6, test 4).
- **Result:** _To be filled in after Step 6._

## 5. Club list

- **Assumption:** Only about 25 of the most popular clubs from the Premier League, La Liga, Serie A, Bundesliga, and Ligue 1.
- **Why:** I need every club's full schedule. Clubs from other leagues would be missing their league matches and score unfairly low.
- **How the list was chosen:** _[fill in when you pick the clubs, e.g., top 25 by US Google Trends interest]_

## 6. Kickoff-time season

- **Assumption:** 2025-26 kickoff times represent each competition's typical time slots.
- **Why:** It's the most recent complete season, so all kickoff times are final.
- **Risk:** TV scheduling can shift slots in future seasons. Noted as a limitation.

## 7. Value of European and cup matches

- **Assumption:** Each expected European or cup match is worth that competition's average window score in 2025-26.
- **Why:** European competitions and cups play in fairly consistent time slots, so a competition-wide average is a reasonable estimate for a future match.

## Assumptions to add later

- **UEFA format change adjustment** (Step 4): how pre-2024-25 Champions League and Europa League seasons are adjusted
- **Source time zones** (Step 2): which time zone each data source uses
- **Any cleaning decisions** that change what counts in the score