# Superstore Sales Forecasting & Inventory Planning

## Executive Summary:
Inventory mismanagement (stock-outs or overstocking) is a major cost driver in retail. Using historical sales data from the Superstore dataset (2014-2016), I developed a Time Series forecasting model to predict monthly sales for 2017. 

**Key Findings:** The analysis identified a recurring seasonal surge in Q4 (November-December). The final SARIMA model successfully predicted these trends with an RMSE of ~13,995, providing a reliable baseline for inventory planning.

**Recommendation:** To maximize revenue, the inventory procurement team should increase stock levels by 40-50% starting in October to meet end-of-year demand, while maintaining leaner inventory during Q1 (Jan-Feb).

---

### Business Problem: 
**"How much inventory should we buy for next month?"**

Retail sales are rarely linear. Seasonal fluctuations make it difficult for supply chain managers to optimize stock levels. 
* **Under-stocking** leads to lost sales and dissatisfied customers.
* **Over-stocking** leads to high storage costs and potential waste.

The goal of this project is to build a predictive model that anticipates future demand, allowing stakeholders to make data-driven decisions rather than relying on gut feeling.

![Placeholder: Insert your 'Monthly Sales Trend' or 'Decomposition' image here](https://github.com/Syarifudin10/time-series-analysis/blob/main/time%20series_sales%20trend.png)
*(Fig 1: Historical sales showing clear seasonal patterns)*

---

### Methodology: 
1.  **Data Preprocessing (Python & Pandas):** * Aggregated daily transaction data into monthly sales totals.
    * Handled time-series specific requirements (indexing, sorting).
    * Verified data integrity (outlier analysis and missing values).

2.  **Exploratory Data Analysis (EDA):**
    * Decomposed the series into **Trend**, **Seasonality**, and **Residuals**.
    * Identified a strong 12-month seasonal cycle.

3.  **Modeling (Statsmodels):**
    * **Baseline:** Simple Moving Average (SMA).
    * **Smoothing:** Holt-Winters Exponential Smoothing.
    * **Final Model:** Seasonal ARIMA (SARIMA) with parameters `(1,1,1)x(1,1,1,12)`.

---

### Results & Analysis:
The SARIMA model proved to be the most effective in capturing the complex seasonal patterns of the dataset.

* **Model Accuracy:** Root Mean Squared Error (RMSE) of **13,995** on the test data.
* **Visual Validation:** As seen in the chart below, the Forecast (Red Line) closely tracks the Actual Sales (Green Line), particularly capturing the critical end-of-year spike.

![Placeholder: Insert your 'Improved Forecast Plot' image here](https://github.com/Syarifudin10/time-series-analysis/blob/main/time%20series_sales%20forecasting.png)
*(Fig 2: Actual Sales (2017) vs SARIMA Forecast)*

---

### Recommendations:

Based on the forecast, I recommend the following adjustments to the supply chain strategy:

1.  **Q4 Inventory Ramp-up:** Begin increasing stock levels for "Technology" and "Furniture" categories in **early October**. The model predicts sales will double in Nov-Des compared to the annual average.
2.  **Q1 Efficiency:** Reduce inventory orders for January and February to prevent dead stock, as these are historically the slowest months.
3.  **Promotional Planning:** Since sales naturally dip in Q1, the marketing team should plan aggressive promotions in February to smooth out the revenue curve.

### Next Steps: 
1.  **Hyperparameter Tuning:** Use `auto_arima` to mathematically optimize the (p,d,q) parameters for potentially lower RMSE.
2.  **Category-Level Forecasting:** Break down the model to forecast specifically for "Technology" vs "Office Supplies" individually, as they may have different trends.
3.  **External Factors:** Incorporate holiday data (e.g., Black Friday dates) as exogenous variables to improve peak prediction accuracy.
