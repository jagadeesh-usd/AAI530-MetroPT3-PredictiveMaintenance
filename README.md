# AAI-530 Final Project: IIoT Predictive Maintenance System

**Course:** AAI-530: AI for IoT
**Student:** Jagadeesh Kumar Sellappan
**University:** University of San Diego
**Dataset:** MetroPT-3 (UCI Machine Learning Repository)

## Project Overview

This project designs and implements a Predictive Maintenance System 
for Air Production Units (APU) on metro trains using LSTM-based deep 
learning. Two complementary models detect anomalies and forecast 
compressor pressure to provide advance warning before failures occur.

## Key Results

- 4/4 failure events detected with 3–7 days advance warning
- Model A threshold: 0.0280 (mean + 3σ)
- Model B forecast: MAE 0.1378, R² 0.4168
- Average lead time: 140.3 hours

## Dataset

**MetroPT-3 Dataset** — real operational metro train, Porto, Portugal

- Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/791/metropt+3+dataset)
- Frequency: ~10-second intervals
- Size: 1,516,948 observations (Feb–Sep 2020)
- Resampled to: 1-minute intervals (306,960 rows)
- Features: 7 continuous sensors + 8 binary signals

## Notebooks

| Notebook | Description |
|---|---|
| 01_EDA_and_Preprocessing.ipynb | Data exploration, validation, resampling |
| 02_Model_A_Anomaly_Detection.ipynb | LSTM Autoencoder anomaly detection |
| 03_Model_B_Forecasting.ipynb | LSTM Forecaster for TP2 pressure |

## Machine Learning Models

### Model A: LSTM Autoencoder (Anomaly Detection)
- Architecture: LSTM(64)→Dropout(0.2)→LSTM(32)→RepeatVector→LSTM(32)→LSTM(64)→Dense(7)
- Training: Healthy data only (Feb–Apr 2020)
- Threshold: Mean + 3σ = 0.0280

### Model B: LSTM Forecaster (Time-Series Prediction)
- Architecture: LSTM(64)→Dropout(0.3)→LSTM(32)→Dropout(0.2)→Dense(16)→Dense(1)
- Target: TP2 compressor pressure, 10 minutes ahead

## IoT Architecture

Four-layer IIoT design:
1. Edge & Ingestion — Industrial sensors + AWS IoT Greengrass
2. Real-Time Operations — AWS IoT Core + AWS Timestream (Hot Path)
3. ML Pipeline — Snowflake + SageMaker (Cold Path)
4. Visualization — Tableau Public Dashboard

## Dashboard

**Tableau Public:** [https://public.tableau.com/app/profile/jagadeesh.sellappan/viz/APUPredictiveMaintenanceDashboard/Dashboard1]

Five visualizations:
1. KPI Summary — Total failures detected, avg lead time
2. Lead Time Summary — Warning hours per failure event
3. Anomaly Detection — Reconstruction error vs threshold
4. Historical System Health — Raw TP2 pressure timeline
5. 10-Minute Pressure Forecast — Actual vs predicted TP2

## How to Run

1. Open notebooks in Google Colab
2. Mount Google Drive
3. Run cells in order: EDA → Model A → Model B

## Requirements

- Python 3.10
- TensorFlow 2.x
- pandas, NumPy, scikit-learn
- matplotlib, seaborn

## License
