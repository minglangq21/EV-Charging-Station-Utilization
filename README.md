# EV-Charging-Station-Utilization
EV Station Utilization Forecasting — LightGBM

Predict hourly utilization of EV charging stations using a time-aware Gradient Boosting Machines(LightGBM). This repository contains data preprocessing, feature engineering (lags & rolling stats), time-aware train/validation splitting that prevents temporal and cross-station leakage, LightGBM training & tuning scripts, and reproducible experiment tracking.

A short version: we build station-aware lag/rolling features (no cross-station leakage), train a LightGBM model to predict hourly utilization, and provide utilities for evaluation and deployment.
