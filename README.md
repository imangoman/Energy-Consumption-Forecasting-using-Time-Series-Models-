# 📈 Energy Consumption Time Series Forecasting

This project explores time series forecasting of monthly energy consumption using three modeling approaches:

- **SARIMA (Seasonal ARIMA)**
- **Facebook Prophet**
- **LSTM (Long Short-Term Memory Neural Network)**

We aim to compare the models on predictive performance and visualize future trends in energy usage from 2010 to 2023.

---

## 📁 Project Structure

```bash
energy-forecasting/
├── energy.csv                         # Input dataset (monthly energy consumption)
├── energy_consumption_timeseries.ipynb  # Main notebook with all models and analysis
├── energy_consumption_timeseries.html   # Exported notebook as HTML
└── README.md                          # This file
```

---

## 🗃️ Dataset

- **File**: `energy.csv`
- **Columns**:  
  - `Time`: Date (monthly, from 2010 to 2023)  
  - `Value`: Monthly energy consumption value
- **Frequency**: Monthly (`MS`)
- **Shape**: ~168 rows × 2 columns

---

## 🔍 Models & Methodology

### 🧹 Preprocessing
- Converted `Time` column to datetime and set as index
- Log transformation used for SARIMA
- MinMax scaling applied for LSTM input
- Train-test split: last 12 months held out for evaluation

### 📉 Forecasting Models

| Model    | Description |
|----------|-------------|
| **SARIMA** | Seasonal ARIMA(0,1,2)(1,0,0,12) for trend + seasonal components |
| **Prophet** | Automatic seasonality, trend changepoints, holiday support |
| **LSTM** | Deep learning model trained on sliding 24-month windows with early stopping |

---

## 📊 Evaluation Metrics (on last 12 months)

| Metric     | SARIMA    | Prophet     | LSTM        |
|------------|-----------|-------------|-------------|
| RMSE       | *~4900*   | 5061.88     | *~5200*     |
| MAE        | *~4300*   | 4467.34     | *~4700*     |
| MAPE       | *~7.5%*   | 8.07%       | ~11.00%     |
| Accuracy   | *~92.5%*  | 91.93%      | 89.00%      |

> Note: SARIMA and LSTM metrics vary slightly based on parameters and runtime conditions.

---

## 📈 Visual Outputs

- **Actual vs Forecast** plots for each model (last 12 months)
- **Full-series overlays** showing model fit
- **Prophet component plots**: trend, seasonality, holidays
- **LSTM** visualization with 24-month rolling input

---

## 🛠 Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels prophet keras tensorflow
```

---

## 🚀 How to Run

1. Open `energy_consumption_timeseries.ipynb` in Jupyter Notebook or VSCode.
2. Execute each cell sequentially.
3. Visualize performance of SARIMA, Prophet, and LSTM.
4. Compare metrics and export results if needed.

---

## 💡 Key Insights

- **Prophet** provides strong interpretability and seasonal detection.
- **SARIMA** performs competitively with low tuning effort.
- **LSTM** captures temporal dependencies but may require careful tuning for optimal accuracy.

---

## 📌 Next Steps

- Add external regressors (e.g., temperature, holidays)
- Tune LSTM hyperparameters (layers, dropout, epochs)
- Try hybrid or ensemble forecasting
- Deploy as a Flask/Dash app for real-time prediction
