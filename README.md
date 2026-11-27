# Melbourne Rental Stress Prediction

A data science early-warning framework for identifying
emerging rental affordability risks across metropolitan
Melbourne using historical rental data and predictive
analytics in R.

## Project Overview

Rental affordability is a growing challenge in Melbourne.
This project explores how historical rental market data
can be used to anticipate future rental price increases
and support proactive housing policy decisions.

The proposed framework aims to integrate rental prices,
household income and socioeconomic indicators to identify
emerging rental-stress hotspots.

The current implementation focuses on predicting
next-quarter median rental price increases.

## Project Objectives

- Analyse historical rental trends across Melbourne.
- Identify geographical differences in rental prices.
- Engineer features from historical rental data.
- Develop binary classification models.
- Evaluate predictive performance using chronological
  train-test splitting.
- Establish a foundation for a multi-source rental
  affordability early-warning system.

## Dataset

**Source:** Homes Victoria — Quarterly Median Rents by
Local Government Area.

- Geographical coverage: 31 metropolitan Melbourne LGAs
- Time period: June 1999 – September 2025
- Frequency: Quarterly
- Total quarters: 106
- Processed observations: 3,286

### Key Variables

| Variable | Description |
|---|---|
| LGA | Local Government Area |
| Quarter | Quarterly observation date |
| Median Rent | Median weekly rental price |
| Rental Count | Number of rental observations |
| Quarterly Growth | Percentage change in median rent |
| Previous Growth | Previous-quarter rental growth |
| Deterioration | Binary next-quarter rent increase indicator |

### Data Source

[Homes Victoria Rental Dataset](https://discover.data.vic.gov.au/dataset/rental-report-quarterly-quarterly-median-rents-by-lga)

## Technologies and Tools

- R
- RStudio
- R Markdown
- Microsoft Excel
- GitHub

### R Libraries

- readxl
- dplyr
- tidyr
- lubridate
- ggplot2

## Methodology

The project follows the CRISP-DM data science framework.

1. Business Understanding
2. Data Understanding
3. Data Preparation
4. Modelling
5. Evaluation
6. Proposed Deployment

### Data Preparation

- Imported and transformed historical rental data.
- Filtered metropolitan Melbourne LGAs.
- Restructured data into tidy longitudinal format.
- Checked missing values, duplicates and invalid records.
- Created temporal and rental growth features.
- Constructed a binary classification target.

### Predictive Modelling

Logistic regression was selected because of its
interpretability and suitability for binary classification.

The target variable indicates whether median weekly rent
increases in the following quarter.

A chronological train-test split was implemented to
reduce temporal data leakage.

| Dataset | Observations | Period |
|---|---:|---|
| Training | 2,852 | Dec 1999 – Sep 2022 |
| Testing | 310 | Mar 2023 – Jun 2025 |

December 2022 observations were excluded from training
to prevent next-quarter target leakage.

## Exploratory Data Analysis

### Historical Rental Trends

![Melbourne Rental Trends](visuals/Figure1_Melbourne_Rental_Trends.png)

The analysis identified substantial increases in median
weekly rental prices between 1999 and 2025, particularly
after 2022.

### Highest Median Weekly Rents — September 2025

| LGA | Median Weekly Rent |
|---|---:|
| Bayside | $743 |
| Manningham | $680 |
| Melbourne | $670 |

## Model Performance

![Model Performance](visuals/Figure2_Model_Performance.png)

| Model | Accuracy |
|---|---:|
| Original Logistic Regression | 45.16% |
| Improved Logistic Regression | 48.71% |
| Logistic Regression (Threshold 0.30) | 61.61% |
| Historical Momentum Baseline | 58.71% |
| Majority-Class Baseline | 63.87% |

The logistic regression model with a classification
threshold of 0.30 achieved a recall of 87.88%.

However, none of the evaluated models outperformed the
majority-class baseline in accuracy.

These findings highlight the importance of baseline
comparison, feature engineering and rigorous temporal
validation.

## Limitations

- The current model predicts rental price increases,
  not actual household rental stress.
- Household income and socioeconomic indicators have
  not yet been integrated.
- Historical rental patterns may not fully capture
  changing market conditions.
- Classification threshold exploration was conducted
  on the test dataset and requires independent validation.
- The models did not outperform the majority-class
  baseline in accuracy.

## Future Improvements

- Integrate Australian Bureau of Statistics income
  and socioeconomic data.
- Develop a comprehensive Rental-Stress Risk Score.
- Explore Random Forest and gradient boosting models.
- Implement rolling-window time-series validation.
- Evaluate precision, recall, F1-score and calibration.
- Develop an interactive geographical dashboard.
- Incorporate uncertainty and fairness assessments.

## Repository Structure

    melbourne-rental-stress-prediction/
    ├── README.md
    ├── .gitignore
    ├── rental_stress_analysis.Rmd
    ├── melbourne_rental_stress.Rproj
    ├── data/
    └── visuals/
        ├── Figure1_Melbourne_Rental_Trends.png
        └── Figure2_Model_Performance.png

## How to Run

1. Clone or download this repository.
2. Download the Homes Victoria rental dataset.
3. Place the Excel dataset inside the data/ directory.
4. Open melbourne_rental_stress.Rproj in RStudio.
5. Install the required R packages.
6. Open rental_stress_analysis.Rmd.
7. Run all code chunks or knit the document to HTML.

Install the required packages using:

    install.packages(c(
      "readxl",
      "dplyr",
      "tidyr",
      "lubridate",
      "ggplot2"
    ))

## Potential Applications

- Housing policy planning
- Rental market monitoring
- Geographic risk identification
- Community housing resource allocation
- Government decision support

## Skills Demonstrated

- Data Cleaning and Preprocessing
- Exploratory Data Analysis
- Data Visualisation
- Feature Engineering
- Statistical Modelling
- Logistic Regression
- Binary Classification
- Temporal Data Validation
- Model Evaluation
- Reproducible Data Science
- Data Governance

## Author

**Arham Chowdary**

Master of Data Science — Monash University

## Acknowledgements

This project was originally developed as part of
FIT5145 — Foundations of Data Science at Monash University.

Rental data is sourced from Homes Victoria.

## Disclaimer

This project is an educational research prototype.
It is not a deployed rental-stress forecasting system
and should not be used as the sole basis for housing
or financial decisions.
