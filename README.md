# SKU-Level Sales Forecasting in Grocery Retail (Regularization & ML Comparison)

This project develops and compares forecasting models to predict weekly SKU-level sales for orange juice across 10 stores, using scanner data from Dominick’s Finer Foods. The focus is on evaluating classical econometric approaches versus regularization and machine-learning methods under a realistic rolling forecasting setup.

## Objective
- Forecast **weekly sales** at the **SKU–store** level to support demand planning and inventory decisions.
- Compare model classes in terms of accuracy, robustness, and consistency across heterogeneous SKUs and stores.

## Data
- 102 weeks of weekly scanner data (Sep 1989 – Aug 1991)
- 10 stores × 11 SKUs (brand–size combinations)
- Core drivers include **own price**, **competitor prices**, **promotions (feature/deal)**, and **seasonality**.

## Feature Engineering & Preprocessing
- Log-transform of sales and prices (interpretability via elasticities)
- Outlier handling using IQR / Tukey bounds
- Created predictors capturing:
  - own-price dynamics, lags, and promotion effects
  - competitor price aggregates and price gaps
  - interaction terms (promotion × price)
  - seasonal (month) dummies

## Models Compared
- Random Walk benchmark
- Forward Stepwise Regression (BIC selection)
- Ridge, LASSO, Elastic Net (regularization with cross-validation)
- Random Forest (nonlinear benchmark)

## Forecasting & Evaluation
- Rolling-window forecasting (SKU–store specific models)
- Loss metrics: MSE, asymmetric MAE, volume-weighted MSE, error variability across stores
- Statistical comparison using (panel-adjusted) Diebold–Mariano tests

## Key Takeaways
- No single model dominates across all SKUs/stores; performance is product-dependent.
- Regularization (Ridge / Elastic Net) and Random Forest often improve forecasting vs. Random Walk, especially where predictors are correlated or relationships are nonlinear.
- Business-relevant evaluation (volume-weighting, asymmetric penalties) changes which models look “best” for operational use.

## Report
- See `report/Report-ML.pdf` for methodology, results, and discussion.
