# Beach Volleyball Match Outcome Prediction Model

## Overview
This repository contains the complete analysis code and methodology for:

**"Performance Analysis of Beach Volleyball Match Outcomes: A Validated Efficiency-Based Prediction Model from 10,095 AVP/FIVB Matches"**

Authors: Kofi Nyantakyi Appiah, Divyanshu Kumar Singh, Nathanael Adu

## Purpose
This project develops and validates a logistic regression model to predict professional beach volleyball match outcomes using standardized performance metrics. The model achieves good discrimination (AUC = 0.6578) with excellent calibration and demonstrates robust generalizability across 18 years of professional competition.

## Contents

### Main Analysis Script
- `YOUR_ACTUAL_analysis.R` - Complete reproducible analysis code including:
  - Model development
  - Internal validation (bootstrap, k-fold cross-validation)
  - External temporal validation
  - Calibration assessment
  - Gender-stratified fairness analysis
  - Visualization generation

### Data
- Pre-processed training data: `training_data_scaled.csv`
- Pre-processed validation data: `validation_data_scaled.csv`
- Original data from BigTimeStats database (https://www.bigtimestats.com)
- Data access date: 14th January 2026
- Raw match-level datasets cannot be redistributed due to database licensing restrictions AND GitHub file size limitations (>25MB)

### Results Output
- `feature_importance_step_1_2.csv` - Model coefficients and odds ratios
- `bootstrap_iterations_step_1_3.csv` - Bootstrap validation results (200 iterations)
- `cv_10fold_overall_step_1_4.csv` - Cross-validation results (10 folds)
- `calibration_by_decile_analysis_1.csv` - Calibration assessment by decile
- `roc_comparison_analysis_2.csv` - ROC curve comparison data
- `discrimination_metrics_analysis_3.csv` - Classification performance metrics
- `test_predictions_step_1_2.csv` - Model predictions on test set
- `bootstrap_male_step_1_3.csv` - Bootstrap results for male athletes
- `bootstrap_female_step_1_3.csv` - Bootstrap results for female athletes
- `bootstrap_summary_step_1_3.csv` - Summary bootstrap statistics
- `Figure3_Calibration.jpg` - Calibration plot visualization

## Requirements

### R Version
- R ≥ 4.0.0

### Required Packages
```r
library(tidyverse)      # Data manipulation and visualization
library(caret)          # Machine learning utilities
library(pROC)           # ROC curve and AUC calculations
library(rms)            # Regression modeling strategies
library(boot)           # Bootstrap resampling
library(DescTools)      # Descriptive statistics
library(car)            # VIF calculation
library(ResourceSelection)  # Hosmer-Lemeshow test
```

### Install Packages
```r
packages <- c("tidyverse", "caret", "pROC", "rms", "boot", 
              "DescTools", "car", "ResourceSelection")
install.packages(packages)
```

## Usage

### Run Complete Analysis
```r
source("YOUR_ACTUAL_analysis.R")
```

## Key Results

### Model Performance
- **Training AUC:** 0.6578 (95% CI: 0.6381–0.6775)
- **Validation AUC:** 0.6578 (excellent temporal stability)
- **Hosmer-Lemeshow χ²:** 8.484, p = 0.3877 (excellent calibration)
- **Brier Score:** 0.2082 (excellent predictive accuracy)
- **Bootstrap Shrinkage Factor:** 0.9954 (minimal overfitting)

### Top Predictors (Logistic Regression)
1. **Kill Efficiency Differential:** OR = 1.493 (49.3% increase per SD; p < 0.001)
2. **Age Difference:** OR = 1.439 (43.9% increase per SD; p < 0.001)
3. **Error Rate Differential:** OR = 0.841 (15.9% decrease per SD; p < 0.001)
4. **Dig Efficiency Differential:** OR = 1.130 (p = 0.001)
5. **Height Differential:** OR = 1.098 (p = 0.0003)
6. **Aces Differential:** OR = 1.099 (p = 0.0002)

### Validation Results
- **10-fold CV AUC:** 0.6812 ± 0.0227 (CV% = 3.34%)
- **Temporal Validation:** 2016-2019 test set AUC = 0.6578 (difference = −0.0234)
- **Gender Equity:** Male AUC = 0.6603; Female AUC = 0.6273 (overlapping 95% CIs)

## Reproducibility

### Random Seed
All analyses use `set.seed(42)` for full reproducibility.

### Session Information
Script includes session info output showing R version, operating system, and package versions.

## Data Availability

The beach volleyball match data analysed in this study are available from the BigTimeStats database (https://www.bigtimestats.com) with data access completed on 14th January 2026. Raw match-level datasets cannot be redistributed directly by the authors due to database licensing restrictions. All statistical analysis code and validation scripts are available at https://github.com/nyantakyiappiah-eng/beach-volleyball-prediction (fixed random seed = 42), enabling complete reproducibility of all reported results.

## Interpretation Guide

### What Does AUC = 0.6578 Mean?
- AUC ranges from 0.50 (random chance) to 1.00 (perfect prediction)
- 0.6578 indicates "good discrimination" for complex behavioral outcomes
- Comparable to NBA (AUC ~0.65-0.68), soccer (AUC ~0.66-0.70)
- Reflects that technical metrics explain ~7% of variance (McFadden R² = 0.0724)
- Unmeasured psychological, tactical, and environmental factors explain remainder

### Practical Applications
1. **Tournament Seeding:** Adjust bracket placement based on predicted win probabilities
2. **Training Prioritization:** Focus resources on highest-impact metrics (kill efficiency, error reduction)
3. **Competitive Intelligence:** Risk-stratify upcoming matches to guide preparation intensity

## Limitations

1. **Professional-only:** Results from FIVB/AVP circuits; may not generalize to amateur/collegiate play
2. **Binary outcome:** Predicts winner only; doesn't predict match margin (set scores)
3. **Data period:** Analysis spans 2002–2019; temporal stability to 2020+ requires new validation
4. **Incomplete case analysis:** 13.2% of original 76,756 matches included (complete data only)

## Citation

If you use this model in your research, please cite:

```
Appiah KN, Singh DK, Adu N. Performance analysis of beach volleyball match outcomes: 
A validated efficiency-based prediction model from 10,095 AVP/FIVB matches. 
International Journal of Sports Science & Coaching. 2026.
```

## Contact & Support

For questions about:
- **Analysis methodology:** See manuscript Methods section
- **Code issues:** Check line comments in `YOUR_ACTUAL_analysis.R`
- **Data access:** Contact BigTimeStats at https://www.bigtimestats.com
- **Manuscript details:** Contact corresponding author

## License

This code is provided for academic and research purposes under the MIT License.

## Acknowledgments

Data compiled from FIVB (International Volleyball Federation) and AVP (Association of Volleyball Professionals) official match statistics, sourced through the BigTimeStats database.

---

**Last Updated:** January 28, 2026  
**Repository Version:** 1.0  
**Analysis Reproducible:** Yes (with seed = 42)