# CPI Analysis — India (2013–2023)

An Excel-based analysis of India's Consumer Price Index (CPI) data, covering Rural, Urban, and Combined (Rural+Urban) sectors from **January 2013 to April 2023**. The workbook cleans the raw index data and investigates category-wise contribution to inflation, year-over-year and month-over-month inflation trends, the impact of COVID-19, and the relationship between crude oil prices and CPI categories.

## Data Source

All-India CPI index values (base-linked, category-wise) published by India's Ministry of Statistics and Programme Implementation (MoSPI), covering the General Index and its sub-categories (Food and Beverages, Housing, Fuel and Light, Health, Transport and Communication, Education, etc.) split by Rural, Urban, and Combined sectors, monthly from 2013 to April 2023.

## Data Dictionary (raw index sheet)

| Column | Description |
|---|---|
| `Sector` | Rural, Urban, or Rural+Urban |
| `Year` / `Month` | Reporting period |
| `General index` | Overall CPI value for that sector/month |
| Category columns (`Cereals and products`, `Meat and fish`, `Housing`, `Fuel and light`, `Health`, `Transport and communication`, `Education`, etc.) | CPI sub-index for that category, sector, and month |

## Workbook Structure

The workbook has 45 sheets. They fall into three groups:

**Raw & cleaned data**
- `All_India_Index_Upto_April23 (1` — the raw CPI index as published, one row per Sector/Year/Month.
- `Clean` — cleaned version with a derived `Index` (month number) and a `Sector and Year` key column; the `Housing` column had missing/`NA` values in the raw data, resolved here via a `Housing Clean` lookup column.
- `Lookups` — helper lookup tables (month name ↔ number, Sector+Year+Month key → cleaned Housing value) used by VLOOKUP formulas elsewhere in the workbook.
- `Sampling` — pivot-table row counts by sector, year, and month, used to confirm the cleaned dataset has complete, evenly distributed records.
- `Rural Miss` / `Urban Miss` / `Rural + Urban Miss` (and their `...Missing` counterparts) — working sheets used to locate and quantify missing values per sector before cleaning.
- `Rough` — scratch/working calculations.

**Analysis by question (Que1–Que5)** — each question has a chain of sheets: a grouping/staging sheet → an inflation or correlation calculation sheet → an analysis/pivot sheet → an insights sheet with the written conclusions.

- `Que1*` — category contribution to the General Index (Rural, Urban, Rural+Urban), with categories grouped into Essential / Food and Beverages / Healthcare / Other.
- `Que2*` — year-over-year inflation by category group, starting from 2017.
- `Que3*` — 12-month and grouped inflation analysis by sector, with a focus on Fruits and Vegetables.
- `Que4*` — COVID-19 impact on inflation, analyzed both month-over-month and year-over-year, split into Pre-COVID / COVID / Post-COVID periods.
- `Que5*` — crude oil price and exchange rate data, correlated against CPI categories (Food, Fuel and Light, Transport and Communication, General CPI), both month-over-month and year-over-year.
- `Crude oil (2)` — monthly crude oil price and INR exchange rate data (2020 onward) used as the external variable for the Question 5 correlation analysis.

## Methodology

1. **Cleaning:** raw index values converted into a consistent monthly dataset; missing `Housing` values identified (`*Miss`/`*Missing` sheets) and filled via lookup; a numeric month index and a combined Sector+Year+Month key added to support time-series calculations and VLOOKUPs.
2. **Category grouping:** the ~25 CPI sub-categories were grouped into broader buckets (Essential, Food and Beverages, Healthcare, Miscellaneous/Other) to make cross-category comparison and averaging more tractable.
3. **Inflation calculation:** month-over-month and year-over-year % change computed per category/group per sector.
4. **Correlation analysis:** Pearson correlation between crude oil price/exchange rate and CPI category inflation, computed separately for M-o-M and Y-o-Y series.
5. **Insights:** each question's insight sheet summarizes the pivot/chart output into written conclusions (see below).

## Key Findings

**Q1 — Category contribution to the General Index**
Food and Beverages contributes the largest share of the General Index across Rural, Urban, and Combined sectors compared to any other category group.

**Q2 — Year-over-year inflation by category (2017 onward)**
Inflation rose steadily from 2019, peaked in 2020–2021 (the COVID period) — Healthcare inflation was highest in 2021 — reached another high in 2022, and then began declining into 2023.

**Q3 — 12-month / grouped inflation (Rural, Urban, Combined)**
Inflation trends, including for Fruits and Vegetables, were computed and grouped separately by sector to compare Rural vs. Urban patterns over 12-month windows.

**Q4 — COVID-19 impact on inflation (M-o-M and Y-o-Y)**
Pre-COVID (2017–early 2020) inflation was relatively stable. During COVID (early 2020–2021), inflation spiked — attributed to panic buying, transport restrictions, and supply-chain disruption — with Healthcare inflation peaking in 2020–2021 due to increased medical demand. Post-COVID (2022–2023), inflation stabilized but remained higher than pre-COVID levels before beginning to decline toward the end of the period.

**Q5 — Crude oil price correlation with CPI categories**
Findings differ notably between time frames:
- *Month-over-month:* only weak correlation between crude oil and Food, General CPI, Fuel and Light, or Transport and Communication — short-term crude oil moves don't strongly track with these categories.
- *Year-over-year:* correlation is stronger — Food and crude oil show a moderate positive correlation; Fuel and Light and General CPI show a weak positive correlation; Transport and Communication shows a **strong positive correlation** with crude oil, meaning sustained crude oil price changes do meaningfully affect transport costs over the year.
- Crude oil inflation itself was highly volatile throughout the period, with the highest spikes around 2021–2022.

## Tools & Techniques

Microsoft Excel — pivot tables, VLOOKUP, grouped averages, percentage-change (inflation) formulas, and Pearson correlation, with supporting charts on each insight sheet.

## How to Use

Open `CPI_Analysis.xlsx` in Excel. Start with `All_India_Index_Upto_April23 (1` and `Clean` to understand the base data, then follow each `Que*` sheet group in order (grouping → inflation/correlation → analysis → insights) to see how each finding was derived.

## Notes

- Some original sheet/column names contain the typo "Inflamation" (Inflation) and "Que" (short for "Question") — these are kept as-is to match the workbook for easy cross-referencing.
- This workbook does not include a customer- or respondent-level identifier; all analysis is at the sector/category/time-period level.

## License

CPI data sourced from India's Ministry of Statistics and Programme Implementation (MoSPI); refer to the original publisher for data usage terms. Add your preferred license (e.g. MIT) for the analysis itself if publishing this repository publicly.
