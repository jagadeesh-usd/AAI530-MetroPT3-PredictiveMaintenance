# AAI-530 Final Project: IIoT Predictive Maintenance System

**Course:** AAI-530: AI for IoT  
**Student:** Jagadeesh kumar Sellappan  
**Dataset:** MetroPT-3 (UCI Machine Learning Repository)

## Project Overview
This project focuses on the design and implementation of a **Predictive Maintenance System** for Air Production Units (APU) on metro trains. In the manufacturing and transportation industries, unexpected compressor failures lead to costly downtime. This project simulates a real-world IoT pipeline that monitors sensor data to detect anomalies and forecast maintenance needs.

### Key Objectives
1.  **IoT System Design:** Develop a theoretical architecture for collecting, processing, and transmitting high-frequency sensor data from moving trains to the cloud.
2.  **Anomaly Detection (Deep Learning):** Build a model (e.g., LSTM Autoencoder) to classify the system state as "Healthy" or "Failure" based on raw sensor telemetry.
3.  **Predictive Analytics (Time-Series):** Create a regression model to forecast critical variables (e.g., Air Pressure) to anticipate threshold breaches.
4.  **Visualization:** Present real-time status and historical trends via a Tableau Public dashboard.

## Dataset
The project uses the **MetroPT-3 Dataset**, collected from a real operational metro train in Porto, Portugal.
* **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/791/metropt+3+dataset)
* **Data Type:** Multivariate Time-Series
* **Frequency:** 1Hz (1 second intervals)
* **Sensors:** 15 variables including:
    * `TP2` (Compressor Pressure)
    * `TP3` (Pneumatic Panel Pressure)
    * `H1` (Valve Pressure)
    * `Motor_Current` (Ampere)
    * `Oil_Temperature` (Celsius)

## Theoretical IoT Architecture
* **Sensors:** Analog pressure and temperature sensors (4-20mA) wired to the APU.
* **Edge Device:** Onboard Industrial PC performing data aggregation and lightweight anomaly inference.
* **Connectivity:** MQTT protocol over Cellular (4G/5G) for real-time alerts; Wi-Fi for bulk data offloading.
* **Cloud/Storage:** Scalable data warehouse for historical analysis and model retraining.

## Machine Learning Models
This project implements two distinct machine learning tasks as required:

### Model A: Anomaly Detection (Deep Learning)
* **Goal:** Classify current system status as **Normal** or **Potential Failure**.
* **Architecture:** Deep Neural Network (DNN) / LSTM built from scratch using TensorFlow/Keras.
* **Input:** Rolling window of sensor readings (e.g., last 60 seconds).

### Model B: Time-Series Forecasting
* **Goal:** Predict the value of **Compressor Pressure (TP2)** for the next time horizon.
* **Method:** Time-series regression (e.g., LSTM or ARIMA).
* **Utility:** Allows operators to see if pressure is trending toward a safety cutoff.

## Dashboard
The final insights are visualized on Tableau Public.
* **Link:** 
* **Visuals:**
    * Real-time device status (Active/Warning).
    * Historical pressure and temperature trends.
    * Predicted failure probability vs. actual events.

## How to Run the Code

## License

