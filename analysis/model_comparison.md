# Model Comparison & Statistical Evaluation Report

This report evaluates and compares the exploratory Simple Linear Regression models against the comprehensive Multiple Linear Regression model built to analyze monthly store sales performance.

## 1. Structural Comparison Table

| Evaluation Item | Model 1: Simple Regression (Marketing) | Model 2: Simple Regression (Footfall) | Model 3: Multiple Regression Model |
| :--- | :--- | :--- | :--- |
| **Model Name** | Simple Model 1: Marketing Spend Focus | Simple Model 2: Store Footfall Focus | Multiple Regression Model |
| **Variables Used** | **Dependent:** `monthly_sales`<br>**Independent:** `marketing_spend` | **Dependent:** `monthly_sales`<br>**Independent:** `footfall` | **Dependent:** `monthly_sales`<br>**Independent:** `marketing_spend`, `footfall`, `inventory_availability_pct`, `region_north`, `region_south`, `region_west` |
| **R-squared** | **0.1574** (Explains 15.74% of variance) | **0.7348** (Explains 73.48% of variance) | **0.8105** (Explains 81.05% of variance) |
| **Significant Variables** | `marketing_spend` ($p < 0.001$) | `footfall` ($p < 0.001$) | `footfall` ($p < 0.001$), `inventory_availability_pct` ($p < 0.01$), `region_north` ($p < 0.05$) |
| **Business Usefulness** | **Very Low.** Cannot be used for operational scaling as it leaves 84.26% of sales variance unexplained. | **Moderately High.** Accurately identifies store traffic as a core baseline volume driver, but remains incomplete. | **Excellent.** Provides a controlled environment to isolate separate operational levers simultaneously for executive planning. |
| **Limitations** | **Omitted Variable Bias.** Over-simplifies retail dynamics by packing all complex parameters into marketing. | **Single-Variable Reliance.** Ignores logistics, geographic layout benefits, and stockout penalties. | **Linearity Constraint.** Assumes straight-line relationships; cannot model diminishing returns or traffic saturation caps. |



## 2. Statistical Insights & Explanatory Power

### The Shift in R-squared
Moving from Simple Model 1 ($R^2 = 0.1574$) to the Multiple Regression Model ($R^2 = 0.8105$) drastically expands our explanatory power. This mathematical lift confirms that monthly sales performance is driven by a coordinated system of operational inputs. While driving footfall is crucial, its financial yield depends closely on supply chain logistics and geographic location parameters.

### Omitted Variable Bias (OVB) Mitigation
In Simple Model 1, marketing spend shows an inflated coefficient because it absorbs the unmodeled impacts of physical footfall and inventory tracking. The Multiple Regression model removes this statistical bias, enabling leadership to isolate the true marginal return of each distinct corporate asset while keeping other factors constant.



## 3. Model Limitations & Data Vulnerabilities
* **Linearity Assumptions:** The Ordinary Least Squares (OLS) algorithm operates on strict linear behavior. In retail stores, variables such as marketing budgets and footfall density eventually hit an S-curve path, meaning they hit diminishing returns or capacity limits that a linear model cannot capture.
* **Administrative Dependability:** The value of these recommendations relies entirely on the tracking consistency of inventory logs (`inventory_availability_pct`) and footfall sensors across our distribution centers.



	
