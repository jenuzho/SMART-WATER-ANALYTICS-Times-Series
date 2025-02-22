# 🌊 WATER ANALYSIS TIME SERIES

## 📖 Project Overview

This project aims to analyze the **relationship between precipitation and lake levels** using **time-series forecasting**. We leveraged **historical hydrological and meteorological data** to develop predictive models for **lake level variations** over time.

### 🔍 **Main Objectives**
✅ Understand how **rainfall impacts lake levels**.  
✅ Identify **seasonal patterns and trends** in water levels.  
✅ Develop predictive models to **forecast lake levels 90 days ahead**.  

---

## 📊 **Dataset & Preprocessing**

The dataset used comes from **Kaggle's Acea Water Prediction competition**, specifically the **Lake Bilancino dataset**. The key features analyzed include:

- **Precipitation Data**: Rainfall from multiple stations (San Piero, Mangona, S. Agata, Cavallina, Le Croci).
- **Temperature Data**: Recorded at Le Croci.
- **Lake Level Data**: The dependent variable (target) to predict.
- **Flow Rate Data**: Measures water discharge from the lake.

### ⚙️ **Data Cleaning & Feature Engineering**
✔ **Handled missing values** with forward-fill (`ffill`) and backward-fill (`bfill`).  
✔ **Detected and treated outliers** using IQR-based capping.  
✔ **Checked for stationarity** (ADF Test) and applied transformations where needed.  
✔ **Created lagged features** and **rolling averages** to enhance model performance.  

---

## 📈 **Models Used for Forecasting**
We implemented and compared **three forecasting models**:

| Model        | Strengths | Weaknesses |
|-------------|-----------|------------|
| **SARIMA**  | Captures trend & seasonality well | Computationally expensive for long-term forecasts |
| **Prophet** | Handles missing data & seasonal trends well | Less accurate in short-term predictions |
| **XGBoost** | Best for complex non-linear relationships | Requires extensive feature engineering |

**🏆 Final Model Selected: `XGBoost`**  
- It provided the **best accuracy** while maintaining computational efficiency.  
- Predicts **lake levels 90 days ahead** with optimized hyperparameters.  

---

## 📊 **Results & Findings**
✅ **Significant correlation** found between rainfall and lake level variations.  
✅ **Seasonality detected**, showing cyclic patterns in water levels.  
✅ **Lag effects confirmed**, with rainfall impacting lake levels **days later**.  
✅ **XGBoost provided the most stable predictions**, capturing **non-linear dependencies**.  

### 📉 **Final Forecast (90 Days Ahead)**
We predicted **lake levels for the next 90 days** using XGBoost, visualized alongside historical trends. The final forecast showed **reasonable fluctuations**, closely following seasonal behavior.

---

## ❗ **Why the Model & ZIP File Were Not Uploaded**
The trained XGBoost model (`xgboost_model.pkl`) and any large ZIP files were **not uploaded** due to **GitHub storage limitations**:

- **GitHub has a 100MB file size limit**, and model files can be large.
- Instead, we saved the model **locally** (`XGboost_Model/`) and added it to `.gitignore`.
- Users can **retrain the model** using the provided training script.

🔹 **To reload the model:**  
```python
import joblib
model = joblib.load("XGboost_Model/xgboost_model.pkl")
