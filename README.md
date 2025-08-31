# Covid19-Death-prediction
This project focuses on predicting COVID-19 confirmed cases globally using machine learning methods
COVID-19 Time Series Forecasting (Global Case Study)

This project focuses on predicting COVID-19 confirmed cases globally using machine learning methods. We applied time series feature engineering, classical ML regressors (Random Forest, XGBoost), and a hybrid ensemble approach for better accuracy.

📌 Project Workflow
1. Data Preparation

Dataset: COVID-19 daily confirmed cases with columns like:

ObservationDate

Country/Region

Confirmed

Sorting: Data was sorted by Country/Region and ObservationDate to maintain chronological order.

Aggregation: For global modeling, confirmed cases were summed across countries per day.

2. Feature Engineering

To capture temporal dependencies:

Lag Features:

Confirmed_lag1: Previous day’s confirmed cases.

Confirmed_lag7: Confirmed cases 7 days ago.

Rolling Statistics:

Confirmed_rolling7: 7-day moving average.

Future Target:

Confirmed_t7: Cases shifted by 7 days (forecast horizon).

These features allow the model to learn patterns like daily momentum and weekly seasonality.

3. Train-Test Split

Date-based split (no random shuffle, since this is time series).

Training set: Before October 1, 2020.

Testing set: On and after October 1, 2020.

This ensures predictions simulate real-world forecasting (no data leakage from the future).

4. Model Training

We trained two ML regressors:

Random Forest Regressor

Captures nonlinearities and interactions between lag features.

Works well with tabular data, robust to outliers.

Baseline model for comparison.

XGBoost Regressor

Gradient boosting model, excellent at capturing complex patterns.

Often outperforms Random Forest in structured/tabular data.

Used tuned hyperparameters for better performance.

5. Evaluation Metrics

Models were evaluated using:

RMSE (Root Mean Squared Error) → Penalizes large errors.

R² (Coefficient of Determination) → How much variance is explained.

MAPE (optional) → Percentage error for interpretability.

6. Visualization

Plotted Actual vs Predicted curves.

Compared:

Actual cases (blue line).

Random Forest predictions (green dashed).

XGBoost predictions (red dashed).

This helps visually assess model performance.

7. Hybrid Ensemble

To improve accuracy:

Created a hybrid model by averaging Random Forest and XGBoost predictions:

Ensemble
=
RF Predictions
+
XGB Predictions
2
Ensemble=
2
RF Predictions+XGB Predictions
	​


Benefits:

Smooths errors of individual models.

Improves stability and robustness.

Plotted ensemble alongside RF, XGB, and actual values.

📊 Key Results

Random Forest: Provided a strong baseline but sometimes under/overfitted peaks.

XGBoost: More accurate at capturing nonlinear patterns.

Hybrid Ensemble: Best trade-off between the two, smoother and closer to actual values.

🚀 Next Steps (if time permits)

Try weighted hybrid (give more weight to the better-performing model).

Experiment with deep learning (LSTM, GRU, Transformers) for sequential learning.

Perform hyperparameter tuning with RandomizedSearchCV + TimeSeriesSplit.

Extend to per-country forecasting and then aggregate for global predictions.

📝 Interview Talking Points

Why lag features? → To encode temporal dependencies.

Why train-test by date? → Prevents data leakage from the future.

Why ensemble? → Reduces variance and leverages strengths of multiple models.

Why RF + XGB? → Random Forest is robust; XGBoost is accurate — ensemble combines both.

Metrics choice? → RMSE penalizes large errors, R² explains variance captured.


chatlink:https://chatgpt.com/share/68b3bdd8-68c4-8011-b297-2df9a0839647
