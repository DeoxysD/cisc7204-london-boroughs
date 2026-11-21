# Crime and house prices in London boroughs

**FAN ZIQIAN** · CISC7204 Class A · Team 05

Research question: in London, do boroughs with a higher recorded crime rate have lower average house prices?

The common-sense claim says yes. On the 2016–2018 means of 32 London boroughs, the claim does not hold. Spearman's rank correlation between crimes per 1,000 residents and average house price is **ρ = 0.47** (n = 32). The association is positive: boroughs with more recorded crime per resident tend to have higher prices, not lower ones. Median earnings move with both prices (ρ = 0.51) and the crime rate (ρ = 0.59). The raw crime count, without dividing by population, only reaches ρ = 0.25.

This is a borough-level association. It does not show that crime causes high prices, and it does not describe any one street or household.

## What is in this repository

This is the individual record of the first two steps of the team project: build the borough-year panel, define the crime rate, and redraw the cross-section.

| Path | Contents |
| --- | --- |
| `notebooks/01_eda.ipynb` | Load, join, rate, correlations, and the figure |
| `data/housing_in_london_monthly.csv` | Monthly prices, sales, and crime totals |
| `data/housing_in_london_yearly.csv` | Annual earnings, population, jobs, and dwellings |
| `data/borough_summary_2016_2018.csv` | The 32-borough table the figure uses |
| `figures/crime_vs_house_price.png` | The figure written by the notebook |

## Data

1. Housing in London, Justinas Cirtautas, on Kaggle: [housing-in-london](https://www.kaggle.com/datasets/justinas/housing-in-london). Monthly file: January 1995–January 2020. Yearly file: earnings, population, jobs, dwellings.
2. Average house prices by borough, Greater London Authority, from HM Land Registry Price Paid Data: [data.london.gov.uk](https://data.london.gov.uk/dataset/average-house-prices).

The working files are the two Kaggle tables. The City of London is left out of the 2016–2018 window. A borough-year enters only when crime is recorded for at least 10 months. Price is the yearly mean, crime is the yearly sum, and the rate is crimes ÷ population × 1,000. The plotted points are borough means over 2016–2018.

## Reproduce

From the repository root, with Python 3:

```bash
pip install -r requirements.txt
jupyter notebook notebooks/01_eda.ipynb
```

The notebook looks for `data/` in the current directory, then in the parent directory, so it also runs if the kernel starts inside `notebooks/`.

## Portfolio

This repository is the project linked from [the portfolio site](https://deoxysd.github.io/data-science-portfolio/).
