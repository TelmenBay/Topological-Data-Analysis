# Improving Market Prediction through N-BEATS Enhanced with Topological Data Analysis

## Overview
This project explores how **Topological Data Analysis (TDA)** can enhance **N-BEATS**, a powerful deep learning model for time series forecasting.  
Our goal is to improve **market prediction accuracy** by integrating geometric insights from TDA with N-BEATS’ interpretable and modular forecasting architecture.

---

## Background

### Topological Data Analysis (TDA)
**TDA** is a mathematical framework that studies the *shape* and *structure* of data rather than relying only on statistical summaries.  
It captures **persistent topological features**—like clusters, loops, and voids—that represent the underlying geometry of the dataset.  
This helps distinguish meaningful structures from noise across multiple scales.

### N-BEATS (Neural Basis Expansion Analysis for Time Series Forecasting)
**N-BEATS** is a deep neural architecture designed specifically for **interpretable time series forecasting**.  
It models complex temporal patterns using stacks of fully connected blocks that decompose data into trend and seasonal components.

#### Key Features
- **Interpretability:** Identifies which components of the data drive predictions.  
- **Modularity:** Built from configurable blocks, allowing flexibility without changing the core architecture.  
- **Generalization:** Performs well across diverse datasets without task-specific tuning.

---

## Research Motivation
To date, **no existing research** directly investigates using TDA for *forecasting tasks*.  
This project aims to bridge that gap—combining **geometric data analysis** with **modern forecasting networks** to uncover deeper temporal structures in financial data.

---

## Dataset and Data Preparation

### Dataset
We use the **Yahoo Finance S&P 500 dataset**, containing historical daily closing prices of the top 500 U.S. publicly traded companies.

We focus initially on a **univariate forecasting** problem:
> Predicting future closing prices based on past lagged values.

### Preprocessing: Sliding Window Approach
We apply a **sliding window** technique to segment the time series into overlapping windows of fixed length.

Each window is used for two purposes:

1. **TDA Feature Extraction:**  
   - Convert each window into a *point cloud* via time-delay embedding.  
   - Extract topological features (e.g., persistent homology) representing the window’s geometric structure.

2. **Forecasting Input (N-BEATS):**  
   - Use the same windows as sequential inputs for model training and validation.  
   - Enables consistent temporal alignment between TDA features and model inputs.

This ensures seamless integration of **topological structure** with **data-driven forecasting**.

---

## Evaluation and Success Metrics
We will compare the **baseline N-BEATS** model against our **TDA-enhanced N-BEATS**.

### Evaluation Metrics
- **Mean Absolute Error (MAE)**
- **Root Mean Squared Error (RMSE)**
- **Mean Absolute Percentage Error (MAPE)**

> Success = Lower error and more consistent forecasts from the TDA-enhanced model compared to the baseline.

---

## Model Architecture
- **Base Model:** N-BEATS (Neural Basis Expansion Analysis for Interpretable Time Series Forecasting)  
- **Enhanced Model:** N-BEATS + TDA features  

We aim to answer the research question:

> **How does the TDA + N-BEATS model perform compared to the baseline N-BEATS model in forecasting accuracy (MAE, RMSE, MAPE)?**

---

## ⚠️ Potential Biases
- **Data Bias:** The S&P 500 focuses on large U.S. companies, possibly limiting generalization to smaller or non-U.S. markets.  
- **Temporal Bias:** Model performance may degrade during structural shifts (e.g., recessions, crises).  
- **Feature Bias:** TDA features may emphasize geometric patterns that don’t actually correlate with future price behavior.

---

## References

1. de Jesus, Luiz Carlos, *et al.* (2025).  
   **Enhancing Financial Time Series Forecasting through Topological Data Analysis.**  
   *Neural Computing and Applications*, 37(9), 6527–6545.  
   [https://doi.org/10.1007/s00521-024-10787-x](https://doi.org/10.1007/s00521-024-10787-x)

2. Nixtla. (2019).  
   **N-BEATS — Nixtla NeuralForecast Library.**  
   [https://nixtlaverse.nixtla.io/neuralforecast/models.nbeats.html](https://nixtlaverse.nixtla.io/neuralforecast/models.nbeats.html)

3. Yahoo Finance. (2025).  
   **Yahoo Finance — Business, Market Data, News.**  
   [https://finance.yahoo.com/](https://finance.yahoo.com/)

---

## License
This project is released under the [MIT License](LICENSE).

