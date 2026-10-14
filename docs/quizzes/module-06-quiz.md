# Module M06 Quiz: Heteroskedasticity

*14 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. For test questions, state H₀, test statistic, critical value, and conclusion.

---

## Question 1

*Lesson L01 · Definition*

Heteroskedasticity violates which Gauss-Markov assumption?

**Type:** Multiple Choice

- **A)** MLR.1 — Linearity in parameters
- **B)** MLR.4 — Zero conditional mean $E(u|\mathbf{x}) = 0$
- **C)** MLR.5 — Homoskedasticity $\text{Var}(u|\mathbf{x}) = \sigma^2$
- **D)** MLR.3 — No perfect multicollinearity

??? success "Show Answer"
    **Answer: C**

    **Homoskedasticity (MLR.5)** requires $\text{Var}(u_i | \mathbf{x}_i) = \sigma^2$ — constant error variance across all observations. **Heteroskedasticity** means $\text{Var}(u_i | \mathbf{x}_i) = \sigma_i^2$ varies with $i$ (depends on the regressors or observation characteristics). This leaves OLS unbiased and consistent (MLR.4 is intact), but violates the efficiency condition needed for Gauss-Markov.

---

## Question 2

*Lesson L01 · Consequences*

When heteroskedasticity is present, OLS:

**Type:** Multiple Choice

- **A)** Is biased and inconsistent
- **B)** Is unbiased and consistent, but no longer BLUE; standard errors are incorrect, invalidating t and F tests
- **C)** Is still BLUE — heteroskedasticity only affects efficiency, not inference
- **D)** Produces coefficients that are too large in absolute value

??? success "Show Answer"
    **Answer: B**

    Since heteroskedasticity does not violate MLR.1–MLR.4, OLS remains **unbiased** ($E(\hat{\beta}|X) = \beta$) and **consistent**. However:

    1. OLS is **no longer BLUE** — it is no longer the minimum-variance linear unbiased estimator (WLS with correct weights beats it).
    2. The standard OLS standard error formulas assume homoskedasticity; with heteroskedasticity they are **biased** → t-statistics and F-statistics are invalid → confidence intervals and hypothesis tests are unreliable (typically too narrow → inflated Type I error).

---

## Question 3

*Lesson L01 · Detection*

A residual plot shows residuals fanning out (increasing spread) as fitted values $\hat{y}$ increase. This pattern suggests:

**Type:** Multiple Choice

- **A)** Serial correlation — errors are correlated across observations
- **B)** Heteroskedasticity — error variance increases with the level of the fitted value
- **C)** Omitted variable bias — a relevant variable is missing
- **D)** Perfect multicollinearity among the regressors

??? success "Show Answer"
    **Answer: B**

    A **fan pattern** (residuals spread wider at higher fitted values) is the classic visual signature of heteroskedasticity where $\text{Var}(u_i) \propto \hat{y}_i$ or some function of the regressors. Common causes: wage data (high earners have more earnings variability), firm-level data (larger firms have larger absolute errors), cross-country data (larger economies have more variable growth). The remedy is robust standard errors or WLS.

---

## Question 4

*Lesson L02 · Breusch-Pagan Test*

Describe the Breusch-Pagan (BP) test for heteroskedasticity step by step.

**Type:** Short Answer

??? success "Show Answer"
    **Steps:**

    1. Estimate the original regression by OLS: $y = X\beta + u$. Obtain residuals $\hat{u}_i$.
    2. Compute squared residuals $\hat{u}_i^2$.
    3. Regress $\hat{u}_i^2$ on the original regressors $x_1, \ldots, x_k$ (and a constant): $\hat{u}_i^2 = \delta_0 + \delta_1 x_{i1} + \cdots + \delta_k x_{ik} + v_i$.
    4. Compute the **LM statistic**: $LM = n \cdot R^2_{\hat{u}^2}$ where $R^2_{\hat{u}^2}$ is the $R^2$ from the auxiliary regression.
    5. Under $H_0$ (homoskedasticity), $LM \sim \chi^2_k$ asymptotically.
    6. Reject $H_0$ if $LM > \chi^2_{k, \alpha}$.

    **$H_0$:** $\delta_1 = \delta_2 = \cdots = \delta_k = 0$ (error variance does not depend on regressors).

    The BP test assumes heteroskedasticity is a **linear function** of the regressors. If the true form is nonlinear, the White test (which adds squared and cross terms) has more power.

---

## Question 5

*Lesson L02 · BP Test Calculation*

**[Calculation]** You run the auxiliary regression of $\hat{u}_i^2$ on $x_1$ and $x_2$ with $n = 200$ observations. The auxiliary regression gives $R^2 = 0.08$. Test for heteroskedasticity at the 5% level. $\chi^2_{2, 0.05} = 5.99$.

**Type:** Calculation

??? success "Show Answer"
    $$LM = n \cdot R^2 = 200 \times 0.08 = \mathbf{16.0}$$

    Since $LM = 16.0 > \chi^2_{2, 0.05} = 5.99$, **reject $H_0$** at the 5% level. There is statistically significant evidence of heteroskedasticity. OLS standard errors are unreliable — use robust (HC) standard errors or WLS.

    Note: $k = 2$ regressors (not counting the intercept in the auxiliary regression), so df = 2.

---

## Question 6

*Lesson L02 · White vs BP*

What is the key difference between the White test and the Breusch-Pagan test? When would you prefer the White test?

**Type:** Short Answer

??? success "Show Answer"
    **Key difference:** The Breusch-Pagan test assumes heteroskedasticity is a **linear function** of the regressors ($\text{Var}(u_i) = \sigma^2 h(\delta_0 + \delta_1 x_1 + \cdots + \delta_k x_k)$). The **White test** is more general — it adds **squared terms** and **cross-products** of all regressors to the auxiliary regression, allowing for nonlinear heteroskedasticity.

    **Prefer the White test when:**
    - You suspect nonlinear heteroskedasticity (e.g. variance proportional to $x^2$)
    - You are unsure of the functional form of the heteroskedasticity
    - After a BP test that fails to reject, if the residual plot still suggests a problem

    **Cost of White test:** Uses more degrees of freedom (with $k$ regressors: $2k + \binom{k}{2}$ terms in the auxiliary regression), reducing power in small samples. The BP test is preferred when the functional form of heteroskedasticity is known or suspected to be linear.

    *(Adapted from MIT 14.32 rec_4_20: "There is no universally better test — BP is better when the linear functional form is correct; White is better when nonlinear heteroskedasticity is present.")*

---

## Question 7

*Lesson L02 · White Test Degrees of Freedom*

**[Calculation]** With $k = 2$ original regressors, the White test auxiliary regression includes: the 2 original regressors, their squares ($x_1^2$, $x_2^2$), and their cross-product ($x_1 x_2$). How many regressors (excluding the intercept) are in the White auxiliary regression?

**Type:** Calculation

??? success "Show Answer"
    - Original regressors: $x_1$, $x_2$ → **2 terms**
    - Squared terms: $x_1^2$, $x_2^2$ → **2 terms**
    - Cross-product: $x_1 x_2$ → **1 term**

    **Total = 5 terms** → degrees of freedom for the $\chi^2$ test: $df = 5$.

    General formula for $k$ regressors: $k + k + \binom{k}{2} = 2k + k(k-1)/2$ terms. For $k=3$: $6 + 3 = 9$ terms. This rapid growth in df explains why the White test loses power quickly as $k$ increases.

---

## Question 8

*Lesson L03 · Robust Standard Errors*

Robust (heteroskedasticity-consistent / HC) standard errors fix the **inference** problem from heteroskedasticity but not the **efficiency** problem. Explain why.

**Type:** Short Answer

??? success "Show Answer"
    **Fixing inference:** Robust (White/Huber-Eicker) SEs use a consistent estimator of $\text{Var}(\hat{\beta}|X)$ that remains valid under any form of heteroskedasticity: $\widehat{\text{Var}}(\hat{\beta}) = (X'X)^{-1} \left(\sum \hat{u}_i^2 x_i x_i'\right) (X'X)^{-1}$. Using these SEs for t and F tests gives asymptotically correct inference.

    **Not fixing efficiency:** Robust SEs still use **OLS point estimates** $\hat{\beta}$. OLS is no longer BLUE under heteroskedasticity — WLS with weights $1/\sigma_i$ would give more precise (lower-variance) estimates. Robust SEs simply correct the reported uncertainty around the (inefficient) OLS estimates. They do not change $\hat{\beta}$ itself.

    **Practical implication:** When heteroskedasticity is suspected, always report robust SEs. But if the form of heteroskedasticity is known, use WLS for efficiency gains.

---

## Question 9

*Lesson L03 · When to Use Robust SEs*

You run a regression and suspect heteroskedasticity but are unsure of its form. Which SEs should you report?

**Type:** Multiple Choice

- **A)** OLS SEs — they are always valid with large samples
- **B)** Robust (HC) SEs — valid asymptotically under any form of heteroskedasticity
- **C)** WLS SEs — always more efficient than OLS
- **D)** Bootstrap SEs — always preferred over asymptotic SEs

??? success "Show Answer"
    **Answer: B**

    When the form of heteroskedasticity is **unknown**, robust (HC) SEs are the safe default. They are valid asymptotically regardless of the heteroskedasticity pattern. OLS SEs (Answer A) are invalid under heteroskedasticity even in large samples — they are biased, not just imprecise. WLS (C) requires knowing the form of heteroskedasticity to choose correct weights; misspecifying the weights can make things worse. Bootstrap SEs (D) are a good alternative but computationally intensive and not always needed.

    **Modern practice:** Most applied econometricians report robust SEs by default, even when heteroskedasticity is not confirmed — the cost is negligible (slightly less power under homoskedasticity) and the protection against invalid inference is valuable.

---

## Question 10

*Lesson L04 · WLS Weights*

If $\text{Var}(u_i) = \sigma^2 \cdot x_i$ (error variance proportional to $x_i$), what weight should observation $i$ receive in WLS?

**Type:** Multiple Choice

- **A)** $w_i = x_i$
- **B)** $w_i = 1/x_i$
- **C)** $w_i = \sqrt{x_i}$
- **D)** $w_i = 1/\sqrt{x_i}$

??? success "Show Answer"
    **Answer: B — $w_i = 1/x_i$**

    WLS multiplies each observation by $1/\sqrt{h_i}$ (transforming the equation), where $\text{Var}(u_i) = \sigma^2 h_i$. Here $h_i = x_i$, so the **weight** applied in WLS is $w_i = 1/h_i = 1/x_i$.

    After weighting: $\tilde{y}_i = y_i/\sqrt{x_i}$, $\tilde{x}_i = x_i/\sqrt{x_i} = \sqrt{x_i}$, $\tilde{u}_i = u_i/\sqrt{x_i}$. Then $\text{Var}(\tilde{u}_i) = \sigma^2 x_i / x_i = \sigma^2$ — homoskedastic. OLS on the transformed model is equivalent to WLS and is now BLUE.

---

## Question 11

*Lesson L04 · FGLS*

In Feasible GLS (FGLS), you estimate $\ln(\hat{u}_i^2) = \delta_0 + \delta_1 x_{i1} + \delta_2 x_{i2} + v_i$ and obtain fitted values $\hat{g}_i$. You then set $\hat{h}_i = e^{\hat{g}_i}$. What weight do you use in the subsequent WLS step?

**Type:** Multiple Choice

- **A)** $w_i = \hat{h}_i$
- **B)** $w_i = 1/\hat{h}_i$
- **C)** $w_i = \ln(\hat{h}_i)$
- **D)** $w_i = \sqrt{\hat{h}_i}$

??? success "Show Answer"
    **Answer: B — $w_i = 1/\hat{h}_i$**

    The auxiliary log-regression estimates $\ln(\text{Var}(u_i)) \approx \hat{g}_i$, so $\hat{h}_i = e^{\hat{g}_i}$ estimates $\text{Var}(u_i)/\sigma^2$. WLS requires weighting by the inverse of the estimated variance: $w_i = 1/\hat{h}_i$. This is FGLS — it is efficient when the model for $h_i$ is correct, and is asymptotically as efficient as GLS with known $h_i$. In practice, FGLS beats OLS (more efficient) but is less reliable than robust SEs when the heteroskedasticity model is misspecified.

---

## Question 12

*Lesson L02 · MIT-Style Comparison*

**[Short Answer — adapted from MIT 14.32 rec_4_20]** "Which is better — the Breusch-Pagan test or the White test?" Give a balanced answer.

**Type:** Short Answer

??? success "Show Answer"
    **Neither is universally better** — each has advantages:

    **BP test advantages:**
    - More powerful when heteroskedasticity is actually a linear function of the regressors
    - Uses fewer degrees of freedom → more power in small samples
    - Simpler to implement and interpret

    **White test advantages:**
    - More general — detects nonlinear heteroskedasticity that BP misses
    - Also detects certain specification errors (since the White test statistic is related to the general test for misspecification)
    - Does not require prior knowledge of the heteroskedasticity's functional form

    **Practical recommendation:** Run BP first. If rejected, heteroskedasticity is confirmed. If not rejected but the residual plot looks suspicious, run the White test as a robustness check. Regardless of test results, in applied work it is now standard to report robust SEs — making the test results less critical for inference (though still important for understanding the data structure).

---

## Question 13

*Lesson L01 · Log Transformation*

Wages are often modelled as $\ln(\text{wage})$ rather than wage levels. Why does taking logs reduce heteroskedasticity?

**Type:** Short Answer

??? success "Show Answer"
    **Log transformation compresses the scale** of the dependent variable, which tends to reduce heteroskedasticity when the variance of the outcome grows with its level.

    **Mechanism:** If $\text{Var}(y_i) \propto \mu_i^2$ (i.e. a constant *coefficient of variation*), then $\text{Var}(\ln y_i) \approx \text{Var}(y_i)/\mu_i^2 \approx $ constant — homoskedastic. This is exactly the case for wages: high earners have higher *absolute* variance but similar *proportional* variability. The log transformation effectively converts absolute dispersion to proportional dispersion.

    Additionally, log-wages are more normally distributed than levels (wages are right-skewed), which validates the normality assumption for exact finite-sample inference.

---

## Question 14

*Lesson L03 · ECMT5001-Style*

**[Short Answer + Calculation]** A regression of house prices on income and household size gives:

| | Coefficient | OLS SE | Robust SE |
|--|--|--|--|
| Intercept | 120,000 | 35,000 | 48,000 |
| Income | 3,840 | 1,200 | 1,670 |
| Household size | −8,000 | 2,500 | 3,200 |

(a) Calculate the t-statistics using OLS SEs and robust SEs for the income coefficient.
(b) Is the income effect still significant at 5% under robust SEs? (Critical value $\approx 1.96$.)
(c) What does the change in SEs suggest about the data?

**Type:** Short Answer + Calculation

??? success "Show Answer"
    **(a) t-statistics for income:**

    - OLS: $t = 3840/1200 = \mathbf{3.20}$
    - Robust: $t = 3840/1670 = \mathbf{2.30}$

    **(b)** Since robust $|t| = 2.30 > 1.96$, the income effect is **still significant at 5%** under robust SEs — though less convincingly so (it would not be significant at 1% with the robust SE).

    **(c)** The robust SEs are substantially larger than OLS SEs (income SE: 1670 vs 1200, a 39% increase; household size: 3200 vs 2500, a 28% increase). This is strong evidence of **heteroskedasticity**: the OLS SEs understate the true sampling variability, making OLS t-tests too liberal (over-rejecting). In house price data, this is common — variance in prices tends to be higher for higher-income households (greater dispersion in luxury spending). Reports should use robust SEs; WLS could improve efficiency if the form of heteroskedasticity can be modelled.
