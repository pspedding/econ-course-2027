# Module M03 Quiz: Multiple Regression

*16 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. Write out your working for calculation questions.

---

## Question 1

*Lesson L01 · Interpretation*

In the multiple regression $\ln(\text{wage}) = \beta_0 + \beta_1 \text{educ} + \beta_2 \text{exper} + u$, the coefficient $\beta_1$ represents:

**Type:** Multiple Choice

- **A)** The simple correlation between education and log-wages
- **B)** The change in log-wages for one additional year of education, holding experience constant (ceteris paribus)
- **C)** The total effect of education on wages, including its effect through experience
- **D)** The average log-wage for a worker with zero education

??? success "Show Answer"
    **Answer: B**

    The ceteris paribus interpretation: $\beta_1$ measures the effect of education on log-wages *holding all other regressors (here, experience) fixed*. This is the whole point of multiple regression — isolating the partial effect of one variable while controlling for others. The Frisch-Waugh-Lovell theorem shows this is literally the slope from regressing wages (residualised on experience) on education (residualised on experience).

---

## Question 2

*Lesson L04 · Omitted Variable Bias*

A researcher regresses wages on education only, omitting ability. Ability is positively correlated with education and positively affects wages. The bias in $\hat{\beta}_\text{educ}$ is:

**Type:** Multiple Choice

- **A)** Downward — the estimated return to education is too low
- **B)** Upward — the estimated return to education is too high
- **C)** Zero — omitting variables never causes bias if the sample is large
- **D)** Ambiguous — we cannot determine the direction without data

??? success "Show Answer"
    **Answer: B**

    OVB formula: $\tilde{\beta}_1 = \beta_1 + \beta_2 \cdot \delta_{12}$ where $\delta_{12} = \text{Cov}(\text{ability}, \text{educ})/\text{Var}(\text{educ}) > 0$ (ability positively correlated with education) and $\beta_2 > 0$ (ability raises wages). So $\tilde{\beta}_1 > \beta_1$ — the estimated return to education is **upward biased**. Part of what looks like a "return to education" is actually the return to unobserved ability.

---

## Question 3

*Lesson L04 · OVB Formula*

**[Calculation]** The OVB formula is $\tilde{\beta}_1 = \beta_1 + \beta_2 \cdot \delta_{12}$. Given: true $\beta_1 = 0.08$ (education effect), $\beta_2 = 0.05$ (ability effect), $\delta_{12} = 0.6$ (slope from regressing ability on education). What is $\tilde{\beta}_1$?

**Type:** Calculation

??? success "Show Answer"
    $$\tilde{\beta}_1 = \beta_1 + \beta_2 \cdot \delta_{12} = 0.08 + 0.05 \times 0.6 = 0.08 + 0.03 = \mathbf{0.11}$$

    The simple regression overstates the education return by 0.03 — about 38% inflation. This is a substantial bias in practice, explaining why education returns estimated without ability controls tend to be higher than those from natural experiments (IV) that arguably hold ability constant.

---

## Question 4

*Lesson L04 · OVB Direction*

In the OVB formula $\tilde{\beta}_1 = \beta_1 + \beta_2 \delta_{12}$, if $\text{Corr}(x_2, x_1) < 0$ and $\beta_2 > 0$, the bias is:

**Type:** Multiple Choice

- **A)** Upward ($\tilde{\beta}_1 > \beta_1$)
- **B)** Downward ($\tilde{\beta}_1 < \beta_1$)
- **C)** Zero
- **D)** Indeterminate

??? success "Show Answer"
    **Answer: B**

    $\delta_{12} < 0$ (negative correlation between $x_2$ and $x_1$) and $\beta_2 > 0 \Rightarrow \beta_2 \cdot \delta_{12} < 0 \Rightarrow \tilde{\beta}_1 < \beta_1$: **downward bias**. Full OVB direction table:

    | $\text{Corr}(x_2, x_1)$ | $\beta_2 > 0$ | $\beta_2 < 0$ |
    |---|---|---|
    | Positive | Upward bias | Downward bias |
    | Negative | Downward bias | Upward bias |

---

## Question 5

*Lesson L01 · Multicollinearity*

If two regressors are **perfectly** collinear (e.g. $x_2 = 3x_1$), OLS:

**Type:** Multiple Choice

- **A)** Produces estimates with very large standard errors
- **B)** Is undefined — $(X'X)$ is singular and cannot be inverted
- **C)** Produces unbiased but imprecise estimates
- **D)** Automatically drops the collinear regressor

??? success "Show Answer"
    **Answer: B**

    Perfect multicollinearity violates MLR.3 (no perfect linear relationships among regressors). The matrix $X'X$ becomes singular (rank-deficient) and cannot be inverted, so $\hat{\beta} = (X'X)^{-1}X'y$ is undefined. Statistical software will typically drop one of the collinear columns and warn you. *Near* perfect multicollinearity (high but not perfect correlation) is handled differently — OLS works but estimates have very large standard errors.

---

## Question 6

*Lesson L03 · MLR.3 Assumption*

Give a concrete example where perfect multicollinearity would arise due to the dummy variable trap.

**Type:** Short Answer

??? success "Show Answer"
    Suppose you include dummies for **all** seasons: $D_\text{Spring}$, $D_\text{Summer}$, $D_\text{Autumn}$, $D_\text{Winter}$, and also an intercept. Since exactly one season dummy = 1 for every observation: $D_\text{Spring} + D_\text{Summer} + D_\text{Autumn} + D_\text{Winter} = 1$ for all $i$. This is a perfect linear relationship with the intercept column (constant 1). Solution: drop one dummy (the "base group") — include only 3 of 4 season dummies. The omitted category becomes the reference level captured by the intercept.

---

## Question 7

*Lesson L05 · Variance Formula*

The variance of $\hat{\beta}_j$ is $\text{Var}(\hat{\beta}_j) = \sigma^2 / [SST_j(1-R_j^2)]$. What is $R_j^2$ and what does $\text{VIF}_j = 1/(1-R_j^2)$ measure?

**Type:** Short Answer

??? success "Show Answer"
    $R_j^2$ is the **$R^2$ from regressing $x_j$ on all other regressors** in the model. It measures how much of $x_j$'s variation is explained by the other regressors.

    $\text{VIF}_j$ (Variance Inflation Factor) measures how much the variance of $\hat{\beta}_j$ is **inflated** relative to the case where $x_j$ is uncorrelated with all other regressors ($R_j^2 = 0 \Rightarrow \text{VIF} = 1$).

    - $\text{VIF} = 1$: no multicollinearity
    - $\text{VIF} = 5$: $\text{Var}(\hat{\beta}_j)$ is 5× what it would be without collinearity; $R_j^2 = 0.8$
    - $\text{VIF} > 10$: rule-of-thumb threshold for "serious" multicollinearity ($R_j^2 > 0.9$)

---

## Question 8

*Lesson L05 · Adding Variables*

If you add an **irrelevant** variable $x_3$ (truly $\beta_3 = 0$ in the population) to a regression, what happens to $\hat{\beta}_1$?

**Type:** Multiple Choice

- **A)** $\hat{\beta}_1$ becomes biased upward
- **B)** $\hat{\beta}_1$ remains unbiased but its variance increases (or at best stays the same)
- **C)** $\hat{\beta}_1$ becomes more precise because we have more information
- **D)** $\hat{\beta}_1$ is inconsistent

??? success "Show Answer"
    **Answer: B**

    Including an irrelevant variable does not cause bias (since the true $\beta_3 = 0$, there is no OVB from including it). However, $\text{Var}(\hat{\beta}_1)$ increases because: (1) we lose a degree of freedom, and (2) if $x_3$ is correlated with $x_1$, VIF$_1$ rises. This is the bias-variance trade-off in variable selection: omitting a relevant variable causes bias; including an irrelevant one inflates variance. The Gauss-Markov Theorem says OLS is efficient *among correctly specified models*.

---

## Question 9

*Lesson L03 · Gauss-Markov*

What do the five MLR assumptions (MLR.1–MLR.5) together guarantee?

**Type:** Short Answer

??? success "Show Answer"
    Under MLR.1–MLR.5 (linearity, random sampling, no perfect multicollinearity, zero conditional mean $E(u|\mathbf{x})=0$, homoskedasticity $\text{Var}(u|\mathbf{x})=\sigma^2$), the **Gauss-Markov Theorem** guarantees that OLS is **BLUE**: the Best Linear Unbiased Estimator. "Best" means minimum variance among all linear unbiased estimators. Adding MLR.6 (normality: $u|\mathbf{x} \sim N(0,\sigma^2)$) upgrades OLS to **BUE** (Best Unbiased Estimator, not just among linear ones) and validates exact $t$ and $F$ tests in finite samples.

---

## Question 10

*Lesson L04 · Adjusted R²*

Adjusted $R^2 = 1 - \frac{SSR/(n-k-1)}{SST/(n-1)}$. Unlike $R^2$, adjusted $R^2$ can **decrease** when a variable is added. Why?

**Type:** Multiple Choice

- **A)** Because adjusted $R^2$ is always smaller than $R^2$
- **B)** Because adding a variable always reduces SSR, but the penalty for the lost degree of freedom ($n-k-1$ shrinks) may outweigh the SSR reduction if the variable adds little explanatory power
- **C)** Because adjusted $R^2$ is only valid for large samples
- **D)** It cannot decrease — adding variables always improves model fit

??? success "Show Answer"
    **Answer: B**

    $R^2$ never decreases when a variable is added (SSR can only fall or stay flat). Adjusted $R^2$ imposes a **degrees-of-freedom penalty**: the denominator $n-k-1$ shrinks by 1 each time a variable is added. If the reduction in SSR is small (the variable is nearly irrelevant), the penalty outweighs the gain and adjusted $R^2$ falls. Adjusted $R^2$ provides a better criterion for model selection than $R^2$ because it does not reward adding noise variables.

---

## Question 11

*Lesson L05 · FWL Theorem*

The Frisch-Waugh-Lovell (FWL) theorem says $\hat{\beta}_1$ from regressing $y$ on $x_1, x_2$ equals the slope from regressing $\tilde{y}$ on $\tilde{x}_1$. What is $\tilde{x}_1$?

**Type:** Multiple Choice

- **A)** $x_1$ standardised to have mean zero and variance one
- **B)** The residuals from regressing $x_1$ on $x_2$ — the part of $x_1$ not explained by $x_2$
- **C)** $x_1$ minus its sample mean
- **D)** The fitted values from regressing $x_1$ on $x_2$

??? success "Show Answer"
    **Answer: B**

    $\tilde{x}_1 = M_2 x_1$ where $M_2$ is the residual maker for $x_2$. Specifically: regress $x_1$ on $x_2$ and take the residuals. These residuals are the variation in $x_1$ **orthogonal to** $x_2$ — the part of $x_1$ that cannot be predicted by $x_2$. Similarly $\tilde{y} = M_2 y$ are the residuals from regressing $y$ on $x_2$. The FWL slope $\hat{\beta}_1 = \text{Cov}(\tilde{y}, \tilde{x}_1)/\text{Var}(\tilde{x}_1)$ is identical to the multiple regression slope.

---

## Question 12

*Lesson L05 · FWL Application*

In a wage regression of $\ln(\text{wage})$ on education and experience, FWL says the education coefficient represents:

**Type:** Short Answer

??? success "Show Answer"
    The education coefficient captures the **relationship between wages and education after removing the linear influence of experience from both**. Concretely:

    1. Residualise education on experience: $\tilde{\text{educ}} = \text{educ} - \hat{\delta}_0 - \hat{\delta}_1 \cdot \text{exper}$
    2. Residualise log-wage on experience: $\tilde{y} = \ln(\text{wage}) - \hat{\gamma}_0 - \hat{\gamma}_1 \cdot \text{exper}$
    3. $\hat{\beta}_\text{educ} = \text{Cov}(\tilde{y}, \tilde{\text{educ}})/\text{Var}(\tilde{\text{educ}})$

    $\tilde{\text{educ}}$ is the component of education **not predicted by experience**. The regression uses only this "clean" variation. This is precisely what "holding experience constant" means — and why adding experience to the regression changes the education coefficient (it removes the part of the education-wage correlation that was actually driven by experience).

---

## Question 13

*Lesson L02 · Matrix OLS*

For OLS with $n = 100$ observations and $k = 2$ slope regressors (plus intercept), the design matrix $X$ is $100 \times 3$. What is the dimension of $(X'X)$?

**Type:** Multiple Choice

- **A)** $100 \times 100$
- **B)** $3 \times 100$
- **C)** $3 \times 3$
- **D)** $100 \times 3$

??? success "Show Answer"
    **Answer: C**

    $X$ is $n \times (k+1) = 100 \times 3$. Then $X' $ is $3 \times 100$. So $X'X$ is $(3 \times 100)(100 \times 3) = \mathbf{3 \times 3}$. The inverse $(X'X)^{-1}$ is also $3 \times 3$. This is why OLS is computationally easy even with huge $n$ — the key matrix to invert is only $(k+1) \times (k+1)$.

---

## Question 14

*Lesson L04 · Practical OVB*

A study regresses crime rates on the number of police officers per capita, without controlling for poverty. The coefficient on police is *positive* — more police is associated with more crime. Is this causal?

**Type:** Short Answer

??? success "Show Answer"
    Almost certainly **not causal** — this is a classic OVB problem. Poverty (the omitted variable) is likely:
    - Positively correlated with police presence ($\delta_{12} > 0$: governments deploy more police to high-crime/high-poverty areas)
    - Positively affects crime ($\beta_2 > 0$: poverty is a driver of crime)

    Therefore $\beta_2 \cdot \delta_{12} > 0$ → **upward bias** in the police coefficient. The positive association between police and crime reflects reverse causality (more crime → more police) and confounding by poverty — not that police *cause* crime. To estimate the causal effect, one needs an instrument for police deployment (e.g. election cycles affecting political motivation to hire police, as in Levitt 1997) or a natural experiment.

---

## Question 15

*Lesson L02 · Calculation*

**[Calculation]** A regression with $n = 50$, $k = 2$ slope regressors (plus intercept) gives $SSR = 400$ and $SST = 1{,}000$. Calculate:
(a) $R^2$, (b) Adjusted $R^2$, (c) $\hat{\sigma}^2$.

**Type:** Calculation

??? success "Show Answer"
    **(a)** $R^2 = 1 - SSR/SST = 1 - 400/1000 = \mathbf{0.60}$

    **(b)** $\bar{R}^2 = 1 - \frac{SSR/(n-k-1)}{SST/(n-1)} = 1 - \frac{400/47}{1000/49} = 1 - \frac{8.511}{20.408} = 1 - 0.417 = \mathbf{0.583}$

    Adjusted $R^2 < R^2$ (always true). The penalty for $k=2$ regressors is modest here.

    **(c)** $\hat{\sigma}^2 = SSR/(n-k-1) = 400/(50-2-1) = 400/47 \approx \mathbf{8.51}$

---

## Question 16

*Lesson L02 · ECMT5001 style*

**[Short Answer + Calculation]** A regression of $\ln(\text{salary})$ on years of experience and a female dummy gives:

| Variable | Coef | Std Err |
|----------|------|---------|
| experience | 0.045 | 0.008 |
| female | −0.183 | 0.052 |
| intercept | 3.210 | 0.065 |

$n = 200$, $R^2 = 0.41$.

(a) Interpret the experience and female coefficients.
(b) Test $H_0: \beta_\text{female} = 0$ at the 1% significance level. Critical value $t_{0.005, 197} \approx 2.601$.

**Type:** Short Answer + Calculation

??? success "Show Answer"
    **(a) Interpretation:**
    - **Experience:** Each additional year of experience is associated with approximately $100 \times 0.045 = 4.5\%$ higher salary, holding gender constant.
    - **Female:** Female workers earn approximately $100 \times 0.183 = 18.3\%$ less than male workers with the same experience. More precisely: $e^{-0.183} - 1 \approx -16.7\%$.

    **(b) t-test for gender gap:**
    $$t = \frac{-0.183 - 0}{0.052} = \frac{-0.183}{0.052} \approx -3.52$$

    $|t| = 3.52 > t_{0.005, 197} = 2.601$, so **reject $H_0$** at the 1% level. The gender pay gap is statistically significant at the 1% level. Note: this is a conditional gap (holding experience fixed); it does not account for occupational sorting, hours worked, or other confounders.
