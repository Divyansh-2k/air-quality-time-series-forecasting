# air-quality-time-series-forecasting
Time-series forecasting of daily PM2.5 concentrations using ARIMA, Holt-Winters ETS, and Prophet.
# Air Quality Time-Series Forecasting

## Overview

This project focuses on forecasting air quality in India using historical PM2.5 concentration data. It implements and compares three time-series forecasting models — ARIMA, Holt-Winters Exponential Smoothing (ETS), and Prophet — to evaluate their performance on daily air-quality observations.

## Dataset

- **Source:** [Air Quality Data in India — Kaggle](https://www.kaggle.com/datasets/fedesoriano/air-quality-data-in-india)
- **Target variable:** PM2.5 concentration (µg/m³)
- **Time period:** 2017–2022
- **Frequency:** Daily averages

### Attributes

- `Timestamp`: Date and hour of the measurement
- `Year`: Year of the measurement
- `Month`: Month of the measurement
- `Day`: Day of the measurement
- `Hour`: Hour of the measurement
- `PM2.5`: Fine particulate matter concentration in the air

The project uses PM2.5 concentration as the target variable for forecasting.

## Methodology

### 1. Data Preprocessing

- Converted the `Timestamp` column to a datetime index.
- Handled missing PM2.5 values using time-based interpolation, followed by backward and forward filling.
- Resampled the data into daily average PM2.5 concentrations.
- Split the time series chronologically, using the final 30 days as the test set and the preceding observations as the training set.

### 2. Forecasting Models

**ARIMA (Auto-Regressive Integrated Moving Average)**

A statistical forecasting model that captures temporal dependencies through autoregression, differencing, and moving-average components.

**Holt-Winters Exponential Smoothing (ETS)**

A forecasting method that models the level and trend of a time series, with a seasonal component to capture recurring patterns.

**Prophet**

An additive forecasting model that represents a time series using trend and seasonality components.

### 3. Evaluation

The models were evaluated using Root Mean Squared Error (RMSE). Forecast plots, residual plots, and a model-comparison chart were used to examine their performance.

## Results

The original experiment reported the following RMSE values:

| Model | RMSE |
|---|---:|
| ARIMA | 4.40 |
| Holt-Winters ETS | 4.05 |
| Prophet | 12.69 |

Holt-Winters ETS achieved the lowest reported RMSE, followed by ARIMA. Prophet had a substantially higher RMSE on the selected test period.

Lower RMSE indicates a smaller magnitude of prediction error on the evaluated observations.

## Technologies Used

- **Language:** Python
- **Data Processing:** Pandas, NumPy
- **Forecasting:** Statsmodels (ARIMA and ETS), Prophet
- **Evaluation:** Scikit-learn
- **Visualization:** Matplotlib
- **Environment:** Google Colab / Jupyter Notebook

## How to Run

1. Download the dataset from the [Kaggle dataset page](https://www.kaggle.com/datasets/fedesoriano/air-quality-data-in-india).
2. Install the required Python libraries:

   ```bash
   pip install pandas numpy matplotlib scikit-learn statsmodels prophet
   ```

3. Open `air_quality_forecasting.ipynb` in Google Colab or Jupyter Notebook.
4. Make the downloaded CSV file available to the notebook. Update the file path or upload logic if necessary.
5. Run the notebook cells in order to preprocess the data, fit the models, calculate RMSE, and generate visualizations.

## Limitations

- The experiment focuses on a single variable: PM2.5 concentration.
- Model performance was evaluated using a single 30-day holdout period.
- The reported results come from the original experiment; preprocessing and evaluation choices may require further validation before drawing broader conclusions.

## Author

**Divyansh Sharma**
