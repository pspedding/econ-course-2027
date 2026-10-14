# Formula Sheet

!!! tip "Exam Reference"
    Key formulas for ECMT5001 (USYD S1 2027). Organised by module. All notation follows Wooldridge *Introductory Econometrics* unless stated.

---

## M01 — Statistics Review

### Expectation and Variance

$$E(aX + bY) = aE(X) + bE(Y)$$

$$\text{Var}(X) = E(X^2) - [E(X)]^2$$

$$\text{Var}(aX + bY) = a^2\text{Var}(X) + b^2\text{Var}(Y) + 2ab\,\text{Cov}(X,Y)$$

$$\text{Cov}(X,Y) = E(XY) - E(X)E(Y)$$

$$\text{Corr}(X,Y) = \frac{\text{Cov}(X,Y)}{\sqrt{\text{Var}(X)\,\text{Var}(Y)}} \in [-1, 1]$$

If $X$ and $Y$ are **independent**: $\text{Cov}(X,Y) = 0$ (but **not** the converse in general).

### Conditional Expectation

$$E(Y) = E[E(Y \mid X)] \quad \text{(Law of Iterated Expectations)}$$

$$\text{Var}(Y) = E[\text{Var}(Y \mid X)] + \text{Var}[E(Y \mid X)] \quad \text{(LTE variance decomposition)}$$

### Standard Distributions

| Distribution | PMF/PDF | $E(X)$ | $\text{Var}(X)$ |
|---|---|---|---|
| $\text{Bernoulli}(p)$ | $p^x(1-p)^{1-x}$ | $p$ | $p(1-p)$ |
| $\text{Binomial}(n,p)$ | $\binom{n}{x}p^x(1-p)^{n-x}$ | $np$ | $np(1-p)$ |
| $\mathcal{N}(\mu,\sigma^2)$ | $\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ | $\mu$ | $\sigma^2$ |
| $\chi^2_k$ | — | $k$ | $2k$ |
| $t_k$ | — | $0$ ($k>1$) | $k/(k-2)$ ($k>2$) |
| $F_{k_1,k_2}$ | — | $k_2/(k_2-2)$ | — |

### Hypothesis Testing

**$z$-test for proportion $p$:**

$$z = \frac{\hat{p} - p_0}{\sqrt{p_0(1-p_0)/n}} \sim \mathcal{N}(0,1) \text{ under } H_0$$

**One-sample $t$-test for $\mu$:**

$$t = \frac{\bar{X} - \mu_0}{s/\sqrt{n}} \sim t_{n-1} \text{ under } H_0$$

**$95\%$ confidence interval for $\mu$:**

$$\bar{X} \pm t_{n-1, 0.025} \cdot \frac{s}{\sqrt{n}}$$

---

## M02 — Simple Regression

### The Simple Regression Model

$$y = \beta_0 + \beta_1 x + u, \quad E(u \mid x) = 0$$

### OLS Estimators

$$\hat{\beta}_1 = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^n (x_i - \bar{x})^2} = \frac{S_{xy}}{S_{xx}}$$

$$\hat{\beta}_0 = \bar{y} - \hat{\beta}_1 \bar{x}$$

### Sums of Squares

$$SST = \sum_{i=1}^n (y_i - \bar{y})^2 \quad \text{(total)}$$

$$SSE = \sum_{i=1}^n (\hat{y}_i - \bar{y})^2 \quad \text{(explained)}$$

$$SSR = \sum_{i=1}^n \hat{u}_i^2 \quad \text{(residual)}$$

$$SST = SSE + SSR$$

### Goodness of Fit

$$R^2 = 1 - \frac{SSR}{SST} = \frac{SSE}{SST} \in [0,1]$$

For simple regression: $R^2 = \hat{\text{Corr}}(x,y)^2$

### Variance and Standard Error of OLS

$$\text{Var}(\hat{\beta}_1) = \frac{\sigma^2}{SST_x}, \quad \text{Var}(\hat{\beta}_0) = \frac{\sigma^2 \sum x_i^2}{n \cdot SST_x}$$

$$\hat{\sigma}^2 = \frac{SSR}{n-2} \quad \text{(unbiased estimator of } \sigma^2\text{)}$$

$$SE(\hat{\beta}_1) = \frac{\hat{\sigma}}{\sqrt{SST_x}}$$

### Inference in Simple Regression

$$t = \frac{\hat{\beta}_1 - \beta_1^0}{SE(\hat{\beta}_1)} \sim t_{n-2} \quad \text{(under MLR.1–MLR.6)}$$

**$95\%$ CI for $\beta_1$:** $\hat{\beta}_1 \pm t_{n-2,0.025} \cdot SE(\hat{\beta}_1)$

### Algebraic Properties of OLS

$$\sum_{i=1}^n \hat{u}_i = 0, \quad \sum_{i=1}^n x_i \hat{u}_i = 0, \quad \bar{y} = \hat{\beta}_0 + \hat{\beta}_1\bar{x}$$

---

## M03 — Multiple Regression

### The Multiple Regression Model

$$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \cdots + \beta_k x_k + u$$

**Matrix form:** $\mathbf{y} = \mathbf{X}\boldsymbol{\beta} + \mathbf{u}$

**OLS estimator:** $\hat{\boldsymbol{\beta}} = (\mathbf{X}'\mathbf{X})^{-1}\mathbf{X}'\mathbf{y}$ (requires $\mathbf{X}'\mathbf{X}$ invertible)

### Adjusted R-Squared

$$\bar{R}^2 = 1 - \frac{SSR/(n-k-1)}{SST/(n-1)} = 1 - \frac{n-1}{n-k-1}(1-R^2)$$

- $\bar{R}^2 \leq R^2$ always
- $\bar{R}^2$ can be **negative**
- $\bar{R}^2$ rises when adding a regressor iff its $|t\text{-stat}| > 1$ (approx.)

### MLR Assumptions Summary

| Assumption | Statement | Consequence if Violated |
|------------|-----------|------------------------|
| MLR.1 | Linear in parameters | Model misspecified |
| MLR.2 | Random sampling | Generalisation invalid |
| MLR.3 | No perfect collinearity | OLS cannot be computed |
| MLR.4 | $E(u\mid\mathbf{x})=0$ | OLS **biased and inconsistent** |
| MLR.5 | $\text{Var}(u\mid\mathbf{x})=\sigma^2$ | OLS **inefficient**; SEs wrong |
| MLR.6 | $u\mid\mathbf{x}\sim\mathcal{N}(0,\sigma^2)$ | Finite-sample $t$/$F$ invalid |

**Gauss–Markov Theorem:** Under MLR.1–MLR.5, OLS is **BLUE** (Best Linear Unbiased Estimator).

### Omitted Variable Bias (OVB)

True model: $y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + u$  
Estimated (omitting $x_2$): $y = \tilde{\beta}_0 + \tilde{\beta}_1 x_1 + v$

$$\boxed{E(\tilde{\beta}_1) = \beta_1 + \beta_2\,\tilde{\delta}_1}$$

where $\tilde{\delta}_1 = \dfrac{\sum(x_{i1}-\bar{x}_1)(x_{i2}-\bar{x}_2)}{\sum(x_{i1}-\bar{x}_1)^2}$ is the coefficient from regressing $x_2$ on $x_1$.

**Bias direction:**

| | $\tilde{\delta}_1 > 0$ | $\tilde{\delta}_1 < 0$ |
|---|---|---|
| $\beta_2 > 0$ | Upward bias | Downward bias |
| $\beta_2 < 0$ | Downward bias | Upward bias |

### Variance of OLS in Multiple Regression

$$\text{Var}(\hat{\beta}_j) = \frac{\sigma^2}{SST_j(1 - R_j^2)}$$

where $SST_j = \sum(x_{ij}-\bar{x}_j)^2$ and $R_j^2$ is the $R^2$ from regressing $x_j$ on all other regressors.

### Variance Inflation Factor

$$VIF_j = \frac{1}{1 - R_j^2}$$

$$\text{Var}(\hat{\beta}_j) = \frac{\sigma^2}{SST_j} \cdot VIF_j$$

Rule of thumb: $VIF_j > 10$ indicates severe multicollinearity.

$$SE(\hat{\beta}_j) = \frac{\hat{\sigma}}{\sqrt{SST_j(1-R_j^2)}} = \frac{\hat{\sigma}\sqrt{VIF_j}}{\sqrt{SST_j}}$$

### Inference in Multiple Regression

**$t$-statistic for $\beta_j$:**

$$t_j = \frac{\hat{\beta}_j}{SE(\hat{\beta}_j)} \sim t_{n-k-1} \quad \text{under } H_0: \beta_j = 0 \text{ and MLR.1–MLR.6}$$

**$F$-statistic (joint test of $q$ restrictions):**

$$F = \frac{(SSR_r - SSR_{ur})/q}{SSR_{ur}/(n-k-1)} \sim F_{q,\,n-k-1}$$

where $r$ = restricted model, $ur$ = unrestricted model, $q$ = number of restrictions.

**Equivalently using $R^2$:**

$$F = \frac{(R^2_{ur} - R^2_r)/q}{(1 - R^2_{ur})/(n-k-1)}$$

---

## Quick Reference: Notation

| Symbol | Definition |
|--------|-----------|
| $n$ | Sample size |
| $k$ | Number of regressors (excluding intercept) |
| $\hat{u}_i$ | OLS residual: $y_i - \hat{y}_i$ |
| $\sigma^2$ | Population error variance |
| $\hat{\sigma}^2$ | $SSR/(n-k-1)$ — estimated error variance |
| $\hat{\sigma}$ | $\sqrt{\hat{\sigma}^2}$ — root mean squared error (RMSE) |
| $SST$ | $\sum(y_i-\bar{y})^2$ |
| $SSE$ | $\sum(\hat{y}_i-\bar{y})^2$ |
| $SSR$ | $\sum\hat{u}_i^2$ |
| $R^2$ | $1 - SSR/SST$ |
| $\bar{R}^2$ | Adjusted $R^2$ |
| $VIF_j$ | $1/(1-R_j^2)$ |
