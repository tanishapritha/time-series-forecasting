# Time Series Forecasting Project

### Overview
This project predicts revenue using past revenue data with various models.  
It also explains key time series models and parameters in simple terms.

---

### Workflow

1. Upload CSV to Colab
2. Clean data:
   - Remove missing or infinite values
   - Convert dates to datetime
3. Visualize revenue over time
4. Check stationarity:
   - Use ADF test
   - Difference if necessary
5. Split data: 80% train, 20% test
6. Fit model on training data
7. Predict revenue for test period
8. Compare predictions with actual values
9. Evaluate performance using RMSE and MAE
---

### Libraries
```
pandas, numpy, matplotlib, statsmodels, sklearn.metrics
```

---

### Time Series Models Explained

#### 1. AutoRegressive (AR)
```
- Predicts the next value using past values in the series
- Parameter:
  - p → Number of past steps (lags) to use
- Example: AR(p=3) uses the last 3 values to predict today
```

#### 2. Moving Average (MA)
```
- Predicts the next value using past errors (residuals)
- Parameter:
  - q → Number of past errors to use
- Example: MA(q=2) uses the last 2 prediction errors
```

#### 3. ARMA (AutoRegressive Moving Average)
```
- Combines AR and MA
- Uses both past values and past errors
- Parameters:
  - p → AR lags
  - q → MA lags
- Works for stationary series (no trend or seasonality)
```

#### 4. ARIMA (AutoRegressive Integrated Moving Average)
```
- Handles non-stationary series (with trend)
- Parameters:
  - p → AR lags
  - d → Number of differences to make series stationary
  - q → MA lags
- Example: ARIMA(2,1,2) → 2 AR lags, 1 difference, 2 MA lags
```

#### 5. SARIMA (Seasonal ARIMA)
```
- Extends ARIMA to handle seasonality
- Parameters:
  - (p,d,q) → ARIMA parameters
  - (P,D,Q,m) → Seasonal AR, differencing, MA, and seasonal period
- Example: SARIMA(1,1,1)(1,1,1,12) → captures yearly seasonality (m=12 months)
```

#### Parameters

| Parameter | Meaning                           |
| :-------: | :-------------------------------- |
|   **p**   | AR lags (previous values)         |
|   **d**   | Differencing (to remove trend)    |
|   **q**   | MA lags (previous errors)         |
|   **P**   | Seasonal AR lags                  |
|   **D**   | Seasonal differencing             |
|   **Q**   | Seasonal MA lags                  |
|   **m**   | Seasonal period (e.g., 12 months) |


#### 7. How to Choose
```
1. Plot ACF → helps pick q (MA)
2. Plot PACF → helps pick p (AR)
3. Check for trend → use d if series is non-stationary
4. Check for seasonality → use SARIMA
```

---

### Working
```
AR → past values → predict next
MA → past errors → predict next
ARMA → past values + past errors → predict next
ARIMA → difference to remove trend → ARMA
SARIMA → ARIMA + seasonal patterns (period m)
```

---

### Output
```
- Plots showing actual vs predicted revenue
- Forecast metrics: RMSE, MAE
- Model summary: coefficients, AIC/BIC
```

