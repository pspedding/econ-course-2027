# Module M02 Quiz: Simple Linear Regression

*18 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. Show your algebra for calculation questions.

---

## Question 1

*Lesson L02 · OLS Objective*

OLS estimation minimises which quantity?

**Type:** Multiple Choice

- **A)** $\sum_{i=1}^n \hat{u}_i$
- **B)** $\sum_{i=1}^n |\hat{u}_i|$
- **C)** $\sum_{i=1}^n \hat{u}_i^2$
- **D)** $\max_i |\hat{u}_i|$

??? success "Show Answer"
    **Answer: C**

    OLS minimises the **sum of squared residuals**: $\text{SSR} = \sum_{i=1}^n \hat{u}_i^2 = \sum_{i=1}^n (y_i - \hat{\beta}_0 - \hat{\beta}_1 x_i)^2$. Squaring penalises large deviations more heavily than small ones, and makes the first-order conditions linear — yielding closed-form estimators.

---

## Question 2

*Lesson L02 · OLS Computation*

**[Calculation]** Given $x = \{1,2,3,4,5\}$ and $y = \{2,4,5,4,6\}$, compute $\hat{\beta}_1$ using:
$$\hat{\beta}_1 = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^n (x_i - \bar{x})^2}$$

**Type:** Calculation

??? success "Show Answer"
    $\bar{x} = 3$, $\bar{y} = 4.2$

    | $i$ | $x_i - \bar{x}$ | $y_i - \bar{y}$ | product | $(x_i-\bar{x})^2$ |
    |-----|---------|---------|---------|--------|
    | 1 | $-2$ | $-2.2$ | $4.4$ | $4$ |
    | 2 | $-1$ | $-0.2$ | $0.2$ | $1$ |
    | 3 | $0$ | $0.8$ | $0$ | $0$ |
    | 4 | $1$ | $-0.2$ | $-0.2$ | $1$ |
    | 5 | $2$ | $1.8$ | $3.6$ | $4$ |
    | **Sum** | | | **8.0** | **10** |

    $$\hat{\beta}_1 = \frac{8.0}{10} = \mathbf{0.8}$$

---

## Question 3

*Lesson L02 · OLS Intercept*

**[Calculation]** Using the result from Q2 ($\hat{\beta}_1 = 0.8$, $\bar{x}=3$, $\bar{y}=4.2$), compute $\hat{\beta}_0$.

**Type:** Calculation

??? success "Show Answer"
    $$\hat{\beta}_0 = \bar{y} - \hat{\beta}_1 \bar{x} = 4.2 - 0.8 \times 3 = 4.2 - 2.4 = \mathbf{1.8}$$

    Fitted line: $\hat{y} = 1.8 + 0.8x$. This passes through the sample means $(\bar{x}, \bar{y}) = (3, 4.2)$ — a guaranteed property of OLS.

---

## Question 4

*Lesson L03 · Residual Properties*

Which of the following is **NOT** a guaranteed algebraic property of OLS residuals?

**Type:** Multiple Choice

- **A)** $\sum_{i=1}^n \hat{u}_i = 0$
- **B)** $\sum_{i=1}^n x_i \hat{u}_i = 0$
- **C)** $\sum_{i=1}^n \hat{u}_i^2 = 0$
- **D)** $\bar{y} = \hat{\bar{y}}$ (mean of fitted values equals mean of $y$)

??? success "Show Answer"
    **Answer: C**

    $\sum \hat{u}_i^2 = \text{SSR} > 0$ unless the fit is perfect. The true OLS properties are:

    - $\sum \hat{u}_i = 0$ (from intercept FOC)
    - $\sum x_i \hat{u}_i = 0$ (from slope FOC — residuals orthogonal to $x$)
    - $\bar{\hat{y}} = \bar{y}$ (consequence of the first property)

---

## Question 5

*Lesson L04 · R-squared*

A regression of hourly wage on years of education gives $R^2 = 0.35$. The best interpretation is:

**Type:** Multiple Choice

- **A)** Education causes 35% of the variation in wages
- **B)** 35% of the variation in wages is explained by the linear relationship with education
- **C)** The regression fits the data well
- **D)** Education is statistically significant at the 35% level

??? success "Show Answer"
    **Answer: B**

    $R^2 = \text{SSE}/\text{SST}$ measures the proportion of total variation in $y$ *explained* (in a statistical, not causal, sense) by the regression. 35% is fairly typical for simple wage regressions. Option A is wrong — $R^2$ says nothing about causality. Option C is misleading — whether 35% is "good" depends on the application.

---

## Question 6

*Lesson L04 · SST decomposition*

**[Calculation]** $\text{SST} = 200$, $\text{SSE} = 150$. Compute $\text{SSR}$ and $R^2$.

**Type:** Calculation

??? success "Show Answer"
    $$\text{SST} = \text{SSE} + \text{SSR} \Rightarrow \text{SSR} = 200 - 150 = \mathbf{50}$$

    $$R^2 = \frac{\text{SSE}}{\text{SST}} = \frac{150}{200} = \mathbf{0.75}$$

    Equivalently: $R^2 = 1 - \text{SSR}/\text{SST} = 1 - 50/200 = 0.75$. The regression explains 75% of the variation in $y$.

---

## Question 7

*Lesson L05 · SLR Assumptions*

SLR Assumption 1 (linearity in parameters) requires:

**Type:** Short Answer

??? success "Show Answer"
    The population model is **linear in the parameters**: $y = \beta_0 + \beta_1 x + u$. The coefficients $\beta_0, \beta_1$ enter linearly. This does **not** require $y$ and $x$ to have a linear relationship — we can use $\ln(y)$ or $x^2$ as variables and still satisfy SLR.1. What cannot be linear in $\beta$ is something like $y = e^{\beta_1 x} + u$ (a nonlinear model that requires nonlinear least squares).

---

## Question 8

*Lesson L05 · SLR Assumptions*

Why is SLR Assumption 4 — the zero conditional mean $E(u \mid x) = 0$ — considered the key identification assumption?

**Type:** Short Answer

??? success "Show Answer"
    $E(u \mid x) = 0$ means the error term is mean-independent of $x$: everything in $u$ that affects $y$ is uncorrelated with $x$ on average. This is needed for **unbiasedness** — if violated (e.g. $x$ is correlated with an omitted variable in $u$), OLS is biased. In practice, SLR.4 is the hardest assumption to justify with observational data. Randomised experiments guarantee it by design (random assignment makes $x$ independent of $u$). With observational data, credible strategies (IV, DiD, controls) are needed.

---

## Question 9

*Lesson L05 · Unbiasedness*

$E(\hat{\beta}_1) = \beta_1$ (OLS is unbiased for the slope) requires which SLR assumptions?

**Type:** Multiple Choice

- **A)** SLR.1 only
- **B)** SLR.1, SLR.2, SLR.3, and SLR.4 (not SLR.5)
- **C)** All five assumptions SLR.1–SLR.5
- **D)** SLR.4 and SLR.5 only

??? success "Show Answer"
    **Answer: B**

    Unbiasedness requires SLR.1 (linearity), SLR.2 (random sampling), SLR.3 (variation in $x$), and SLR.4 (zero conditional mean). SLR.5 (homoskedasticity) is **not** needed for unbiasedness — only for the Gauss-Markov result (OLS is BLUE) and for standard error formulas to be correct.

---

## Question 10

*Lesson L05 · Variance of OLS*

$\text{Var}(\hat{\beta}_1) = \sigma^2 / \sum(x_i - \bar{x})^2$. Which statements are correct?

**Type:** Multiple Choice

- **A)** Variance decreases as $n$ increases; variance decreases as spread of $x$ increases
- **B)** Variance increases as $n$ increases; variance increases as spread of $x$ increases
- **C)** Variance is unaffected by sample size
- **D)** Variance decreases as $\sigma^2$ increases

??? success "Show Answer"
    **Answer: A**

    As $n \to \infty$, $\sum(x_i - \bar{x})^2 \to \infty \Rightarrow \text{Var}(\hat{\beta}_1) \to 0$ (consistent estimator). As the spread of $x$ increases (more variation in the regressor), $\sum(x_i-\bar{x})^2$ increases $\Rightarrow$ lower variance. Intuitively: more variation in $x$ gives more "information" to pin down the slope. This is why experimenters often spread $x$ values across the design space.

---

## Question 11

*Lesson L05 · Error Variance*

Why does the unbiased estimator of $\sigma^2$ use $n-2$ as the divisor: $\hat{\sigma}^2 = \text{SSR}/(n-2)$?

**Type:** Multiple Choice

- **A)** Because we have 2 regressors
- **B)** Because estimating $\beta_0$ and $\beta_1$ consumes 2 degrees of freedom, leaving $n-2$ free residuals
- **C)** Convention — $n-1$ would work equally well
- **D)** Because the formula applies only to samples of size $\geq 2$

??? success "Show Answer"
    **Answer: B**

    Each estimated coefficient "uses up" one degree of freedom. With 2 parameters estimated ($\hat{\beta}_0, \hat{\beta}_1$), only $n-2$ residuals are "free". Using SSR/$(n-2)$ makes $E(\hat{\sigma}^2) = \sigma^2$ (unbiased). In multiple regression with $k$ slope coefficients plus intercept: $\hat{\sigma}^2 = \text{SSR}/(n-k-1)$.

---

## Question 12

*Lesson L01 · Log Interpretation*

The estimated regression is $\ln(\text{wage}) = 1.2 + 0.08 \cdot \text{educ}$. The coefficient 0.08 means:

**Type:** Multiple Choice

- **A)** An additional year of education raises wages by \$0.08
- **B)** An additional year of education raises wages by approximately 8%
- **C)** An additional year of education raises log-wages by 8 units
- **D)** Wages increase by 8 times for each year of education

??? success "Show Answer"
    **Answer: B**

    In a log-level model, the coefficient approximates the percentage change: $100 \times 0.08 = 8\%$ wage increase per additional year of education. More precisely: $e^{0.08} - 1 \approx 8.33\%$. The approximation $\approx \beta_1 \times 100\%$ is accurate for small $\beta_1$ (say, $|\beta_1| < 0.2$).

---

## Question 13

*Lesson L04 · Scale Effects*

If we replace $y$ with $100y$ in the regression (e.g., convert from dollars to cents), what happens to $\hat{\beta}_1$ and $R^2$?

**Type:** Multiple Choice

- **A)** $\hat{\beta}_1$ is multiplied by 100; $R^2$ is unchanged
- **B)** Both $\hat{\beta}_1$ and $R^2$ are multiplied by 100
- **C)** $\hat{\beta}_1$ is divided by 100; $R^2$ is unchanged
- **D)** $R^2$ is multiplied by 100; $\hat{\beta}_1$ is unchanged

??? success "Show Answer"
    **Answer: A**

    Scaling $y$ by $c$ scales $\hat{\beta}_1$ by $c$ (since $\hat{\beta}_1 = \hat{\text{Cov}}(x,y)/\hat{\text{Var}}(x)$ and scaling $y$ scales the numerator). $R^2$ is scale-invariant — it measures the proportion of variance explained, which is unchanged by a constant multiplicative transformation of either variable.

---

## Question 14

*Lesson L05 · Gauss-Markov*

OLS is **BLUE** under SLR.1–SLR.5. What does BLUE stand for and what assumption is most critical?

**Type:** Short Answer

??? success "Show Answer"
    **B**est **L**inear **U**nbiased **E**stimator. Among all linear unbiased estimators of $\beta_1$, OLS has the smallest variance.

    The critical assumption is **SLR.5 (homoskedasticity):** $\text{Var}(u \mid x) = \sigma^2$ (constant). If violated (heteroskedasticity), OLS is still unbiased but no longer efficient — weighted least squares (WLS) would beat it. Gauss-Markov requires SLR.1–SLR.5; it does **not** require normality (SLR.6). For valid t/F tests with finite samples, normality is additionally required.

---

## Question 15

*Lesson L02 · CEF with Dummy Regressor*

**[Short Answer]** If $x \in \{0,1\}$ (binary), show that the OLS estimate gives $\hat{\beta}_1 = \bar{y}_1 - \bar{y}_0$ (difference in group means).

**Type:** Short Answer

??? success "Show Answer"
    Let $n_1$ = number with $x=1$, $n_0$ with $x=0$, $n = n_0 + n_1$.

    $\bar{x} = n_1/n$. For $x_i \in \{0,1\}$: $\sum(x_i - \bar{x})^2 = n_1(1-\bar{x})^2 + n_0(0-\bar{x})^2 = n_1 n_0^2/n^2 + n_0 n_1^2/n^2 = n_1 n_0/n$.

    $\sum(x_i-\bar{x})(y_i-\bar{y}) = \sum_{x_i=1}(1-\bar{x})(y_i-\bar{y}) = (1-\bar{x})\sum_{x_i=1}y_i - (1-\bar{x})n_1\bar{y}$

    After algebra: $= (n_0/n)(n_1\bar{y}_1) - (n_0/n)n_1\bar{y} = (n_1 n_0/n)(\bar{y}_1 - \bar{y})$.

    Since $\bar{y} = (n_1\bar{y}_1 + n_0\bar{y}_0)/n$, we get $\bar{y}_1 - \bar{y} = n_0(\bar{y}_1-\bar{y}_0)/n$.

    Therefore: $\hat{\beta}_1 = \frac{(n_1n_0/n)(\bar{y}_1-\bar{y})}{n_1n_0/n} = \bar{y}_1 - \bar{y}_0$. $\square$

---

## Question 16

*Lesson L02 · t-Test — MIT 14.32 style*

**[Calculation]** A wine price regression: $\hat{\beta}_1 = 0.032$ (effect of vintage year on $\ln(\text{price})$), $\text{se}(\hat{\beta}_1) = 0.012$, $n = 25$. Test $H_0: \beta_1 = 0$ at the 5% level. Critical value $t_{0.025, 23} = 2.069$.

**Type:** Calculation

??? success "Show Answer"
    $$t = \frac{\hat{\beta}_1 - 0}{\text{se}(\hat{\beta}_1)} = \frac{0.032}{0.012} = \mathbf{2.67}$$

    Since $|t| = 2.67 > t_{0.025,23} = 2.069$, **reject $H_0$** at 5%. Wine prices are significantly related to vintage year. Each additional year is associated with approximately $100 \times 0.032 = 3.2\%$ higher price.

---

## Question 17

*Lesson L04 · Confidence Interval*

**[Calculation]** $\hat{\beta}_1 = 1.5$, $\text{se}(\hat{\beta}_1) = 0.3$, $n = 50$, $k = 1$ slope. Construct a 95% CI for $\beta_1$. Use $t_{0.025,48} \approx 2.011$.

**Type:** Calculation

??? success "Show Answer"
    $$\text{CI} = \hat{\beta}_1 \pm t_{0.025,48} \times \text{se}(\hat{\beta}_1) = 1.5 \pm 2.011 \times 0.3 = 1.5 \pm 0.603$$

    $$\mathbf{[0.897,\ 2.103]}$$

    Interpretation: If we repeated this sampling procedure many times and constructed a CI each time, 95% of such intervals would contain the true $\beta_1$.

---

## Question 18

*Lesson L02 · Prediction*

**[Calculation]** Using $\hat{y} = 1.8 + 0.8x$ from Q3: for observation $i=3$ with $x_3 = 3$ and $y_3 = 5$, find the fitted value $\hat{y}_3$ and residual $\hat{u}_3$.

**Type:** Calculation

??? success "Show Answer"
    $$\hat{y}_3 = 1.8 + 0.8 \times 3 = 1.8 + 2.4 = \mathbf{4.2}$$

    $$\hat{u}_3 = y_3 - \hat{y}_3 = 5 - 4.2 = \mathbf{0.8}$$

    The positive residual means the actual wage is 0.8 units above the predicted value for this observation.