# Walmart Sales Prediction

A Machine Learning Project

## Overview

Walmart Inc. is an American multinational retail corporation operating a chain of hypermarkets, discount department stores, and grocery stores. This project develops a machine learning model to estimate weekly sales across Walmart stores based on economic indicators. The model helps the marketing service understand how sales are influenced by external factors and supports future marketing campaign planning.

## Project Objectives

- Perform exploratory data analysis and comprehensive data preprocessing
- Train a baseline linear regression model
- Develop regularized regression models to minimize overfitting

## Dataset Description

The dataset contains weekly sales data from multiple Walmart stores along with relevant economic variables. Key variables include store identifiers, sales figures, temperature, fuel prices, consumer price index (CPI), unemployment rates, and holiday indicators. The dataset has been custom-prepared and contains 6,435 observations across multiple stores and time periods.

## Data Preprocessing

### Missing Values Management

Weekly_Sales rows with missing values were removed without imputation to avoid prediction bias. Date entries with missing values were also deleted. Numerical features (Temperature, Fuel_Price, CPI, Unemployment) were imputed using median strategy. Boolean features (Holiday_Flag) were imputed using the most frequent value.

### Outlier Detection

Observations outside the range [mean ± 3 standard deviations] were removed from numerical features to ensure data quality. This conservative approach eliminated extreme outliers while preserving the dataset integrity.

### Feature Engineering

The Date column was decomposed into Year, Month, Day, and Day of Week to capture temporal patterns. Day of Week was subsequently removed due to perfect multicollinearity. Store and Holiday_Flag variables were treated as categorical features for proper model encoding.

## Exploratory Data Analysis Insights

### Target Variable

Weekly Sales exhibits a bimodal distribution with two distinct groups, suggesting different store sizes or operational models.

### Numerical Features

Temperature and Unemployment show normal distributions, while Fuel_Price and CPI display bimodal patterns. Correlations between features are minimal (< 0.2), indicating absence of multicollinearity.

### Feature-Target Relationships

Temperature and CPI show negative correlations with sales, while Unemployment shows positive correlation. Fuel price exhibits negligible correlation with weekly sales.

### Holiday Effect

Although holiday periods show slightly higher mean and median sales, a t-test confirms this difference is not statistically significant (p > 0.05).

## Modeling Approach

### Data Preparation

Data was split into training (80%) and testing (20%) sets using stratified sampling before any transformations. A preprocessing pipeline applied StandardScaler to numerical features and OneHotEncoder to categorical features.

### Baseline Model

A linear regression model served as the baseline. This model achieved excellent performance with test R² = 0.9322 and test RMSE = $213,651. The minimal difference between training and testing metrics (overfitting gap = 0.0432) indicates strong generalization.

### Regularized Model

A Lasso regression model with hyperparameter tuning via GridSearchCV was tested to reduce overfitting. However, the regularized model underperformed the baseline (test R² = 0.9184), confirming that the baseline already exhibits minimal overfitting and further regularization degrades performance.

## Key Findings

### Feature Importance

Permutation importance analysis reveals Temperature as the dominant predictor, followed by Year and CPI. These findings suggest that weather conditions significantly influence customer purchasing behavior, likely driven by seasonal product demand.

### Model Performance

The baseline linear regression model explains 93.22% of variance in test data with an average prediction error of approximately $213,651. This performance level supports reliable sales forecasting and business decision-making.

### Economic Indicators

Temperature emerges as the critical factor influencing sales, outweighing traditional economic measures. Higher inflation (CPI) correlates with reduced sales, while higher unemployment unexpectedly correlates with increased sales.

## Recommendations

- Shift from calendar-based planning to weather-based inventory management, prioritizing weather forecasts in supply chain decisions
- Develop seasonal product strategies aligned with temperature variations
- Monitor economic indicators, particularly inflation, for demand planning
- Deploy the linear regression model for weekly sales forecasting across store networks

## Technical Stack

- Python 3.8
- pandas, NumPy for data manipulation
- scikit-learn for model development and evaluation
- matplotlib, seaborn, plotly for visualization
- scipy for statistical testing

## Conclusion

This project demonstrates that linear regression effectively models Walmart weekly sales with minimal overfitting and excellent predictive accuracy. Temperature emerges as the critical driver of sales, warranting strategic emphasis on weather-responsive inventory management. The model provides a solid foundation for demand forecasting and supports data-driven decision-making in retail operations.

## Author
Mounia Tonazzini Agricultural Engineer & Data Scientist | AI & AgriTech

Location: Montpellier, France LinkedIn: www.linkedin.com/in/mounia-tonazzini GitHub: Mounia-Agronomist-Datascientist

Last Updated: April 2026: This project is part of the Jedha Bootcam certification