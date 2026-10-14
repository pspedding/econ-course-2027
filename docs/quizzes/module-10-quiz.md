# Module M10 Quiz: IV, 2SLS & Causal Inference

*14 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. IV questions require careful economic reasoning, not just algebra.

---

## Question 1

*Lesson L01 · Endogeneity Definition*

A regressor $x$ is endogenous if:

**Type:** Multiple Choice

- **A)** It has many missing values
- **B)** $\text{Cov}(x, u) \neq 0$ — the regressor is correlated with the error term
- **C)** It is correlated with other regressors (multicollinearity)
- **D)** Its distribution is skewed

??? success "Show Answer"
    **Answer: B**

    Endogeneity: $\text{Cov}(x, u) \neq 0$, which means $E(u \mid x) \neq 0$ — SLR.4/MLR.4 is violated. OLS is then **biased and inconsistent**: $\text{plim}(\hat{\beta}_1) \neq \beta_1$ even in infinitely large samples.

    Three sources of endogeneity:
    1. **Omitted variables** correlated with $x$ (most common)
    2. **Measurement error** in $x$ (attenuation bias)
    3. **Simultaneity** — $y$ causes $x$ and $x$ causes $y$

---

## Question 2

*Lesson L01 · Sources of Endogeneity*

A researcher regresses crime rates on police presence. Police are deployed in response to crime. This creates endogeneity because:

**Type:** Multiple Choice

- **A)** Police data is measured with error
- **B)** Simultaneity — crime causes more police AND police (may) reduce crime; the causal direction runs both ways
- **C)** Poverty is an omitted variable
- **D)** Both B and C are valid sources of endogeneity here

??? success "Show Answer"
    **Answer: D — Both B and C**

    Two separate endogeneity problems:

    1. **Simultaneity (B):** High crime → government deploys more police → $\text{Cov}(\text{police}, u_{\text{crime}}) > 0$ → OLS coefficient on police is upward biased (appears that more police = more crime)

    2. **OVB (C):** Poverty increases crime AND is correlated with police deployment (police go to poorer, higher-crime areas) → even in a cross-section without simultaneous causality, omitting poverty biases the police coefficient

    Both require IV or quasi-experimental methods to identify the causal effect of police on crime. Levitt (1997) used electoral cycles (politicians hire more police before elections) as an instrument.

---

## Question 3

*Lesson L02 · IV Estimator*

The IV estimator with a single instrument $z$ is:

**Type:** Multiple Choice

- **A)** $\hat{\beta}_{IV} = \text{Cov}(x,y)/\text{Var}(x)$
- **B)** $\hat{\beta}_{IV} = \text{Cov}(z,y)/\text{Cov}(z,x)$
- **C)** $\hat{\beta}_{IV} = \text{Cov}(z,x)/\text{Cov}(z,y)$
- **D)** $\hat{\beta}_{IV} = \text{Var}(z)/\text{Cov}(z,y)$

??? success "Show Answer"
    **Answer: B**

    $$\hat{\beta}_{IV} = \frac{\text{Cov}(z,y)}{\text{Cov}(z,x)} = \frac{\sum (z_i - \bar{z})(y_i - \bar{y})}{\sum (z_i - \bar{z})(x_i - \bar{x})}$$

    Intuition: $\text{Cov}(z,y)$ captures how much $y$ varies with the instrument; $\text{Cov}(z,x)$ scales this by how much $x$ varies with the instrument. The ratio gives the effect of $x$ on $y$ using only the exogenous (instrument-driven) variation in $x$.

---

## Question 4

*Lesson L02 · Instrument Validity*

A valid instrument $z$ requires two conditions. Which correctly states both?

**Type:** Multiple Choice

- **A)** $\text{Cov}(z,y) \neq 0$ (relevance) and $\text{Cov}(z,x) = 0$ (exclusion)
- **B)** $\text{Cov}(z,x) \neq 0$ (relevance) and $\text{Cov}(z,u) = 0$ (exclusion)
- **C)** $z$ is normally distributed and uncorrelated with $y$
- **D)** $\text{Var}(z) > \text{Var}(x)$ and $z$ is measured without error

??? success "Show Answer"
    **Answer: B**

    1. **Relevance:** $\text{Cov}(z,x) \neq 0$ — the instrument must actually move the endogenous regressor. **Testable** via the first-stage $F$-statistic ($F > 10$ rule of thumb).

    2. **Exclusion restriction:** $\text{Cov}(z,u) = 0$ — the instrument affects $y$ **only through** $x$, not directly. **Untestable** — requires economic reasoning. This is always an assumption, never a fact.

    Note: relevance means $z$ is correlated with $x$ (not $y$ directly); exclusion means $z$ is uncorrelated with $u$ (the error in the structural equation for $y$).

---

## Question 5

*Lesson L02 · Card (1995) Instrument*

Card (1995) uses distance to nearest college as an instrument for years of education in a wage equation. Evaluate the two IV conditions.

**Type:** Short Answer

??? success "Show Answer"
    **Relevance:** Students growing up near a college face lower cost of attendance (time, money, information) → more likely to attend → more years of education. First-stage: regress education on distance-to-college → coefficient should be negative and significant. $F$-statistic typically exceeds 10. ✅ **Reasonably satisfied.**

    **Exclusion restriction:** Distance to college should affect wages **only through education** — not directly. Potential violations:
    - Areas near colleges may have different labour market conditions (higher demand for educated workers, agglomeration effects)
    - Parental characteristics (more educated parents live near colleges) directly affect wages

    Card addresses this partly by adding family background controls. The exclusion restriction is **debated** — it is the standard validity concern for this instrument. ⚠️ **Arguable but widely used.**

---

## Question 6

*Lesson L03 · 2SLS Procedure*

**[Short Answer]** Describe the Two-Stage Least Squares (2SLS) procedure step by step, including what goes into each stage.

**Type:** Short Answer

??? success "Show Answer"
    **Stage 1 — First Stage:**

    Regress the endogenous variable $x$ on the instrument $z$ and all other exogenous controls $\mathbf{w}$:
    $$x_i = \pi_0 + \pi_1 z_i + \pi_2 w_{2i} + \cdots + v_i$$

    Save fitted values $\hat{x}_i = \hat{\pi}_0 + \hat{\pi}_1 z_i + \hat{\pi}_2 w_{2i} + \cdots$

    $\hat{x}_i$ is the exogenous component of $x$ — the part driven by the instrument $z$, which is uncorrelated with $u$ by the exclusion restriction.

    **Stage 2 — Second Stage:**

    Regress $y$ on $\hat{x}$ (the fitted values from Stage 1) and all exogenous controls:
    $$y_i = \beta_0 + \beta_1 \hat{x}_i + \beta_2 w_{2i} + \cdots + u_i$$

    $\hat{\beta}_1$ from Stage 2 is the 2SLS estimate — consistent under valid instruments.

    **Critical warning:** Never compute Stage 2 manually using OLS — the resulting standard errors are wrong (they don't account for Stage 1 uncertainty). Always use software's built-in IV/2SLS estimator (`ivreg` in R, `ivregress` in Stata, `linearmodels.IV2SLS` in Python).

---

## Question 7

*Lesson L04 · Weak Instruments*

**[Calculation]** A first-stage regression of $x$ on instrument $z$ and controls gives $F = 7.2$. Is this a strong or weak instrument?

**Type:** Calculation

??? success "Show Answer"
    $F = 7.2 < 10$ → **Weak instrument** by the Staiger & Stock (1997) rule of thumb.

    With a weak instrument:
    - 2SLS is severely biased (toward the inconsistent OLS estimator)
    - Standard confidence intervals are unreliable (too narrow)
    - IV estimates are very sensitive to small violations of the exclusion restriction

    The $F$-statistic here is the test of $H_0: \pi_1 = 0$ in the first stage. $F < 10$ suggests $z$ moves $x$ only weakly — there is not enough signal in the instrument to identify $\beta_1$ reliably.

    **Remedy:** Find a stronger instrument ($F > 10$), use more instruments, or report weak-instrument-robust confidence intervals (Anderson-Rubin).

---

## Question 8

*Lesson L03 · 2SLS Standard Errors*

If you manually run Stage 2 OLS using $\hat{x}$ from Stage 1, the standard errors reported by the Stage 2 regression are:

**Type:** Multiple Choice

- **A)** Correct — 2SLS standard errors are the same as Stage 2 OLS standard errors
- **B)** Too small — they ignore the sampling uncertainty in $\hat{x}$ from Stage 1 estimation
- **C)** Too large — they overstate the true precision
- **D)** Correct only if the first-stage $F > 10$

??? success "Show Answer"
    **Answer: B — Too small**

    Stage 2 OLS treats $\hat{x}$ as if it were the true (non-estimated) regressor. But $\hat{x}$ has its own sampling uncertainty from Stage 1. The true 2SLS variance formula accounts for this additional source of uncertainty, producing larger standard errors than naive Stage 2 OLS.

    Using wrong SEs leads to over-rejection of $H_0$ (liberal inference). This is why software implements the correct 2SLS variance formula directly — never manually chain two OLS regressions for IV.

---

## Question 9

*Lesson L05 · DiD Estimator*

**[Calculation]** Using Card & Krueger (1992) data: NJ (treated) employment pre = 20.44, post = 21.03; PA (control) employment pre = 23.33, post = 21.17. Calculate $\hat{\beta}_{DD}$ and interpret.

**Type:** Calculation

??? success "Show Answer"
    $$\hat{\beta}_{DD} = (\bar{Y}_{NJ,\text{post}} - \bar{Y}_{NJ,\text{pre}}) - (\bar{Y}_{PA,\text{post}} - \bar{Y}_{PA,\text{pre}})$$

    $$= (21.03 - 20.44) - (21.17 - 23.33) = 0.59 - (-2.16) = \mathbf{2.75}$$

    **Interpretation:** The NJ minimum wage increase was associated with approximately **2.75 more full-time equivalent employees per restaurant** relative to what would have been expected based on PA's trend. Employment in NJ *rose* relative to the PA counterfactual — contrary to the standard competitive model prediction that minimum wages reduce employment.

---

## Question 10

*Lesson L05 · Parallel Trends*

The parallel trends assumption in DiD states:

**Type:** Multiple Choice

- **A)** Treated and control groups must have identical outcomes before treatment
- **B)** In the absence of treatment, the treated group would have followed the same trend as the control group
- **C)** Treatment and control groups must be randomly assigned
- **D)** The treatment effect must be constant across all observations

??? success "Show Answer"
    **Answer: B**

    Parallel trends: $E(Y_{1,t}^{(0)} - Y_{1,t-1}^{(0)}) = E(Y_{0,t} - Y_{0,t-1})$ for all $t$ — the counterfactual trend for the treated group equals the observed trend for the control group.

    Key points:
    - Does **not** require pre-treatment levels to be equal (that's answer A — too strong)
    - Is **untestable** for the post-treatment period (we never observe the treated group without treatment)
    - Can be partially tested using **pre-treatment periods**: if treated and control had parallel trends before treatment, it's more credible they would have continued
    - Groups need not be randomly assigned (DiD is used in observational settings)

---

## Question 11

*Lesson L05 · DiD Regression*

In the DiD regression $y_{it} = \alpha + \gamma D_i^{\text{treat}} + \lambda D_t^{\text{post}} + \beta (D_i^{\text{treat}} \times D_t^{\text{post}}) + \varepsilon_{it}$, what does $\gamma$ represent?

**Type:** Multiple Choice

- **A)** The treatment effect
- **B)** The pre-treatment difference between treated and control groups
- **C)** The time trend in the treated group
- **D)** The post-treatment mean of the control group

??? success "Show Answer"
    **Answer: B**

    $\gamma$ is the coefficient on $D_i^{\text{treat}}$ alone (without the post dummy). It captures the **pre-existing difference** between treated and control groups before treatment occurs — the baseline gap.

    Full interpretation of all coefficients:
    - $\alpha$: control group mean in the pre-period
    - $\gamma$: pre-treatment gap (treated − control, in pre-period)
    - $\lambda$: time trend in the control group (post − pre for controls)
    - $\beta$: **DiD treatment effect** (the interaction term)

---

## Question 12

*Lesson L05 · Pre-Trend Testing*

**[Short Answer]** How would you formally test whether treated and control groups had parallel trends before the treatment?

**Type:** Short Answer

??? success "Show Answer"
    **Method — Leads/Pre-treatment interaction test:**

    1. With multiple pre-treatment periods (say $t = -3, -2, -1, 0$), define interaction terms for each pre-period: $D_i^{\text{treat}} \times \mathbf{1}[t = -2]$, $D_i^{\text{treat}} \times \mathbf{1}[t = -1]$ (using $t = -3$ as the reference period)

    2. Add these interactions to the DiD regression alongside the main treatment interaction

    3. **Test:** $F$-test of joint significance of all pre-period interactions under $H_0$: all pre-period interaction coefficients = 0

    4. If $H_0$ is not rejected (pre-period interactions are small and jointly insignificant): parallel trends held pre-treatment → credible assumption for the post-period

    5. If $H_0$ is rejected (pre-trends are significantly different): the groups were already diverging before treatment → DiD estimate is unreliable; may need to control for group-specific trends or find a better comparison group

    Also useful: **placebo tests** — apply the DiD to a period with no treatment and verify $\hat{\beta}_{DD} \approx 0$.

---

## Question 13

*Lesson L01 · IV vs OLS Consistency*

OLS is inconsistent when $x$ is endogenous. IV is consistent but:

**Type:** Multiple Choice

- **A)** IV is unbiased in finite samples
- **B)** IV is biased in finite samples (especially with weak instruments), but consistent — the bias vanishes as $n \to \infty$
- **C)** IV has lower variance than OLS always
- **D)** IV is only valid when the instrument is binary

??? success "Show Answer"
    **Answer: B**

    IV has a **finite-sample bias** that is proportional to the "weakness" of the instrument and the degree of OVB. With a strong instrument ($F \gg 10$) and large $n$, the finite-sample bias is small and the consistency advantage over OLS dominates.

    Trade-offs:
    - IV is **consistent** (bias → 0 as $n \to \infty$); OLS is not
    - IV has **larger variance** than OLS — using only the $z$-driven variation in $x$ discards information
    - With a weak instrument, IV finite-sample bias can be so large that OLS is actually less biased — a key reason the $F > 10$ rule matters

---

## Question 14

*Lesson L02 · Overidentification*

When you have **more instruments than endogenous variables** (overidentified model), you can test the validity of instruments using the Sargan-Hansen (J) test. The J test:

**Type:** Short Answer

??? success "Show Answer"
    **The J-test (Sargan-Hansen overidentification test):**

    With $k$ instruments and 1 endogenous regressor, you have $k - 1$ overidentifying restrictions — testable restrictions on instrument validity.

    **Procedure:**
    1. Estimate 2SLS; obtain 2SLS residuals $\hat{u}_{IV}$
    2. Regress $\hat{u}_{IV}$ on all instruments $z_1, \ldots, z_k$ and exogenous controls
    3. $J = n \cdot R^2_{\text{aux}} \sim \chi^2_{k-1}$ under $H_0$

    **$H_0$:** All instruments satisfy the exclusion restriction

    **Reject $H_0$:** At least one instrument is correlated with $u$ (invalid)

    **Important caveat:** The J-test tests the instruments **relative to each other**. If ALL instruments are invalid in the same direction, the J-test will not detect it. Passing the J-test is necessary but not sufficient for instrument validity — economic reasoning remains essential.
