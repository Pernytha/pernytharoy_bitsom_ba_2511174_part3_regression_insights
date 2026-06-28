# Regression Model Equations & Parameter Specifications

This document defines the mathematical and conceptual frameworks for the regression models used to analyze monthly sales performance across our store network. It provides a formal breakdown of equations, coefficient weights, and the transformation strategy applied to categorical data.



## 1. Categorical Variable Mappings & Reference Group

To incorporate geographical factors into our quantitative models, the qualitative dimension `region` was converted into binary numeric variables ($0$ or $1$). The underlying dataset covers four unique operational regions: **East, North, South, and West**.

### The Dummy Variable Strategy & Redundancy Avoidance
To prevent statistical redundancy and completely avoid the **Dummy Variable Trap** (a state of perfect multicollinearity where the sum of all dummy variables perfectly equals a vector of ones), the **East Region** was intentionally omitted from the regression range selection. It serves as our designated **Reference Category**.

* **Omitted Reference Baseline:** `East Region`
* **Included Dummy Regressors:** `region_north`, `region_south`, `region_west`

### Business Translation of the Baseline Group
Because the East region is our omitted baseline, the **Intercept** ($\beta_0$) of the multiple regression model represents the theoretical baseline monthly sales of a store operating specifically within the **East region**, assuming its marketing spend, footfall, and inventory availability percentages are completely zero. 

The coefficients attached to `region_north`, `region_south`, and `region_west` do not represent isolated or standalone sales totals; instead, they measure the expected marginal shift in monthly sales when moving from an East region store to that respective region, keeping all other operational drivers constant.



## 2. Regression Equations

### Simple Linear Regression Model 1 (Marketing Spend Focus)
$$\text{Monthly Sales} = 567,463.56 + 1.95 \times (\text{marketing\_spend})$$
* **Explanatory Power ($R^2$):** $0.1574$ (Explains 15.74% of the variance in monthly sales)
* **P-Value:** $< 0.001$

### Simple Linear Regression Model 2 (Footfall Focus)
$$\text{Monthly Sales} = 447,699.03 + 34.85 \times (\text{footfall})$$
* **Explanatory Power ($R^2$):** $0.7348$ (Explains 73.48% of the variance in monthly sales)
* **P-Value:** $< 0.001$

### Final Multiple Linear Regression Model
$$\text{Monthly Sales} = \beta_0 + \beta_1(\text{marketing\_spend}) + \beta_2(\text{footfall}) + \beta_3(\text{inventory\_availability\_pct}) + \beta_4(\text{region\_north}) + \beta_5(\text{region\_south}) + \beta_6(\text{region\_west})$$

$$\text{Monthly Sales} = 155,754.15 + 0.42(\text{marketing\_spend}) + 54.12(\text{footfall}) + 2,145.80(\text{inventory\_availability\_pct}) + 42,350.10(\text{region\_north}) - 18,920.45(\text{region\_south}) + 8,430.60(\text{region\_west})$$
* **Explanatory Power ($R^2$):** **$0.8105$** (Explains 81.05% of global monthly sales variance)



## 3. Business Interpretation of Coefficients

* **Intercept (\$155,754.15):** This represents the baseline expected monthly revenue for a store operating in our reference **East region**, assuming zero marketing spend, zero customer footfall, and completely depleted stock levels.
* **Footfall (\$54.12):** Each additional unique customer walking through a store's entrance corresponds to an average revenue increase of **\$54.12**, holding all other variables perfectly constant. In business terms, physical traffic remains our most high-leverage immediate volume driver.
* **Inventory Availability (\$2,145.80):** For every single percentage point increase in keeping top-velocity items in stock, monthly sales scale up by an average of **\$2,145.80**. This highlights the major financial impact of stockouts and supply chain delays on conversion.
* **Marketing Spend (\$0.42):** Each additional dollar allocated to localized marketing spend yields a marginal shift of only **\$0.42** in sales when traffic, inventory, and regional parameters are controlled. This demonstrates that marketing works as an indirect traffic facilitator rather than an independent volume creator.
* **region_north (\$42,350.10):** Holding all internal operational performance variables equal, a store located in the North region outperforms an identical store in our baseline **East region** by an average of \$42,350.10 per month.
* **region_south (-\$18,920.45):** Under identical operational variables, a branch situated in the South region underperforms our baseline **East region** by an average of \$18,920.45 per month, pinpointing a structural market bottleneck or regional efficiency lag.
* **region_west (\$8,430.60):** A store located in the West region captures a modest premium over the baseline **East region**, outperforming it by an average of \$8,430.60 per month under controlled conditions.



## 4. Final Model Selection Justification

The **Multiple Linear Regression Model** was selected as the final analytical framework for corporate strategic formulation and capital allocation planning. 

While Simple Model 2 (Footfall) exhibits strong standalone predictive traits ($R^2 = 0.7348$), single-variable models inherently suffer from **Omitted Variable Bias** by condensing multi-variable store performance into an isolated driver. The Multiple Regression model expands absolute explanatory power to **81.05%**, giving leadership a controlled environment to evaluate how marketing budgets, customer traffic density, supply chain logistics, and geographic location interact simultaneously to drive corporate revenue.