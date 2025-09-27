# Hourly Energy Consumption Prediction (XGBoost)

This project demonstrates forecasting of **hourly energy consumption** using the **PJM Hourly Energy Consumption dataset** and **XGBoost regression**.  
The workflow includes preprocessing, **time series cross-validation**, feature engineering, hyperparameter tuning, and forecasting.

---

## 📂 Files

- `PJME_hourly.csv` – Dataset containing hourly energy consumption (MW).  
- `Hourly_Energy_Consumption_Prediction_Using_XGBoost.ipynb` – Jupyter/Colab notebook with the full workflow.  

---

## 📊 Dataset

- **Source**: PJM Interconnection LLC (PJM)  
- **Columns**:
  - `Datetime`: Timestamp (hourly)  
  - `PJME_MW`: Energy consumption in megawatts  

⚠️ Note: Data covers ~10 years but availability may vary by region and time.

---

## 🛠️ Project Workflow

### 1. Data Preprocessing
- Load PJM dataset.  
- Convert `Datetime` column to datetime dtype and set as index.  
- Remove outliers (`PJME_MW < 19,000`).  

### 2. Time Series Cross Validation
- Apply **`TimeSeriesSplit`** from `sklearn.model_selection`.  
- Ensure validation sets always follow training sets.  

### 3. Feature Engineering
- Extract time-based features (hour, day, month, year).  
- Capture daily, weekly, and seasonal consumption patterns.  

### 4. Hyperparameter Tuning
- Tune **`n_estimators`** using cross-validation.  
- Select the value minimizing validation error (MSE).  

### 5. Final Model Training
- Retrain the XGBoost regression model on the **entire dataset** with the best hyperparameters.  

### 6. Forecasting
- Create a **future dataframe** by extending timestamps.  
- Predict future hourly energy consumption.  

### 7. Visualization
- **Final visualization comparing historical values (blue) with the forecasted values (purple).**  
