# RBI Bank Credit Deployment Analysis

Sector-wise trend analysis of bank credit deployment in India, built from raw RBI data, not a pre-cleaned Kaggle dataset.

## Why this project

Most portfolio projects use datasets that are already cleaned and picked apart by hundreds of other people. This one uses RBI's own published statistics, so the cleaning, the judgment calls, and the mistakes along the way are all real.

## Data source

Reserve Bank of India, Database on Indian Economy (DBIE), "Sector-wise Gross Bank Credit of Scheduled Commercial Banks," monthly data, January 2019 to May 2026.
Source: [rbi.org.in](https://rbi.org.in) → Statistical Tables Relating to Banks in India

## What's in this repo

| File | Description |
|---|---|
| `Deployment_of_Bank_Credit_by_Major_Sectors.xlsx` | Cleaned, analysis-ready dataset (long format) |
| `Deployment_of_Bank_Credit_Full_Insights.xlsx` | Dashboard workbook with charts and summary tables |
| `Data_Cleaning_Report_Bank_Credit_Deployment.md` | Full documentation of every cleaning step and decision |

## Data cleaning summary

Raw RBI exports are not analysis-ready. This project involved:
- Removing duplicate header rows and blank spacer rows left over from the source export
- Unmerging cells and filling labels down so every row had a proper category name
- Standardizing an irregular fortnightly reporting cadence into one consistent column per month
- Disclosing (rather than silently fixing) six reporting periods where RBI's own footnote states the labeled date doesn't match the actual collection date
- Identifying a structural break: the HDFC–HDFC Bank merger (July 2023) caused a one-time inflated jump in credit figures across several sectors; RBI's merger-adjusted figures were used for accurate comparison
- Treating missing values marked "-" as nulls, not zero, to avoid understating growth
- Maintaining category hierarchy carefully (e.g. Industry sub-categories were never summed together with the Industry total) to avoid double counting

Full detail: see `Data_Cleaning_Report_Bank_Credit_Deployment.md`.

## Key findings

- Total Bank Credit grew **130.5%** from January 2019 to May 2026; Non-food Credit grew almost identically (130.8%), while Food Credit lagged at 93.1%.
- **Industry credit, which looked stagnant over the full 7-year period (+70.3%), is actually the fastest-accelerating sector right now**: 13.4% annualized growth in the last ~18 months versus 3.9% in 2019–2022.
- **Personal Loans, the historical growth leader (+215.3% over the full period), has plateaued**: 14.7% recent annualized growth versus 14.8% earlier, essentially flat.
- The HDFC merger inflated reported Personal Loans figures by as much as 10.8% at the point of the merger, while Industry was barely affected (0.5%), confirming the merger's impact was concentrated in mortgage-heavy lending.

## Tools used

Excel, Power Query, Power BI

## Known limitations

- Underlying bank reporting coverage expanded from ~90% to ~95% of total non-food credit over this period, so a portion of observed growth may reflect wider coverage rather than pure organic growth.
- Six specific monthly data points carry a minor date-labeling discrepancy per RBI's own footnote (see cleaning report for the exact list); retained as-is and disclosed rather than corrected.
