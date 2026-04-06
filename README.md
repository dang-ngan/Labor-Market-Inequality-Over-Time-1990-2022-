# Labor Market Inequality Over Time (1990–2022)

## Project Overview
This project performs a longitudinal analysis of the U.S. labor market using Current Population Survey (CPS) data. It explores how human capital variables — specifically education and potential experience — impact real hourly wages across different demographic groups and time periods.

## Key Research Questions
* **The Mincer Equation:** How much does an additional year of schooling increase an individual's earnings on average?
* **The Gender Wage Gap:** Do men and women receive the same "return" on their investment in education?
* **Time Trends:** How has the "Skill Premium" (the value of a degree) evolved from 1990 to 2022?

## Methodology
The analysis utilizes **Ordinary Least Squares (OLS) Regression** based on the Mincer Earnings Function:
$$\ln(w) = \beta_0 + \beta_1 S + \beta_2 E + \beta_3 E^2 + \epsilon$$
Where:
* $w$ = Real hourly wage
* $S$ = Years of schooling
* $E$ = Potential experience

### Advanced Features:
* **Interaction Terms:** Testing for heterogeneity by interacting `educ_yrs` with `sex` to measure differences in slopes.
* **Experience Centering:** Centering the experience variable to reduce multicollinearity and improve model stability.
* **Yearly Coefficient Tracking:** Running 32 separate regressions to visualize the shifting value of education over three decades.

## Visualizations Included
1.  **Experience-Earnings Profile:** A line plot showing the concave relationship between potential experience and log wages.
2.  **The Education Premium Trend:** A time-series plot of $\beta_1$ coefficients with 95% confidence intervals, showing the rising or falling value of education over 30 years.
3.  **Gender Interaction Slopes:** A comparison of wage "growth" trajectories for men vs. women based on education levels.

## Requirements
* Python 3.12+
* `pandas`, `numpy`: Data manipulation
* `statsmodels`: Econometric modeling
* `seaborn`, `matplotlib`: Statistical visualization
* `tqdm`: Progress tracking for iterative loops

## Dataset
The analysis is conducted on a cleaned version of the **IPUMS CPS dataset** (approx. 1.9 million observations), covering annual surveys from 1990 to 2022.

---

## Key Findings and Interpretation

### 1. The Return to Education (The "Schooling Premium")
Our baseline model indicates that for the reference group (females), every additional year of education is associated with an approximately **10.8% increase in hourly wages**. 
* **Significance:** This is a high rate of return, confirming that education remains one of the most significant predictors of individual economic success in the U.S. labor market.

### 2. Gender Differences in Education Returns
By using interaction terms ($educ\_yrs \times sex$), the model reveals a "Gender-Education Paradox":
* **The Intercept Shift:** Men start with a higher base wage (approx. 46% higher than women at the intercept).
* **The Slope Difference:** However, women have a **steeper slope** (higher return per year of schooling) than men. Men’s return to education is roughly **1.3 percentage points lower** than women’s (approx. 9.5% vs 10.8%).
* **Interpretation:** While a gender pay gap exists at all levels, education acts as a stronger "equalizer" for women; a degree provides a larger percentage boost to a woman's earnings than to a man's.


### 3. Experience and the "Life-Cycle" of Earnings
The analysis confirms the classic Mincerian "concave" earnings profile. 
* **Positive Linear Term (`exp`):** Wages rise as workers gain experience and specialized skills early in their careers (approx. 2.1% per year).
* **Negative Quadratic Term (`exp2`):** The growth rate slows down over time. This creates a "hump-shaped" curve where earnings typically peak in the late 40s or early 50s before plateauing.


### 4. Longitudinal Trends (1990–2022)
By tracking the education coefficient annually, the project documents the **Evolution of the Skill Premium**:
* **The 1990s-2000s:** A period of significant growth in the value of a degree, likely driven by Skill-Biased Technological Change (SBTC).
* **Recent Stability:** The "10% Benchmark" remains a resilient feature of the U.S. economy, though shifts in the most recent years (2020–2022) suggest potential volatility in the post-pandemic labor market.
