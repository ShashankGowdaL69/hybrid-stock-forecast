# Hybrid Stock Forecasting

A stock market forecasting project exploring the integration of statistical time-series models, deep learning, gradient boosting, financial-news sentiment analysis, and explainable AI for Indian equities.

## Overview

Hybrid Stock Forecasting explores how multiple forecasting approaches can be combined to analyze historical stock prices and generate multi-day forecasts.

The project brings together three base forecasting models—ARIMA, LSTM, and XGBoost—with an XGBoost stacking meta-model. Financial-news sentiment analysis and SHAP-based explanations provide additional context for interpreting forecasts.

The application is designed around a React frontend, Spring Boot backend, and Python-based machine learning service.

## Key Components

- **ARIMA:** Statistical time-series forecasting using historical closing prices.
- **LSTM:** Deep learning model for learning temporal patterns in sequential stock-price data.
- **XGBoost:** Gradient-boosted decision-tree model using market data and engineered technical indicators.
- **Stacking Ensemble:** Uses an XGBoost meta-model to combine predictions from the three base models.
- **Sentiment Analysis:** Analyzes financial news to derive sentiment signals and apply a separate forecast adjustment.
- **SHAP Explainability:** Provides feature-attribution explanations for XGBoost predictions.
- **Interactive Dashboard:** Provides visualizations for stock data, forecasts, model metrics, and technical indicators.
- **Sentiment Simulation:** Demonstrates how manually entered financial news can influence a simulated stock-price graph.

## System Architecture

```text
          React + TypeScript
                 |
                 v
          Spring Boot Backend
             /         \
            v           v
      MongoDB Atlas   FastAPI ML Service
                           |
                           v
                  Historical Market Data
                           |
             +-------------+-------------+
             |             |             |
             v             v             v
           ARIMA          LSTM         XGBoost
             |             |             |
             +-------------+-------------+
                           |
                           v
                 XGBoost Meta-Model
                           |
                           v
                    Hybrid Forecast
                           |
                +----------+----------+
                |                     |
                v                     v
        Sentiment Adjustment    SHAP Explanations
```

The sentiment-analysis workflow operates separately from the three base forecasting models. Its output is incorporated as a post-processing adjustment rather than being directly supplied as a trained input feature to every base model.

## Model Evaluation

The forecasting approach uses chronological data splits to preserve temporal order.

The models are evaluated using:

| Metric | Purpose |
|---|---|
| MAE | Average absolute prediction error |
| RMSE | Penalizes larger prediction errors |
| MAPE | Average absolute percentage error |

Expanding-window walk-forward validation is used to assess model performance across successive time periods.

## Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite, Tailwind CSS |
| Backend | Java, Spring Boot, REST APIs |
| ML Service | Python, FastAPI, Uvicorn |
| Machine Learning | TensorFlow/Keras, XGBoost, Scikit-learn, Statsmodels |
| Data Processing | Pandas, NumPy |
| Explainability | SHAP |
| Sentiment Analysis | Hugging Face Transformers, Google News RSS |
| Database | MongoDB Atlas |
| Authentication | Clerk |
| Visualization | Chart.js, Framer Motion |
| Deployment | AWS EC2, Render |

## Repository Structure

```text
hybrid-stock-forecast/
├── frontend/
│   ├── src/
│   ├── package.json
│   └── vite.config.ts
│
├── backend/
│   ├── src/
│   ├── pom.xml
│   └── mvnw
│
├── ml/
│   ├── app/
│   │   ├── predictor.py
│   │   └── utils/
│   └── requirements.txt
│
├── docs/
├── notebooks/
└── README.md
```

## Project Scope

This repository contains selected frontend, backend, and machine-learning project components for exploration and reference.

**Note:** This repository is an incomplete showcase snapshot. Configuration, service entry points, and integration components may be unavailable. The application is not guaranteed to run as-is.

## Disclaimer

This project is intended for educational and research purposes. Stock forecasts are estimates and are not guaranteed to predict future market movements. Nothing in this project constitutes financial advice.
