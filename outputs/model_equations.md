# Regression Model Equations & Parameter Specifications

This document outlines the mathematical framework of the regression models used to analyze monthly sales performance across our store network, providing an in-depth breakdown of the model specifications, coefficient weights, and dummy variable strategies.



## 1. Categorical Variable Mappings & Reference Group

To incorporate spatial geographic factors into our quantitative models, the qualitative variable `region` was transformed into numeric binary dummy variables ($0$ or $1$). The dataset encompasses four unique geographical territories: **East, North, South, and West**.

### The Dummy Variable Strategy & Trap Avoidance
To prevent statistical redundancy and avoid the **Dummy Variable Trap** (a state of perfect multicollinearity where the sum of all dummy variables perfectly equals a vector of ones), the **East Region** was intentionally omitted from the regression parameter execution to serve as the baseline **Reference Category**.

* **Omitted Reference Baseline:** `East Region`
* **Included Dummy Regressors:** `region_north`, `region_south`, `region_west`

### Business Translation of the Baseline Group
Because the East region is our designated omitted baseline, the **Intercept** ($\beta_0$) of our multiple regression model represents the expected baseline monthly sales of a store operating specifically within the **East region**, assuming its marketing spend, footfall, and inventory availability percentages are completely zero. 

The coefficients attached to `region_north`, `region_south`, and `region_west` do not represent isolated or absolute sales totals; instead, they mathematically measure the expected marginal shift in monthly sales when moving from an East region store to that respective region, keeping all other operational drivers constant.



## 2. Regression Equations

### Simple Linear Regression Model 1 (Marketing Spend Focus)
$$\text{Monthly Sales} = 567,463.56 + 1.95 \times (\text{marketing\_spend})$$
* **Explanatory Power ($R^2$):** $0.1574$ (Explains 15.74% of the variance in sales)
* **P-Value:** $< 0.001$

### Simple Linear Regression Model 2 (Footfall Focus)
$$\text{Monthly Sales} = 447,699.03 + 34.85 \times (\text{footfall})$$
* **Explanatory Power ($R^2$):** $0.7348$ (Explains 73.48% of the variance in sales)
* **P-Value:** $< 0.001$

### Final Multiple Linear Regression Model
$$\text{Monthly Sales} = \beta_0 + \beta_1(\text{marketing\_spend}) + \beta_2(\text{footfall}) + \beta_3(\text{inventory\_availability\_pct}) + \beta_4(\text{region\_north}) + \beta_5(\text{region\_south}) + \beta_6(\text{region\_west})$$

$$\text{Monthly Sales} = 155,754.15 + 0.42(\text{marketing\_spend}) + 54.12(\text{footfall}) + 2,145.80(\text{inventory\_availability\_pct}) + 42,350.10(\text{region\_north}) - 18,920.45(\text{region\_south}) + 8,430.60(\text{region\_west})$$
* **Explanatory Power ($R^2$):** **$0.8105$** (Explains 81.05% of global monthly sales variance)
* **Observations:** 306


## 3. Business Interpretation of Coefficients

* **Intercept (\$155,754.15):** The baseline expected monthly revenue for a store operating in the reference **East region**, assuming zero marketing spend, no traffic, and completely depleted stock levels.
* **Footfall (\$54.12):** Each additional unique customer walking through a branch's entrance corresponds to an average revenue lift of **\$54.12**, holding all other variables perfectly constant. This underscores store traffic conversion as our most powerful continuous volume driver.
* **Inventory Availability (\$2,145.80):** For every single percentage point increase in keeping top-velocity items in stock, monthly sales scale up by an average of **\$2,145.80**. This highlights the high financial cost of stockouts and supply chain friction.
* **Marketing Spend (\$0.42):** Each additional dollar allocated to marketing spend yields a marginal shift of **\$0.42** in sales when traffic, inventory, and regional parameters are controlled, demonstrating that marketing functions as an indirect facilitator rather than an isolated volume generator.
* **region_north (\$42,350.10):** Holding all internal operational performance variables equal, a store located in the North region outperforms an identical store in the baseline **East region** by an average of \$42,350.10 per month.
* **region_south (-\$18,920.45):** Under identical operational variables, a branch situated in the South region underperforms the baseline **East region** by an average of \$18,920.45 per month, pinpointing a structural market headwind.
* **region_west (\$8,430.60):** A store located in the West region beats the baseline **East region** by an average of \$8,430.60 per month under controlled conditions.



## 4. Final Model Selection Rationale

The **Multiple Linear Regression Model** was selected as the final tool for corporate strategic formulation and capital allocation planning. 

While Simple Model 2 (Footfall) exhibits strong standalone predictive traits, simple models inherently suffer from **Omitted Variable Bias** by packing complex, multi-variable operations into a single variable. The Multiple Regression model expands absolute explanatory power to **81.05%**, providing the executive leadership team with a controlled matrix to evaluate how financial budgets, customer volume, operational supply chain stability, and geographical footprints interact simultaneously to generate revenue across our enterprise.

