### **Hybrid ML-Weibull Predictive Maintenance for Tire RUL**

This project introduces a hybrid framework that integrates Machine Learning with the Weibull reliability distribution to provide dynamic Remaining Useful Life (RUL) estimations for vehicle tires. It utilizes real-world telemetry captured via an edge-cloud architecture to move beyond static maintenance schedules.

## 🎯 Research Objective

The primary objective of this study is to formulate and apply machine learning to the Weibull scale parameter ($\lambda$), transforming it from a traditionally rigid parameter into a dynamic, data-driven variable. By predicting $\lambda$ based on real-time operational stressors—such as tire pressure, temperature, and vehicle load—this methodology allows for a more adaptive and accurate failure probability assessment, reflecting the actual wear trajectory of the tire.

## 🛠 Project Environment

> **Note:** These notebooks were developed using **Google Colab** connected to **Google Drive**.
> If you are running this locally:
> 1. Adjust the file paths in the `pd.read_csv()` functions to point to your local data directory.
> 2. Comment out or remove the `drive.mount('/content/gdrive')` cells.
> 3. Ensure your environment has the dependencies listed in the root `requirements.txt`.
> 
> 

---

## 📊 Methodology & System Architecture

The system employs an **Edge-Cloud architecture** to process disparate data sources into a unified reliability model:

### 1. Data Sources (Edge Gateway)

* **TPMS:** Tire pressure and internal temperature.
* **OBD-II:** Engine load and vehicle speed.
* **GPS:** Distance tracking using the **Haversine Formula** to calculate precise mileage.
* **Hardware:** Data is aggregated via an ESP32-S3 gateway before cloud transmission.

### 2. Machine Learning Regressors

* **XGBoost & LightGBM:** Used to map operational stressors to the Weibull scale parameter ($\lambda$).
* **Bernard's Approximation:** Employed to calculate median ranks for the initial Weibull fitting.

---

## 🚀 How to Run

### Step 1: Obtain the Dataset

1. Use the vehicle logs provided in the `data/raw/` directory or your own captured telemetry (TPMS, OBD-II, and GPS logs).
2. Ensure the data is in `.csv` format as expected by the preprocessing script.

### Step 2: Data Fixing & Preprocessing

**Open `nb00_fix_sensor_reading.ipynb`:**

* This notebook synchronizes time-series data from different sensors.
* It handles missing values and calculates the total mileage per trip.
* **Output:** A cleaned dataset (e.g., `vehicle_logs_tread_total.csv`) ready for modeling.

### Step 3: Model Training & Experimentation

**Open `nb01_model_training_experimentation.ipynb`:**

* Load the processed dataset and define the feature matrix (Load, Speed, Pressure, Temp).
* Train the regressors to predict the dynamic $\lambda$.
* This notebook includes hyperparameter tuning (GridSearch) for **XGBoost** and **LightGBM**.

### Step 4: Visualization & Reliability Mapping

**Open `nb02_model_training_visualization.ipynb`:**

* Use the trained models to generate **Probability Density Function (PDF)** and **Cumulative Distribution Function (CDF)** curves.
* Visualize how the reliability curve "shifts" in real-time as driving conditions change.
* **Export:** The notebook saves the final trained models as `.pkl` files (e.g., `xgboost_grid.pkl`) for deployment.

---

## 📈 Evaluate Results

The performance is validated using standard regression metrics alongside reliability-specific error calculations:

* **MAE, MSE, and RMSE:** General prediction accuracy.
* **$R^2$ Score:** Variance explanation of the regressor.
* **Weibull Error & Quadratic Weibull Error:** Specialized metrics measuring the distance between the predicted reliability curve and the empirical failure data.

---

## Implemantation

Youtube (bahasa) : https://www.youtube.com/watch?v=4htOM1ONs-Q

---

## 📝 Citation

If you use this code or the hybrid methodology in your research, please cite:

> M. F. Ramadhan, F. A. A. W. Putra, N. D. Nozyra, S. M. Nasution, and R. R. Septiawan, “Hybrid ML-Weibull Predictive Maintenance System for Dynamic Tire Remaining Useful Life Estimation,” *International Journal of Information Technology (IJIT)*, 2026.
