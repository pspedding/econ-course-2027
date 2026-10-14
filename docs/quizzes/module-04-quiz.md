# Module M04 Quiz: Inference — t-Tests & F-Tests

*16 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. Show full working for hypothesis tests — state the test statistic, critical value, and conclusion.

---

## Question 1

*Lesson L02 · t-Statistic*

The t-statistic $t = (\hat{\beta}_j - \beta_{j0})/\text{se}(\hat{\beta}_j)$ follows a $t_{n-k-1}$ distribution exactly when:

**Type:** Multiple Choice

- **A)** The sample size is large ($n > 30$)
- **B)** The CLM assumptions hold: MLR.1–MLR.5 plus MLR.6 (normality of $u$)
- **C)** The regressors are normally distributed
- **D)** Heteroskedasticity is absent

??? success "Show Answer"
    **Answer: B**

    Under the Classical Linear Model (CLM) assumptions MLR.1–MLR.6, $t = (\hat{\beta}_j - \beta_{j0})/\text{se}(\hat{\beta}_j) \sim t_{n-k-1}$ **exactly** in finite samples. MLR.6 (normality of $u$) is the critical additional assumption — it ensures $\hat{\beta}_j$ is normally distributed conditional on $X$, making the standardised ratio a $t$ distribution. Without MLR.6, the t-statistic is asymptotically $N(0,1)$ by the CLT (used for large samples).

---

## Question 2

*Lesson L02 · t-Test Calculation*

**[Calculation]** $\hat{\beta}_1 = 2.4$, $\text{se}(\hat{\beta}_1) = 0.8$, $n = 32$, $k = 2$ regressors (plus intercept). Test $H_0: \beta_1 = 0$ vs $H_1: \beta_1 \neq 0$ at $\alpha = 0.05$. Critical value $t_{0.025, 29} = 2.045$.

**Type:** Calculation

??? success "Show Answer"
    $$t = \frac{\hat{\beta}_1}{\text{se}(\hat{\beta}_1)} = \frac{2.4}{0.8} = \mathbf{3.0}$$

    Since $|t| = 3.0 > t_{0.025, 29} = 2.045$, **reject $H_0$** at the 5% level. The coefficient is statistically significant.

    Degrees of freedom: $df = n - k - 1 = 32 - 2 - 1 = 29$.

---

## Question 3

*Lesson L02 · One-Sided Test*

**[Calculation]** $H_0: \beta_1 \leq 0$ vs $H_1: \beta_1 > 0$. Observed $t = 1.85$ with $df = n - k - 1 = 38$. At $\alpha = 0.05$, the one-tailed critical value $t_{0.05, 38} = 1.686$. Reject?

**Type:** Calculation

??? success "Show Answer"
    Since $t = 1.85 > t_{0.05, 38} = 1.686$, **reject $H_0$** at the 5% level (one-tailed).

    Note: If we had used a two-tailed test, the critical value would be $t_{0.025, 38} \approx 2.024$, and we would *fail* to reject. This illustrates the power advantage of a one-tailed test when the direction of the effect is known a priori. **However:** the one-tailed test is only valid if the directional hypothesis was specified before seeing the data.

---

## Question 4

*Lesson L03 · Confidence Interval*

**[Calculation]** $\hat{\beta}_1 = 3.2$, $\text{se}(\hat{\beta}_1) = 0.9$, $n = 60$, $k = 3$ regressors. Construct a 95% CI for $\beta_1$. Use $t_{0.025, 56} \approx 2.003$.

**Type:** Calculation

??? success "Show Answer"
    $$\text{CI} = \hat{\beta}_1 \pm t_{0.025, 56} \times \text{se}(\hat{\beta}_1) = 3.2 \pm 2.003 \times 0.9 = 3.2 \pm 1.803$$

    $$\mathbf{[1.397,\ 5.003]}$$

    Since the CI does not include zero, we reject $H_0: \beta_1 = 0$ at the 5% level — consistent with a t-test. The interval can also be used to test any specific null value: e.g. $H_0: \beta_1 = 5$ is rejected since 5 lies outside $[1.40, 5.00]$ — just barely.

---

## Question 5

*Lesson L02 · p-Value*

A coefficient has $t = 2.15$ with 45 degrees of freedom. For a two-tailed test, $p < 0.05$?

**Type:** Multiple Choice

- **A)** No — $p > 0.05$ because $t = 2.15 < t_{0.025,45} = 2.014$... wait, which is correct?
- **B)** Yes — $t_{0.025, 45} \approx 2.014 < 2.15$, so $p < 0.05$
- **C)** Cannot determine without knowing $\sigma^2$
- **D)** No — we need $n$ not just df

??? success "Show Answer"
    **Answer: B**

    $t_{0.025, 45} \approx 2.014$ (from t-tables). Since $|t| = 2.15 > 2.014$, the two-tailed p-value $< 0.05$. More precisely, $p = 2 \times P(T_{45} > 2.15) \approx 2 \times 0.018 = 0.036$. We reject $H_0: \beta_j = 0$ at the 5% level.

---

## Question 6

*Lesson L05 · Economic Significance*

A regression of firm profits on advertising spending gives: $\hat{\beta}_\text{advertising} = 0.0001$ with $p = 0.001$. Is this effect practically important?

**Type:** Short Answer

??? success "Show Answer"
    **Probably not** — this is a case of **statistical significance without economic significance**. With a very large sample ($n$ must be large for $p = 0.001$ on such a tiny coefficient), even trivially small effects become statistically significant.

    The coefficient $0.0001$ means \$1 extra advertising spending raises profits by \$0.0001 — one hundredth of a cent. That is economically negligible regardless of the p-value.

    **Key lesson:** Always report effect sizes alongside p-values. Statistical significance tells you whether the effect is distinguishable from zero; economic significance tells you whether it matters. For policy, the magnitude and confidence interval matter far more than the p-value.

---

## Question 7

*Lesson L04 · F-Test Setup*

Testing the joint hypothesis $H_0: \beta_1 = 0 \text{ AND } \beta_2 = 0$ — how many restrictions $q$ does this impose?

**Type:** Multiple Choice

- **A)** 1
- **B)** 2
- **C)** Depends on the sample size
- **D)** Depends on the number of regressors

??? success "Show Answer"
    **Answer: B**

    Each "$\beta_j = $ [specific value]" is one linear restriction. Testing two coefficients simultaneously imposes $q = 2$ restrictions. In general, $q$ equals the number of equality constraints in $H_0$. The F-test statistic with $q$ and $n-k-1$ degrees of freedom tests whether all $q$ restrictions hold simultaneously — this cannot be replicated by running $q$ separate t-tests (which would inflate the Type I error rate).

---

## Question 8

*Lesson L04 · F-Test Calculation*

**[Calculation]** Restricted model (imposing $H_0$): $SSR_r = 600$. Unrestricted model: $SSR_{ur} = 480$. $q = 2$ restrictions, $n = 100$, $k = 4$ regressors (unrestricted). Calculate $F$ and compare to $F_{2, 95, 0.05} \approx 3.09$.

**Type:** Calculation

??? success "Show Answer"
    $$F = \frac{(SSR_r - SSR_{ur})/q}{SSR_{ur}/(n-k-1)} = \frac{(600-480)/2}{480/(100-4-1)} = \frac{120/2}{480/95} = \frac{60}{5.053} \approx \mathbf{11.87}$$

    Since $F = 11.87 \gg F_{2, 95, 0.05} = 3.09$, **reject $H_0$** strongly. The two restricted coefficients are jointly significant.

---

## Question 9

*Lesson L04 · F vs t*

For a single restriction ($q = 1$), $F = t^2$. If $t = 2.5$, what is $F$?

**Type:** Calculation

??? success "Show Answer"
    $$F = t^2 = (2.5)^2 = \mathbf{6.25}$$

    For a single restriction, the F-test and the two-tailed t-test are equivalent: reject $H_0$ at 5% if $F > F_{1, n-k-1, 0.05} \approx 3.84$ (which equals $t_{0.025}^2 \approx 1.96^2 = 3.84$). The F-test becomes essential (and more powerful than repeated t-tests) when testing **joint** hypotheses with $q \geq 2$.

---

## Question 10

*Lesson L04 · Overall F-Test*

The **overall F-test** tests $H_0: \beta_1 = \beta_2 = \cdots = \beta_k = 0$ (all slopes are zero). If $F = 8.3$ with $p < 0.001$, the correct conclusion is:

**Type:** Multiple Choice

- **A)** At least one slope coefficient is individually significant
- **B)** The regressors, as a group, explain a statistically significant portion of the variation in $y$
- **C)** The model is correctly specified
- **D)** $R^2$ is large

??? success "Show Answer"
    **Answer: B**

    The overall F-test asks: "Is the regression as a whole useful?" — do the regressors jointly explain any variation in $y$? Rejecting $H_0$ means at least one $\beta_j \neq 0$, so the model has joint explanatory power. This does **not** imply any individual coefficient is significant (they could all be jointly significant due to multicollinearity), nor does it validate model specification ($R^2$ could still be low).

---

## Question 11

*Lesson L01 · Asymptotic Normality*

Why does asymptotic normality matter, and when does it apply?

**Type:** Short Answer

??? success "Show Answer"
    **Why it matters:** Without MLR.6 (normality of $u$), the t and F statistics are not *exactly* t- and F-distributed in finite samples. However, by the **Central Limit Theorem**, as $n \to \infty$, $\hat{\beta}_j$ is approximately normally distributed regardless of the distribution of $u$ (under regularity conditions). This means t and F tests are asymptotically valid.

    **When it applies:** Large samples ($n$ large relative to $k$). The approximation is better when $u$'s distribution is not too skewed or heavy-tailed. In practice, $n \geq 50$–100 usually suffices for good approximations; with binary or skewed regressors, larger samples may be needed. For small $n$ with non-normal errors, bootstrap inference is preferred.

---

## Question 12

*Lesson L05 · Interpreting Output*

A regression table shows: coef = $1.23$, se = $0.41$, $t = 3.00$, $p = 0.003$, 95% CI = $[0.42, 2.04]$. Write a complete interpretation.

**Type:** Short Answer

??? success "Show Answer"
    The estimated coefficient is **1.23** [units of $y$ per unit of $x$]. The standard error of 0.41 reflects sampling uncertainty. The t-statistic of 3.00 tests $H_0: \beta = 0$; with $p = 0.003 < 0.05$, we **reject $H_0$** — the coefficient is statistically significant at the 5% and 1% levels. The 95% confidence interval $[0.42, 2.04]$ tells us: if we repeated the sampling procedure many times, 95% of constructed intervals would contain the true $\beta$. Since zero is outside this interval, significance at 5% is confirmed. The effect size (1.23) should be assessed for economic significance relative to the scale of $y$ and $x$.

---

## Question 13

*Lesson L02 · Linear Combination*

You want to test $H_0: \beta_1 = \beta_2$ (two coefficients are equal). How do you construct a t-test?

**Type:** Short Answer

??? success "Show Answer"
    Reparametrise: define $\theta = \beta_1 - \beta_2$ and test $H_0: \theta = 0$.

    **Method 1:** Create a new variable $\tilde{x} = x_1 - x_2$ and include $x_2$ and $\tilde{x}$ in the regression. The coefficient on $\tilde{x}$ is $\theta = \beta_1 - \beta_2$, and its standard t-test applies.

    **Method 2 (direct):** $t = (\hat{\beta}_1 - \hat{\beta}_2)/\text{se}(\hat{\beta}_1 - \hat{\beta}_2)$ where $\text{Var}(\hat{\beta}_1 - \hat{\beta}_2) = \text{Var}(\hat{\beta}_1) + \text{Var}(\hat{\beta}_2) - 2\text{Cov}(\hat{\beta}_1, \hat{\beta}_2)$. The covariance term is available from the variance-covariance matrix of $\hat{\beta}$, reported by most software. **Never** test $H_0: \beta_1 = \beta_2$ by comparing their individual CIs — this ignores the covariance.

---

## Question 14

*Lesson L04 · ECMT5001 style*

**[Calculation]** A regression of house price (AUD) on size (sqm), bedrooms, and distance from CBD gives $R^2 = 0.72$, $n = 150$. The restricted model (dropping bedrooms and distance, keeping only size and intercept) gives $SSR_r = 2{,}400$. The unrestricted $SSR_{ur} = 1{,}800$. Test $H_0: \beta_\text{bedrooms} = \beta_\text{distance} = 0$ at the 5% level. $F_{2, 146, 0.05} \approx 3.06$.

**Type:** Calculation

??? success "Show Answer"
    $q = 2$ restrictions (two slopes set to zero). Unrestricted model has $k = 3$ regressors (size, bedrooms, distance) $\Rightarrow df_{ur} = n - k - 1 = 150 - 3 - 1 = 146$.

    $$F = \frac{(SSR_r - SSR_{ur})/q}{SSR_{ur}/df_{ur}} = \frac{(2400 - 1800)/2}{1800/146} = \frac{300}{12.33} \approx \mathbf{24.3}$$

    Since $F = 24.3 \gg F_{2, 146, 0.05} = 3.06$, **reject $H_0$** strongly. Bedrooms and distance from CBD are jointly highly significant — excluding them would be a major specification error.

---

## Question 15

*Lesson L01 · Normality Assumption*

MLR.6 says $u \mid \mathbf{x} \sim N(0, \sigma^2)$. What does this assumption add over MLR.1–MLR.5, and when is it strictly needed?

**Type:** Multiple Choice

- **A)** It adds nothing — MLR.1–MLR.5 are sufficient for all econometric inference
- **B)** It ensures exact $t_{n-k-1}$ and $F_{q,n-k-1}$ distributions in finite samples; without it, these hold only asymptotically
- **C)** It is needed only for OLS to be unbiased
- **D)** It ensures that OLS is consistent

??? success "Show Answer"
    **Answer: B**

    MLR.1–MLR.5 give BLUE (Gauss-Markov) and imply asymptotic normality of $\hat{\beta}$ (so t and F tests are approximately valid in large samples). MLR.6 additionally ensures $\hat{\beta}_j \mid X \sim N(\beta_j, \sigma^2(X'X)^{-1}_{jj})$ **exactly** in finite samples, making t and F statistics exactly distributed — critical for small samples. If errors are non-normal (e.g. skewed, heavy-tailed), rely on large-sample approximations or the bootstrap.

---

## Question 16

*Lesson L03 · CI Interpretation*

"I am 95% confident that $\beta_1$ lies in $[1.2,\ 3.8]$." What is the precise frequentist meaning of this statement?

**Type:** Short Answer

??? success "Show Answer"
    **Precise meaning:** If we were to draw many random samples from the population and compute a 95% CI from each sample, **95% of those intervals would contain the true parameter** $\beta_1$.

    **Common misconception:** "$\beta_1$ is in $[1.2, 3.8]$ with probability 95%." This is wrong in the frequentist framework — $\beta_1$ is a fixed (unknown) constant, not a random variable. A given realised interval either contains $\beta_1$ or it doesn't; there is no probability about it. The 95% refers to the **procedure** (the long-run coverage rate), not the specific interval.

    The Bayesian credible interval does have the direct probability interpretation, but requires a prior distribution on $\beta_1$.
