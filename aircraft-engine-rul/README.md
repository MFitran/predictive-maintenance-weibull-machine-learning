# Aircraft Engine Remaining Useful Life (RUL) Prediction

This project focuses on the benchmark NASA C-MAPSS dataset to predict the Remaining Useful Life (RUL) of turbofan engines. The research provides a systematic comparative analysis of 12 unique preprocessing pipelines paired with three distinct machine learning regressors.

## 🎯 Research Objective
The primary objective of this study is to formulate and apply machine learning to the Weibull scale parameter ($\lambda$), transforming it from a traditionally rigid parameter into a dynamic, data-driven variable. This methodology allows for a more adaptive and accurate failure probability assessment, moving beyond static historical averages to reflect the actual operational state of the system.

## 🛠 Project Environment
> **Note:** These notebooks were developed using **Google Colab** connected to **Google Drive**. 
> 
> If you are running this locally:
> 1. Adjust the file paths in the `pd.read_csv()` and `pd.to_csv()` functions.
> 2. Comment out or remove the `drive.mount('/content/gdrive')` cells.
> 3. Ensure your local directory structure matches the script's expectations.

---

## 📊 Methodology & Pipelines
The core of this research is the evaluation of how preprocessing affects model performance. We tested **12 distinct pipelines**:

### 1. Preprocessing Combinations
* **Denoising Methods:** Moving Average, Exponentially Weighted Moving Average (EWMA), Wavelet Denoising, and No Denoising.
* **Feature Scaling:** Standardization, Min-Max Scaling, and Robust Scaling.

### 2. Regressor Models
* **Linear Regression:** Baseline statistical model.
* **XGBoost:** High-performance gradient boosting.
* **K-Nearest Neighbors (KNN):** Distance-based non-parametric regressor.

---

## 🚀 How to Download and Train

### Step 1: Obtain the Dataset
1. Visit the [NASA Prognostics Data Repository](https://data.nasa.gov/dataset/cmapss-jet-engine-simulated-data/resource/5224bcd1-ad61-490b-93b9-2817288accb8).
2. Download the **Turbofan Engine Degradation Simulation Data Set (C-MAPSS)**.
3. Extract the files (e.g., `train_FD001.txt`, `test_FD001.txt`, `RUL_FD001.txt`).

### Step 2: Set Up Directory
Place the extracted `.txt` files into a folder named `data/` within this project directory. If using Colab, upload these to your specific Google Drive folder.

### Step 3: Run the Notebooks
1.  **Open `01_data_exploration.ipynb`:** Use this to visualize sensor trends and understand the degradation curves of the turbofan units.
2.  **Open `02_model_training.ipynb`:** * Change the `root_path` variable to point to your data location.
    * The script is designed to iterate through all 12 preprocessing pipelines.
    * **Training:** Execute the cells to train the models. The notebook will automatically calculate performance metrics.

### Step 4: Evaluate Results
The models are evaluated using standard metrics and custom Weibull-specific metrics:
* **Mean Absolute Error (MAE)**
* **Root Mean Square Error (RMSE)**
* **Coefficient of Determination ($R^2$)**
* **Weibull Error:** Measures the deviation between the predicted $\lambda$ and the actual time-to-failure.

---

## 📝 Citation
If you use this code or the methodology in your research, please cite ([DOI](https://doi.org/10.48084/etasr.15186)):
> M. F. Ramadhan, N. D. Nozyra, F. A. A. W. Putra, S. M. Nasution, and R. R. Septiawan, “Machine Learning for Covariate-Driven Changes in Weibull Scale Parameter”, Eng. Technol. Appl. Sci. Res., vol. 16, no. 1, pp. 31802–31808, Feb. 2026.
