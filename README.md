# Predictive Maintenance: Weibull-Machine Learning Framework

This repository explores the integration of **Machine Learning** with the **Weibull Distribution** to improve the accuracy of Remaining Useful Life (RUL) estimations. By treating the Weibull scale parameter ($\lambda$) as a dynamic target for regression, these projects bridge the gap between statistical reliability analysis and modern data-driven maintenance.

---

## 🛠 Project Environment & Setup
**Important Note on Execution:**
These projects were developed using **Google Colab** connected to a local **Google Drive** for dataset storage. 
* **Path Management:** If you wish to run these notebooks locally or in another cloud environment, you **must** adjust the file paths in the data loading cells (e.g., `pd.read_csv`).
* **G-Drive Mounting:** The code contains `drive.mount('/content/gdrive')`. Replace this with local directory paths if you are not using Colab.
* **Dependencies:** Run `pip install -r requirements.txt` to install necessary libraries including `lifelines`, `xgboost`, `lightgbm`, and `scikit-learn`.

---

## 📊 The Weibull Distribution in Maintenance
The Weibull distribution is a versatile tool used to model the life cycle and failure rates of mechanical components.

### 1. Probability Density Function (PDF)
The PDF represents the probability of failure occurring at a specific time $t$. 
$$f(t; k, \lambda) = \frac{k}{\lambda} \left( \frac{t}{\lambda} \right)^{k-1} e^{-(t/\lambda)^k}$$

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/755c61ad-7bd7-4bf0-a3f8-c003586115c5" />

### 2. Cumulative Distribution Function (CDF)
The CDF represents the cumulative probability that a component has failed by time $t$. This is used to determine the unreliability of the system.
$$F(t; k, \lambda) = 1 - e^{-(t/\lambda)^k}$$

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/b9e4ff99-d4c5-4827-9501-0eb57496810e" />

### 3. Development of Weibull Error Metrics
The Weibull Error Metrics was developed to evaluate performance of all machine learning models trained in this research. More on this is discussed on this [Journal titled "Machine Learning for Covariate-Driven Changes in Weibull Scale Parameter"](https://doi.org/10.48084/etasr.15186).
1. Weibull Error (WE)
 - $WE(t_i,\ \ \lambda,\ \ k)=t+\frac{2\lambda}{k}\mathrm{\Gamma}\left(\frac{1}{k},\left(\frac{t}{\lambda}\right)^k\right)-\frac{\lambda}{k}\mathrm{\Gamma}\left(\frac{1}{k}\right)$
 - $MWE=\frac{1}{n}\sum_{i=1}^{n}{WE(t_i,\ \ \lambda,\ \ k)}$
2. Quadratic Weibull Error (QWE)
 - $QWE(t_i,\ \ \lambda,\ \ k)=t+\frac{2\lambda}{k}\mathrm{\Gamma}\left(\frac{1}{k},\left(\frac{t}{\lambda}\right)^k\right)-\frac{\lambda}{k}\mathrm{\Gamma}\left(\frac{1}{k}\right)+\frac{\lambda}{k2^{\frac{1}{k}}}\mathrm{\Gamma}\left(\frac{1}{k}\right)$
 - $MQWE=\frac{1}{n}\sum_{i=1}^{n}{QWE(t_i,\ \ \lambda,\ \ k)}$
3. Right Weibull Error
  - $RWE(t_i,\ \ \lambda,\ \ k)=\frac{\lambda}{k}\mathrm{\Gamma}\left(\frac{1}{k},\left(\frac{t}{\lambda}\right)^k\right)$
  - $MRWE=\frac{1}{n}\sum_{i=1}^{n}{RWE(t_i,\ \ \lambda,\ \ k)}$ 
4. Left Weibull Error
 - $LWE(t_i,\ \ \lambda,\ \ k)=t+\frac{\lambda}{k}\mathrm{\Gamma}\left(\frac{1}{k},\left(\frac{t}{\lambda}\right)^k\right)-\frac{\lambda}{k}\mathrm{\Gamma}\left(\frac{1}{k}\right)$
 - $MLWE=\frac{1}{n}\sum_{i=1}^{n}{LWE(t_i,\ \ \lambda,\ \ k)}$

<img width="526" height="321" alt="image" src="https://github.com/user-attachments/assets/9e15249a-9692-4309-ac55-e668933d8ac5" />


**Key Parameters:**
* **$k$ (Shape):** Determines the failure behavior (Infant mortality if $k<1$, random if $k=1$, and wear-out if $k>1$).
* **$\lambda$ (Scale):** Represents the characteristic life; the point in time where 63.2% of the units are expected to have failed.

---

## 🎯 Objectives

the main objective of this study is to develop and apply machine learning on a Weibull Scale Parameter ($\lambda$). From a static parameter to a dynamic, covariate-driven estimate,. this could hypotethically gives a more accurate percentage-based assessment of a system's Remaining Useful Life (RUL).

### 1. [Aircraft Engine RUL Prediction](./dir01-aircraft-engine-rul/)
Based on the research: *"A Comparative Analysis of Machine Learning Models for Aircraft Engine Remaining Useful Life Prediction."*
* **Objective:** Comparative study of 12 unique preprocessing pipelines.
* **Models:** Linear Regression, XGBoost, and K-Nearest Neighbors (KNN).
* **Datasets:** NASA C-MAPSS (Turbofan Engine Degradation).

### 2. [Tire Maintenance System](./dir02-tire-degradation/)
Based on the research: *"Hybrid ML-Weibull Predictive Maintenance System for Dynamic Tire Remaining Useful Life Estimation."*
* **Objective:** Using an edge-cloud architecture to dynamically predict the Weibull $\lambda$ parameter.
* **Hardware context:** ESP32-S3 gateway capturing TPMS, OBD-II, and GPS data.
* **Innovation:** Treating $\lambda$ as a dynamic covariate influenced by real-time operational stressors.

---

## 📂 Repository Structure

predictive-maintenance-weibull-machine-learning/
- dir00-learning-weibull-distribution
  - README.md
  - nb00_probability_distribution.ipynb
  - nb01_weibull_distribution.ipynb
- dir01-aircraft-engine-rul/
  - CMAPPSData.zip
  - README.md 
  - nb00_model_training.ipynb
  - nb01_prediction_visualization.ipynb
- dir02-tire-degradation/ 
  - data/
    - vehicle_logs_rows.csv
    - vehicle_logs_tread_14_1.csv
    - vehicle_logs_tread_14_2.csv
    - vehicle_logs_tread_21.csv
    - vehicle_logs_tread_24_1.csv
    - vehicle_logs_tread_24_2.csv
  - nb00_fix_sensor_reading.ipynb
  - nb01_model_training_experimentation.ipynb
  - nb02_model_training_evaluation.ipynb
- .gitignore
- requirements.txt
- README.md
