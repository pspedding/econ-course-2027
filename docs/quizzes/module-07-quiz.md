# Module M07 Quiz: Misspecification, Proxy Variables & Measurement Error

*12 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. Write out reasoning for short-answer questions.

---

## Question 1

*Lesson L01 · Omitted Variables*

Omitting a relevant variable $x_2$ from the regression of $y$ on $x_1$ causes OLS to be:

**Type:** Multiple Choice

- **A)** Inefficient but unbiased, regardless of correlation between $x_1$ and $x_2$
- **B)** Biased and inconsistent if $\text{Cov}(x_1, x_2) \neq 0$; unbiased if $\text{Cov}(x_1, x_2) = 0$
- **C)** Always biased, even if $x_1$ and $x_2$ are uncorrelated
- **D)** Only biased in small samples

??? success "Show Answer"
    **Answer: B**

    OVB formula: $\text{plim}(\tilde{\beta}_1) = \beta_1 + \beta_2 \cdot \delta_{12}$ where $\delta_{12} = \text{Cov}(x_2,x_1)/\text{Var}(x_1)$.

    - If $\text{Cov}(x_1, x_2) = 0$: $\delta_{12} = 0$ → no bias (though efficiency is lost and $R^2$ is lower)
    - If $\text{Cov}(x_1, x_2) \neq 0$: $\delta_{12} \neq 0$ → OLS is **biased AND inconsistent** (the bias persists as $n \to \infty$)

    This is why more data cannot fix omitted variable bias — it is an identification problem, not a sample size problem.

---

## Question 2

*Lesson L01 · Irrelevant Variables*

Including an irrelevant variable $x_3$ (truly $\beta_3 = 0$) in a regression causes:

**Type:** Multiple Choice

- **A)** Upward bias in all other coefficients
- **B)** No bias but increased variance of $\hat{\beta}_1$ (inefficiency); adjusted $R^2$ may fall
- **C)** Inconsistency of all OLS estimates
- **D)** The model becomes unidentified

??? success "Show Answer"
    **Answer: B**

    Since $\beta_3 = 0$ truly, there is no OVB from including it — $E(\hat{\beta}_1) = \beta_1$ still holds. However:

    1. One degree of freedom is wasted → $\hat{\sigma}^2$ uses $(n-k-2)$ instead of $(n-k-1)$
    2. If $x_3$ is correlated with $x_1$, $\text{VIF}_1$ increases → larger $\text{Var}(\hat{\beta}_1)$

    The trade-off: omitting a relevant variable causes bias; including an irrelevant one causes inefficiency. The bias from omission is typically worse — but large models with many weak controls also suffer.

---

## Question 3

*Lesson L01 · RESET Test*

The Ramsey RESET test adds $\hat{y}^2, \hat{y}^3$ to the regression and tests if their coefficients are jointly zero. What does rejection imply?

**Type:** Multiple Choice

- **A)** The dependent variable is not normally distributed
- **B)** Functional form misspecification — the linear model may be missing nonlinear terms or interactions
- **C)** Heteroskedasticity is present
- **D)** Serial correlation is present

??? success "Show Answer"
    **Answer: B**

    Powered fitted values ($\hat{y}^2, \hat{y}^3$) proxy for the nonlinear combinations of regressors that might be missing from the model. If they are jointly significant ($F$-test rejects), the linear specification is inadequate — possibly missing quadratic terms, interactions, or the wrong functional form (e.g. should use logs).

    RESET does **not** detect heteroskedasticity (use BP/White) or serial correlation (use DW/BG). It is a general functional form test, not a targeted diagnostic.

---

## Question 4

*Lesson L02 · Proxy Variables*

A researcher wants to control for "ability" in a wage regression, but ability is unobserved. They include an IQ test score as a proxy. For this to be valid, the proxy must satisfy:

**Type:** Short Answer

??? success "Show Answer"
    A valid proxy $x_2$ for unobservable $x_2^*$ requires:

    1. **Correlation with the omitted variable:** $\text{Cov}(x_2, x_2^*) \neq 0$ — the proxy must actually measure the latent variable (IQ score must be correlated with true ability)
    2. **Conditional independence:** Once $x_2$ is included, the true omitted variable $x_2^*$ is uncorrelated with the error — i.e. $\text{Cov}(x_2^*, u | x_2) = 0$. The proxy "soaks up" all the variation in $x_2^*$ that is relevant for $y$.

    If the proxy is imperfect (noisy), it only partially reduces OVB — better than nothing, but doesn't fully solve the problem. The IQ score is a commonly used but imperfect proxy for ability; part of ability is captured, part is not.

---

## Question 5

*Lesson L02 · Measurement Error*

Classical errors-in-variables: the true regressor is $x^*$, but you observe $x = x^* + e$ where $e$ is pure measurement noise uncorrelated with $x^*$ and $u$. OLS on the mismeasured $x$ produces:

**Type:** Multiple Choice

- **A)** An unbiased estimator of $\beta_1$
- **B)** An upward-biased estimator
- **C)** Attenuation bias — $\hat{\beta}_1$ is biased toward zero: $|\hat{\beta}_1| < |\beta_1|$
- **D)** Inconsistency only in small samples

??? success "Show Answer"
    **Answer: C — Attenuation bias**

    $$\text{plim}(\hat{\beta}_1) = \beta_1 \cdot \frac{\text{Var}(x^*)}{\text{Var}(x^*) + \text{Var}(e)} = \beta_1 \cdot \lambda$$

    where $\lambda = \text{Var}(x^*)/\text{Var}(x) \in (0,1)$ is the signal-to-total variance ratio. Since $\lambda < 1$, $|\hat{\beta}_1| < |\beta_1|$ — the coefficient is **attenuated toward zero**.

    Intuition: measurement noise in $x$ looks like extra random variation unrelated to $y$, making the slope appear flatter. The more noisy the measurement (larger $\text{Var}(e)$), the worse the attenuation.

---

## Question 6

*Lesson L02 · Attenuation — Calculation*

**[Calculation]** True $\beta_1 = 0.5$. The true variable $x^*$ has $\text{Var}(x^*) = 4$. Measurement error has $\text{Var}(e) = 1$ (so $\text{Var}(x) = 5$). What is $\text{plim}(\hat{\beta}_1)$?

**Type:** Calculation

??? success "Show Answer"
    $$\lambda = \frac{\text{Var}(x^*)}{\text{Var}(x^*) + \text{Var}(e)} = \frac{4}{4 + 1} = \frac{4}{5} = 0.8$$

    $$\text{plim}(\hat{\beta}_1) = \beta_1 \cdot \lambda = 0.5 \times 0.8 = \mathbf{0.4}$$

    OLS attenuates the true effect by 20%. To recover $\beta_1 = 0.5$, you need an instrument for $x$ — a variable correlated with $x^*$ but not with the measurement error $e$ (e.g. a second noisy measure of the same concept).

---

## Question 7

*Lesson L03 · Missing Data*

Data are **Missing Completely At Random (MCAR)**. OLS on the complete cases is:

**Type:** Multiple Choice

- **A)** Biased — any missing data causes bias
- **B)** Unbiased and consistent — MCAR means the complete cases are a random subsample
- **C)** Consistent but biased in finite samples
- **D)** Only valid if less than 10% of data is missing

??? success "Show Answer"
    **Answer: B**

    MCAR means the probability of missingness is unrelated to both observed and unobserved variables. The complete cases are then a random subset of the full sample — OLS on this subset has the same properties as OLS on the full sample.

    - **MAR (Missing At Random):** Missingness depends on observed $x$, not unobserved $u$ — OLS is still consistent if $x$ is included in the model
    - **MNAR (Missing Not At Random):** Missingness depends on $y$ or $u$ — **selection bias**; OLS is inconsistent. Example: only employed workers report wages → wages are MNAR (low earners with zero wages are selectively excluded)

---

## Question 8

*Lesson L03 · Selection Bias*

A study of wages only surveys employed workers. Why is this a selection problem?

**Type:** Short Answer

??? success "Show Answer"
    This is a **non-random sample** — workers who choose to work may be systematically different from non-workers on unobservables (higher motivation, better health, higher ability) that also affect wages. The sample of workers is thus selected on characteristics correlated with the error term in the wage equation.

    Formally: $E(u \mid \text{employed}) \neq 0$ even if $E(u) = 0$ in the full population. OLS on the employed-only sample is biased.

    The classic fix is the **Heckman two-step**: model the selection equation (who works), compute the inverse Mills ratio (IMR), and add it to the wage regression as an additional control. The IMR corrects for the selection bias under distributional assumptions.

---

## Question 9

*Lesson L01 · Functional Form Misspecification*

The true model is $y = \beta_0 + \beta_1 x + \beta_2 x^2 + u$ but you estimate $y = \beta_0 + \beta_1 x + u$. This causes:

**Type:** Multiple Choice

- **A)** No problem if the quadratic term is small
- **B)** OVB: $x^2$ is omitted; since $x^2$ is a function of $x$, $\text{Cov}(x, x^2) \neq 0$ → $\hat{\beta}_1$ is biased and inconsistent
- **C)** Only heteroskedasticity
- **D)** Only inflated standard errors

??? success "Show Answer"
    **Answer: B**

    The omitted variable here is $x^2$. Since $x^2$ is a deterministic function of $x$, they are correlated — $\text{Cov}(x, x^2) \neq 0$ for most $x$ distributions. The OVB formula applies: $\tilde{\beta}_1 = \beta_1 + \beta_2 \cdot \delta_{12}$ where $\delta_{12} = \text{Cov}(x, x^2)/\text{Var}(x) \neq 0$.

    The RESET test would detect this: powered fitted values $\hat{y}^2$ (which include $x^2$ terms) would be significant. Remedy: add $x^2$ to the model.

---

## Question 10

*Lesson L02 · Measurement Error in y*

Classical measurement error is in the **dependent variable** $y$: you observe $\tilde{y} = y + v$ where $v$ is noise uncorrelated with $x$ and $u$. What is the effect on OLS?

**Type:** Short Answer

??? success "Show Answer"
    **No bias or inconsistency** — measurement error in $y$ (when uncorrelated with regressors) simply adds to the error term:

    $$\tilde{y} = \beta_0 + \beta_1 x + (u + v)$$

    The composite error $(u + v)$ still satisfies $E(u + v \mid x) = 0$ since both $u$ and $v$ are uncorrelated with $x$. OLS is unbiased and consistent.

    The only consequence: $\text{Var}(u + v) = \sigma_u^2 + \sigma_v^2 > \sigma_u^2$ — the error variance is larger, making OLS **less precise** (larger standard errors, lower $R^2$). Contrast with measurement error in $x$: that causes attenuation bias; error in $y$ does not.

---

## Question 11

*Lesson L01 · Model Selection*

A researcher is choosing between two models: Model A (3 regressors, $R^2 = 0.72$) and Model B (8 regressors, $R^2 = 0.75$). Which should they prefer and why?

**Type:** Short Answer

??? success "Show Answer"
    **Cannot simply compare $R^2$** — it always rises (or stays flat) when more regressors are added.

    Better criteria:

    1. **Adjusted $R^2$**: penalises added regressors. If Model B's adjusted $R^2 >$ Model A's, the extra variables add genuine explanatory power.
    2. **$F$-test**: test whether the 5 additional regressors in B are jointly significant. If $F < F_\text{critical}$, they are not jointly useful and Model A is preferred.
    3. **AIC/BIC**: information criteria that penalise complexity; BIC penalises more strongly.
    4. **Theory**: do the extra 5 regressors in B have theoretical justification? Are they causing multicollinearity?

    In practice: if the $F$-test for the 5 extra regressors fails to reject $H_0$ (jointly insignificant), prefer the parsimonious Model A. Occam's razor applies — complexity without payoff increases standard errors and reduces interpretability.

---

## Question 12

*Lesson L02 · IV Fix for Measurement Error*

**[Short Answer]** Measurement error in education (people mis-report years of schooling) attenuates the OLS wage-education slope. How would IV help?

**Type:** Short Answer

??? success "Show Answer"
    Use an **instrument $z$ correlated with true education $x^*$ but uncorrelated with the measurement error $e$**. A good candidate: parental education or proximity to a college — these affect true years of schooling through family background or opportunity, not through reporting bias.

    **Why it works:** The IV estimator $\hat{\beta}_{IV} = \text{Cov}(z,y)/\text{Cov}(z,x)$ uses only the variation in $x$ that is driven by $z$. Since $z$ is uncorrelated with measurement error $e$, the $z$-driven variation in $x$ is "clean" — reflecting variation in $x^*$ only. The IV therefore estimates $\beta_1$ consistently despite the mismeasured $x$.

    Formally: $\text{plim}(\hat{\beta}_{IV}) = \text{Cov}(z,y)/\text{Cov}(z,x) = \beta_1 \cdot \text{Cov}(z,x^*)/\text{Cov}(z,x) = \beta_1$ when $\text{Cov}(z,e) = 0$.
