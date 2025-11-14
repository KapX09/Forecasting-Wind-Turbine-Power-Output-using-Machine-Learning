# Forecasting-Wind-Turbine-Power-Output-using-Machine-Learning
A predictive model that estimates the power output of a wind turbine using weather and turbine parameters such as wind speed, air temperature, humidity, and pressure.

### Project Overview
This project predicts the power output of a wind turbine based on operational parameters such as wind speed and wind direction. It uses machine learning models (Linear Regression and XGBoost) to estimate power output and provides an easy-to-use Streamlit interface for real-time predictions.

[wind turbine power prediction app](https://forecasting-wind-turbine-power-output-using-machine-learning-a.streamlit.app/). Check this out!

---

#### DATASET - The Wind Turbine Scada Dataset
(https://www.kaggle.com/datasets/berkerisen/wind-turbine-scada-dataset)

In Wind Turbines, Scada Systems measure and save data's like wind speed, wind direction, generated power etc. for 10 minutes intervals. This file was taken from a wind turbine's scada system that is working and generating power in Turkey.

---
## Project Structure
```
project-root/
├── data/
│ └── WindTurbine_Data.csv ← Raw dataset (not deployed)
├── notebooks/
│ └── training_notebook.ipynb ← Full EDA + model training notebook
├── models/
│ ├── wind_power_model.pkl ← Saved best model + preprocess function
│ ├── preprocess_input.pkl ← Preprocessing function
│ └── model_metadata.pkl ← Features and performance metrics
├── app/
│ └── streamlit_app.py ← Deployment UI script
├── requirements.txt ← Required Python libraries
└── README.md ← Project documentation
```

---

## Dataset
- **WindTurbine_Data.csv** contains:
  - `Date/Time` — timestamp of observation
  - `Wind Speed (m/s)` — wind speed
  - `LV ActivePower (kW)` — actual turbine power output
  - `Theoretical_Power_Curve (KWh)` — ideal turbine power curve
  - `Wind Direction (°)` — wind direction

---

## Features and Preprocessing
The following engineered features are used for modeling:

- `Wind_Speed_Cubed` — cubic of wind speed (aerodynamic relation)
- `Dir_Sin`, `Dir_Cos` — sine and cosine of wind direction (handles circularity)
- `Rolling_Speed` — rolling mean of wind speed for short-term stability

The preprocessing function (`preprocess_input.pkl`) handles new user inputs in the same way.

---

## Model Training
- **Models used:**
  - Linear Regression (baseline)
  - XGBoost Regressor (non-linear)
- **Train/Test Split:** 80% train, 20% test (time-based)
- **Evaluation Metrics:**
  - RMSE, MAE, R²
- Best model selection is automatic based on RMSE.

---

## Requirements
To install all required libraries, run:

    pip install -r requirements.txt

### Key Libraries
- numpy
- pandas
- scikit-learn
- xgboost
- streamlit
- joblib

### Optional Libraries (for EDA and Colab deployment)
- matplotlib – for plotting in notebooks
- seaborn – for correlation and heatmaps
- pyngrok – to expose Streamlit app publicly from Colab

---
