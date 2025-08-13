# Mortality Investigation Project

![Actuarial Science](https://img.shields.io/badge/Field-Actuarial_Science-blue)

This repository contains an R-based mortality investigation analyzing policyholder data to calculate key mortality metrics.

## Project Overview

The analysis:
- Calculates crude and graduated mortality rates
- Compares actual vs expected mortality experience
- Implements two approaches for central exposed-to-risk calculation:
  - Exact individual exposure method
  - Census approximation method
- Generates diagnostic outputs

## Key Features

- 🕰️ Time-aware age calculation (last birthday convention)
- 📅 Handles exact date arithmetic with leap year awareness
- 📊 Comparative analysis of exact vs census methods
- 📈 Force of mortality estimation

## Technical Details

### Data Requirements
- Policyholder birth dates
- Entry/exit dates
- Death indicators (where applicable)

### Core Calculations
```r 
# Exact exposure calculation
total_EX <- sum(exact$EXPOSURE_AGEX, na.rm = TRUE)

# Census method  
ce_x <- function(dates, populations) {
  time_intervals <- diff(dates)/365.25
  avg_pop <- (populations[-1] + populations[-length(populations)])/2
  sum(time_intervals * avg_pop)
}
```

# Usage
- Clone repository
- Install dependencies:

```r
install.packages(c("tidyverse", "lubridate", "demography"))
```
- Run mortality_analysis.Rmd

# Results
Sample outputs:
- Central exposed-to-risk: 70.5 person-years
- Force of mortality (age 70): 0.0426

# References
Actuarial Mathematics (2nd ed.) by Bowers et al.
R for Data Science by Wickham & Grolemund

_Created with R 4.3.1 and RStudio 2023.03_
