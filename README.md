# Predictive Analytics Using Historical Data

## Project Objective

Build a predictive analytics system using historical sales data to identify trends, evaluate predictive models, and forecast future sales for the next 30 days.

## Task Requirements

- Clean and preprocess historical data
- Perform trend and exploratory analysis
- Use regression and time-series models for prediction
- Evaluate model performance
- Visualize actual and predicted values
- Generate a future 30-day forecast

## Dataset

The dataset contains historical daily sales information for:

- Product: 1 product
- Store: 1 store
- Period: January 2018 to December 2020
- Original records: 1,080
- Calendar gap identified: February 29, 2020

The missing calendar date was handled during preprocessing to create a continuous daily time series.

## Data Preprocessing

The project includes:

- Date conversion and validation
- Missing-value checks
- Duplicate checks
- Calendar-gap detection
- Missing-date handling
- Outlier analysis
- Time-based feature engineering

## Feature Engineering

The predictive models use:

- Day of week
- Month
- Day
- Day of year
- Week of year
- Month-end indicator
- Lag 1
- Lag 7
- Lag 14
- Lag 30
- 7-day rolling mean
- 30-day rolling mean

The `Year` feature was intentionally excluded to avoid relying on an unseen future year during forecasting.

## Models

The project compares multiple approaches:

### Regression Models

- Linear Regression
- Random Forest Regression
- Tuned Random Forest Regression

### Time-Series Models

- Holt-Winters
- SARIMA

### Baseline Methods

- Naive last-value forecast
- Seasonal naive last-week forecast
- Last-year smoothed forecast

## Model Evaluation

A chronological train-test split was used for one-step-ahead evaluation.

For realistic long-horizon forecasting, four consecutive 30-day backtesting windows were used.

Evaluation metrics:

- MAE — Mean Absolute Error
- RMSE — Root Mean Squared Error
- MAPE — Mean Absolute Percentage Error
- R² — R-squared

## Backtesting Results

The tuned Random Forest was selected based on the lowest average RMSE across the 30-day backtesting windows.

| Model | MAE | RMSE | MAPE |
|---|---:|---:|---:|
| Random Forest (tuned) | 685 | 950 | 15.8% |
| Last year (7-day smoothed) | 742 | 963 | 15.7% |
| Holt-Winters | 862 | 1027 | 24.1% |
| Linear Regression | 949 | 1086 | 24.6% |
| SARIMA | 936 | 1102 | 27.6% |
| Naive (last value) | 857 | 1167 | 17.4% |
| Seasonal naive (last week) | 1142 | 1515 | 33.2% |

Random Forest achieved 7.8% lower MAE and 1.4% lower RMSE than the best baseline. The baseline had slightly lower MAPE, which is also reported for transparency.

## Forecast

A 30-day recursive forecast was generated for:

**December 17, 2020 – January 15, 2021**

- Average predicted value: approximately 3,110
- Peak predicted value: approximately 3,357
- Peak date: January 6, 2021

## Visualization

The notebook includes visualizations for:

- Historical sales trends
- Monthly trends
- Year-over-year seasonal patterns
- Actual vs predicted values
- 30-day backtesting results
- Final historical data and future forecast

## Project Files

- `Sales_Forecasting.ipynb` — Complete analysis and forecasting notebook
- `dataset.csv` — Historical dataset
- `30_Day_Sales_Forecast.csv` — Generated 30-day forecast

## Limitations

This dataset contains only one product and one store. The model does not include external variables such as promotions, prices, holidays, weather, or marketing campaigns.

Forecast uncertainty may increase as the prediction horizon becomes longer because recursive forecasting uses previous predictions as inputs.

## Conclusion

This project demonstrates an end-to-end predictive analytics workflow covering data preprocessing, exploratory analysis, feature engineering, regression, time-series forecasting, model evaluation, backtesting, and future prediction.

The final forecast provides a data-driven estimate of sales for the following 30 days based on historical patterns.
