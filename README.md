# EV-Charging-Station-Utilization
EV Station Utilization Forecasting — LightGBM

Predict hourly utilization of EV charging stations using a time-aware Gradient Boosting Machines (LightGBM). This repository contains data preprocessing, feature engineering (lags & rolling stats), time-aware train/validation, LightGBM training & tuning, and results analysis.

# Purpose
Operators and planners for charging networks need accurate short-term forecasts of station utilization to:
    Optimize scheduling and investment in charging infastructure
    Allocate maintenance and staffing
    Analyze what peak times are to reduce congestion 

# Data
The dataset we used was the kaggle dataset: [EV Charging Station Usage of California City](https://www.kaggle.com/datasets/venkatsairo4899/ev-charging-station-usage-of-california-city) 
Additionally it was merged with the Open Meteo API

# Highlights
Time-aware train/validation splitting to mimic real-world deployment
Initial dataset had 200k+ data points
Graphs that analyze trends of utilization, inlcuding heatmaps, bar graphs, and line plots 
Expanded 4 raw columns into 40+ actionable features

# Results
Test RMSE: .126 

R^2: .71

Results are further plotted in notebook


# Key modeling & preprocessing decisions
Time-aware split 
Data cleaning included getting rid of implausible sessions (e.g., charging durations > 24 hours) and correcting missing transaction dates
Feature engineering for LightGBM
    Lag features (short, medium, long lags): util_lag_2h, util_lag_24h, util_lag_168h, etc - filled using seasonal fill
    Rolling aggregations: rolling_mean_24h, rolling_std_24h, rolling_max_24h, etc.
    Time features: cyclic encoding of day of week and hour, month, year, season 
    External features aligned to datetime_hour: weather and holiday
