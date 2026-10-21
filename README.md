# Do Higher Hospitality Wages Lead to Better Hotel Ratings?

Hotel reviews and hospitality wages across U.S. states.

**Team B07:** Anna Zvanskaya, Paula Vasques, Pushan Parihr, Summer Kao, Sharanya Srinivas
**Course:** BA780 Introduction to Data Analytics, Final Project

## Overview

Do states that pay hospitality workers more have better-rated hotels, and what do guests actually complain about? The project joins U.S. hotel reviews with 2013 BLS wage data by state to find out. It is aimed at hotel managers, HR teams, and investors deciding where to spend to improve ratings.

## Key Findings

- **Wages are not linked to ratings.** Across 42 states, the correlation between average hospitality wage and average rating is **−0.03**.
- **Room condition is.** The share of reviews mentioning room problems (cleanliness, pests, smell or smoke, broken or outdated rooms) correlates **−0.89** with state ratings.
- **Cleanliness is the top complaint** (roughly 18–20% of low-rated reviews vs. about 6% for staff and service).
- **Ratings are stable over time.** The national average stayed between 3.68 and 3.82 from 2011 to 2016. State averages range from 3.17 (SC) to 4.60 (NH).

**Takeaway:** Focus on room upkeep over across-the-board wage increases. Wages still matter for retention and fairness, but state-level wage levels do not predict guest ratings.

## Data Sources

| Data | Source | License |
| --- | --- | --- |
| Hotel reviews | [Datafiniti Hotel Reviews (Kaggle)](https://www.kaggle.com/datasets/datafiniti/hotel-reviews) | CC BY-NC-SA 4.0 |
| Wages | [U.S. BLS Occupational Employment and Wage Statistics, May 2013](https://www.bls.gov/oes/tables.htm) | Public domain |

**Input files** (not included; add them to the working folder):

| File | Rows | Columns |
| --- | ---: | ---: |
| `Datafiniti_Hotel_Reviews.csv` | 10,000 | 25 |
| `Datafiniti_Hotel_Reviews_Jun19.csv` | 10,000 | 26 |
| `7282_1.csv` | 35,912 | 19 |
| `780_data_wages_01.xlsx` | 434,473 | 29 |

## Method

1. **Clean reviews:** merge three schemas, remove 214 exact duplicates, standardize fields, keep missing values, and flag possible duplicates and truncated text.
2. **Normalize ratings:** halve the 357 scores above 5 (10-point scale) and drop zeros. The main analysis uses 27,474 U.S. reviews from 42 states with at least 100 reviews each.
3. **Clean wages:** convert special symbols to missing values, label area and ownership codes, and average hospitality wages per state.
4. **Classify complaints:** keyword matching into 8 categories (cleanliness, pests, smell and smoke, broken or outdated room, staff and service, noise, bed comfort, price and billing). Low-rated is 1–3 stars and high-rated is 4–5.
5. **Join by state** and compare with correlations and group comparisons (Q1–Q12 in the notebook).

## Running the Notebook

1. Upload the four input files (in Colab, use the Files panel).
2. Requirements: Python, pandas 2.0+, NumPy, Matplotlib, Seaborn, openpyxl.
3. Run top to bottom. Cleaned data is written to `hotel_cleaning_outputs/` and `oes_2013_clean.csv`; charts are saved as `Q6_` to `Q9_` PNG and CSV files.
4. The analysis cells load `hotel_reviews_combined_cleaned (1).csv`. Adjust the filename if yours differs.

## Limitations

- Correlation across state averages does not show causation.
- Wages are from 2013, while reviews span 2011–2016.
- The rating scale of `7282_1.csv` is unverified, so the halving is an assumption.
- Keyword matching misses some complaints and catches some positive mentions.
- Wage averages are not weighted by employment, and reviews per state are uneven.
- Download links, access dates, and reuse terms for the supplied files still need confirming.

## AI Disclosure

The team used Claude for outlining, code review and debugging, and visualization ideas. All AI-generated content was reviewed and validated by the team.
