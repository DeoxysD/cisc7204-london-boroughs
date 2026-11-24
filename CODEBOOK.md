# Codebook

Team 05, Class A. The notebook `CISC7204-Team05-Analysis.ipynb` is the executable version of this note.

## Question and sample

The question is whether London boroughs with more recorded crime have lower average house prices.

A borough-year enters the panel when all of these hold:

- `borough_flag == 1` (London boroughs, including the City of London in the raw files)
- price is the mean of the monthly averages, and crime is the sum of the monthly totals
- `crime_months` is the number of months with a non-missing crime total, and the year is kept only if that count is at least 10
- population is present, because the rate needs a denominator

The cross-section keeps boroughs that have all three years 2016, 2017, and 2018, and that have price, crime rate, median earnings, and jobs. That leaves **n = 32**. The City of London drops out of this window. The rate panel stops at 2018 because the yearly file has no population for 2019.

Inner London in Figure 5 is Camden, Islington, Hammersmith and Fulham, Hackney, Haringey, Southwark, Lambeth, Tower Hamlets, Wandsworth, Westminster, and Kensington and Chelsea (11). The other 21 boroughs are outer London.

## Variables

| Name | Meaning |
| --- | --- |
| `average_price` | Monthly mean house price (£), then averaged within the year |
| `no_of_crimes` | Monthly count of recorded offences. Blank before January 2001 |
| `crime_per_1000` | Yearly crime total ÷ population × 1,000 |
| `median_salary` | Median earnings from the yearly file |
| `population_size` | Resident population, yearly file |
| `number_of_jobs` | Workplace jobs, yearly file |
| `jobs_ratio` | Jobs ÷ residents on the 2016–2018 means. Westminster is 3.07; the borough median is 0.46 |
| `rate_day` | Crime total ÷ (residents + jobs) × 1,000 |
| denominator at weight `k` | residents + `k` × jobs. `k = 0` is the draft rate |

Offence rows use `MajorText` from the MPS file, summed over the 36 months from 201601 to 201812, then divided by the summed 2016–2018 population. Fraud and forgery sums to zero in those months and is skipped.

## Statistics, as coded

- `spearman` — average ranks, then Pearson correlation of the ranks.
- `perm_p` — two-sided permutation p. The baseline bars use 5,000 shuffles and seed 7. The inner/outer split uses seed 11.
- `partial_spearman` — residualise both rank series on the rank of the control (here, median earnings), then correlate the residuals.
- `ols_line` — a straight guide on a scatter. It is not a prediction.

## What the figures are for

| Figure | File | Reading |
| --- | --- | --- |
| 1 | `fig1_baseline.png` | Crime rate against price, coloured by earnings. ρ = 0.47, n = 32 |
| 2 | `fig2_bars.png` | Four rank correlations on one scale, including earnings on both sides |
| 3 | `fig3_heatmap.png` | Rank correlations among price, crime rate, earnings, and jobs per resident |
| 4 | `fig4_denominator_curve.png` | ρ as the job weight `k` runs from 0 to 2. The sign crosses zero near k = 1.22 |
| 5 | `fig5_inner_outer.png` | Inner ρ about +0.83 (n = 11); outer ρ about −0.29 (n = 21, permutation p about 0.20) |
| 6 | `fig6_offence.png` | Burglary stays high after earnings (0.74, then 0.65). Arson and criminal damage sits on zero (−0.01) and turns negative after earnings (−0.35) |

Each figure is followed in the notebook by a markdown cell that says how it follows Cairo’s guidelines and whether it is truthful, functional, beautiful, and insightful.

## What a successful reading is

A reader can see that these borough tables do not support “more crime, cheaper housing,” and can see why: the sign is positive, earnings moves with both variables, the sign depends on the denominator, and offence types do not share one correlation. Success is not a forecast and not a causal claim.
