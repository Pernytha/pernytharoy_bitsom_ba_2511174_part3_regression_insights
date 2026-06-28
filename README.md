# Part 3: Regression-Based Business Insights & Model Interpretation

This repository contains the complete regression modeling framework and data-driven business insights portfolio developed to evaluate the core structural drivers of monthly sales performance across our physical retail store network.



## 1. Business Problem Summary
The executive leadership team of our brick-and-mortar retail chain requires an empirical, mathematically validated understanding of the operational factors that influence monthly store-level sales performance. To optimize capital distribution and store efficiency, upcoming tactical actions—such as expanding localized marketing spend, improving supply chain inventory fulfillment, adjusting discounting parameters, or reallocating store footprints across geographical administrative zones—must move away from qualitative intuition and align with statistical evidence.

This analysis utilizes Ordinary Least Squares (OLS) simple and multiple linear regression models to separate actionable baseline operational drivers from structural market noise, helping leadership maximize gross revenue while mitigating margin erosion.

-

## 2. Dataset Description
The underlying analytical dataset (`data/business_regression_data.xlsx`) comprises 306 cross-sectional monthly operational performance logs captured across unique store branches. The tracking variables include:

* **monthly_sales**: Gross financial revenue recorded by an individual store branch within a given month.
* **marketing_spend**: Localized advertising, digital promotional channels, and community outreach expenditure.
* **footfall**: The absolute count of unique customer entries recorded via automated store threshold sensors.
* **avg_discount_pct**: The weighted average discount rate applied to customer items during checkout.
* **inventory_availability_pct**: The logistical stock fill-rate identifying the real-time availability of top-velocity items.
* **region / store_type**: Qualitative geographical and physical architectural layout classifications for each unit.
* **store_id / month**: Unique alphanumeric administrative tracking keys.


## 3. Dependent and Independent Variables
To ensure statistical discipline, variables were classified into explicit functional parameters within the regression models:

* **Dependent Variable ($Y$):** `monthly_sales` (The focus variable we aim to explain, predict, and optimize).
* **Numerical Independent Variables ($X_n$):** `marketing_spend`, `footfall`, and `inventory_availability_pct`.
* **Categorical Independent Variables:** `region` (East, North, South, West).
* **Omitted Administrative Variables:** `store_id` and `month` were completely excluded from model processing. These fields serve as unique identifiers and contain zero continuous or ordinal predictive value; including them would introduce unnecessary tracking noise.



## 4. Regression Approach
Our analytical workflow followed a three-stage progressive regression framework to minimize error variance and isolate underlying parameters:

1.  **Exploratory Baseline Modeling:** Executed two separate Simple Linear Regression models to establish baseline, unadjusted mathematical relationships between our dependent variable and isolated operational factors (`marketing_spend` and `footfall`).
2.  **Comprehensive Multi-Variable Integration:** Formulated an OLS Multiple Linear Regression model combining continuous operational metrics alongside spatial geographic dummy controls to assess how these drivers interact simultaneously.
3.  **Residual Diagnostic Analysis:** Evaluated the difference between actual sales and model-predicted sales ($\text{Actual} - \text{Predicted}$) across all 306 rows to identify localized operational anomalies, management outliers, and potential systemic over/under-predictions.



## 5. Dummy Variable Approach
To incorporate the qualitative variable `region` into our quantitative linear models, it was converted into numeric binary dummy categories ($0$ or $1$). 

### Avoidance of the Dummy Variable Trap
To maintain statistical integrity and prevent perfect multicollinearity (the **Dummy Variable Trap**, where a group of dummy variables perfectly predicts a vector of ones), the **East Region** was intentionally omitted from the data matrix to act as our **Reference Category**.

* **Reference Baseline Baseline:** `East Region`
* **Included Regressors:** `region_north`, `region_south`, and `region_west`.

### Strategic Interpretation
The model's intercept represents the expected monthly sales of a branch operating within the baseline **East Region** (assuming its traffic, marketing spend, and inventory metrics are zero). The coefficients for `region_north`, `region_south`, and `region_west` show the expected marginal shift in monthly sales compared directly to that East region baseline, holding all other continuous operational metrics perfectly stable.



## 6. Model Comparison Summary
The statistical results extracted from `analysis/regression_workbook.xlsx` confirm a major leap in explanatory accuracy as model dimensions are expanded:

* **Simple Model 1 (Marketing Focus):** Explains a weak **15.74%** ($R^2 = 0.1574$) of sales variance. While statistically significant ($p < 0.001$), marketing spend in isolation is a highly incomplete predictor of absolute store performance.
* **Simple Model 2 (Footfall Focus):** Explains **73.48%** ($R^2 = 0.7348$) of sales variance, verifying that customer traffic volume is our strongest single operational predictor.
* **Multiple Regression Model (Full Integration):** Captures **81.05%** ($R^2 = 0.8105$) of global monthly sales variance. By assessing continuous and spatial parameters together, it controls for omitted-variable bias and minimizes our standard error to \$45,258.96.



## 7. Final Model Selected
The **Multiple Linear Regression Model** was selected as our final tool for corporate strategic formulation and capital allocation planning.

$$\text{Monthly Sales} = 155,754.15 + 0.42(\text{marketing\_spend}) + 54.12(\text{footfall}) + 2,145.80(\text{inventory\_availability\_pct}) + 42,350.10(\text{region\_north}) - 18,920.45(\text{region\_south}) + 8,430.60(\text{region\_west})$$

**Selection Rationale:** While Simple Model 2 (Footfall) offers a strong standalone correlation, single-variable models suffer from high **Omitted Variable Bias** by forcing all complex store operations into a single indicator. Model 3 provides executive leadership with a controlled multivariate environment, showing the true standalone impact of each distinct operational asset while keeping all other variables constant.



## 8. Business Recommendation
* **Prioritize Supply Chain & Fill-Rates:** Logistical inventory protection provides an immediate return of **+\$2,145.80** for every single percentage point increase in high-velocity product availability. Leadership must prioritize reducing stockouts over broad advertising pushes.
* **Optimize Traffic Conversion:** Customer footfall yields a strong, reliable return of **+\$54.12 per visitor**. Operations should invest in optimizing floor layouts, point-of-sale efficiency, and in-store conversion frameworks to fully capture this high-leverage driver.
* **Targeted Regional Adjustments:** The **North Region** generates a structural baseline lift of **+\$42,350.10** relative to the East, making it an excellent candidate for capital expansion. Conversely, the **South Region** displays a structural deficit of **-\$18,920.45**, flagging a need for local management audits.
* **Causation vs. Association Warning:** Leadership must remain aware that linear regression establishes a historical mathematical **association**, but does not automatically prove **causation**. Rising footfall and sales may both be simultaneously driven by an unmodeled external variable, such as localized economic booms or macro holiday periods.



## 9. Assumptions and Limitations
* **Assumption of Linear Continuity:** The Ordinary Least Squares (OLS) algorithm operates on strict linear behavior. In physical retail settings, variables like marketing spend and footfall follow an S-curve path, meaning they will eventually encounter diminishing returns or physical capacity constraints that a linear trend line cannot capture.
* **Administrative Dependability:** The accuracy of these strategic recommendations relies entirely on the tracking consistency of inventory logs and electronic footfall sensors across our distribution networks.



## 10. Screenshots Included
The following verification assets are maintained inside the `screenshots/` directory to document project validity:
1.  **`simple_regression_output.png`**: Captures Excel's OLS summary output for the standalone footfall/marketing exploratory runs.
2.  **`multiple_regression_output.png`**: Verifies the final multivariate parameter results, standard errors, and regional coefficient structures.
3.  **`residuals_preview.png`**: Documents the calculated predicted values and isolated extreme residual outlier rows.
4.  **`model_comparison_preview.png`**: Displays the finalized executive comparison matrix across all three models.