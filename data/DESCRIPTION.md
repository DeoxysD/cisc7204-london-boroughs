# Data sets

## housing_in_london_monthly.csv

Monthly table for London areas. Columns: `date`, `area`, `average_price`, `code`, `houses_sold`, `no_of_crimes`, `borough_flag`.

`average_price` is a monthly mean in pounds. `no_of_crimes` is the monthly recorded-offence total and is blank before January 2001. `borough_flag == 1` marks boroughs (and the City of London); other rows are London or England totals and are left out of the panel.

Source: London Datastore extracts packaged as [Housing in London](https://www.kaggle.com/datasets/justinas/housing-in-london), UK Open Government Licence. House prices are the GLA aggregation of HM Land Registry Price Paid Data.

## housing_in_london_yearly.csv

Annual table. Columns used in the notebook: `area`, `date`, `median_salary`, `population_size`, `number_of_jobs`, `no_of_houses`, `borough_flag`. The file also carries `mean_salary`, `life_satisfaction`, `recycling_pct`, and `area_size`.

Population and jobs are missing for 2019, so the crime rate, which needs a population denominator, stops at 2018.

Same public source and licence as the monthly file.

## MPS_Borough_Level_Crime_Historical.csv

Metropolitan Police recorded crime by borough, major offence (`MajorText`), minor offence (`MinorText`), and month (`YYYYMM` columns). This copy runs from 201004 through 202302 and includes 201601–201812, which the offence figure uses.

Published by the London Datastore as the historical borough file of [MPS Recorded Crime: Geographic Breakdown](https://data.london.gov.uk/dataset/mps-recorded-crime-geographic-breakdown-exy3m), UK Open Government Licence. The live “Historical” download on that page now starts in November 2020, so the 2016–2018 months come from the earlier public extract of the same table.

## borough_summary_2016_2018.csv

One row per borough for the 2016–2018 window: `area`, `avg_price`, `crime_per_1000`, `median_salary`, `population_size`, `crimes`. This is a derived summary of the two housing files, not a third official source. The notebook rebuilds the cross-section from the monthly and yearly files.
