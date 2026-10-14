# Module M09 Quiz: Serial Correlation

*12 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. Many serial correlation questions ask you to state H₀, compute a test statistic, and reach a conclusion.

---

## Question 1

*Lesson L01 · Definition*

Serial correlation (autocorrelation) in time-series errors means:

**Type:** Multiple Choice

- **A)** $\text{Var}(u_t \mid x_t) \neq \sigma^2$ (heteroskedasticity)
- **B)** $\text{Cov}(u_t, u_{t-s}) \neq 0$ for some lag $s \neq 0$
- **C)** $E(u_t \mid x_t) \neq 0$ (endogeneity)
- **D)** Errors are not normally distributed

??? success "Show Answer"
    **Answer: B**

    Serial correlation means past errors predict current errors — shocks persist over time. The most common pattern is **positive AR(1)**: $u_t = \rho u_{t-1} + e_t$ with $\rho > 0$. This means:
    - A positive shock this period → likely positive error next period
    - The error process has "memory"

    Common causes: omitted slowly-changing variables (e.g. technology, preferences), misspecified dynamics (lagged effects of regressors not modelled), or sluggish adjustment in economic processes.

---

## Question 2

*Lesson L01 · Consequences*

With AR(1) serial correlation $u_t = \rho u_{t-1} + e_t$ ($0 < \rho < 1$), OLS is:

**Type:** Multiple Choice

- **A)** Biased and inconsistent — OLS cannot be used
- **B)** Unbiased and consistent (under strict exogeneity), but not BLUE; OLS standard errors are biased — typically understated with positive $\rho$
- **C)** Still BLUE — serial correlation only affects efficiency when $\rho > 0.5$
- **D)** Only a problem when $\rho > 0.9$

??? success "Show Answer"
    **Answer: B**

    Under strict exogeneity (which holds for most static time-series models), OLS is **unbiased** — serial correlation in $u$ doesn't mean $E(u_t \mid x_t) \neq 0$.

    However: Gauss-Markov requires $\text{Var}(\mathbf{u}) = \sigma^2 I$ (spherical errors). With serial correlation, $\text{Var}(\mathbf{u}) \neq \sigma^2 I$ → OLS is **not BLUE** (GLS is more efficient). The OLS variance formula $\hat{\text{Var}}(\hat{\beta}) = \hat{\sigma}^2 (X'X)^{-1}$ is **wrong** — it typically understates the true variance with positive $\rho$, making $t$-statistics too large and inference too liberal.

---

## Question 3

*Lesson L02 · Durbin-Watson*

The Durbin-Watson statistic is $DW \approx 2(1 - \hat{\rho})$ where $\hat{\rho}$ is the first-order autocorrelation of residuals. If $DW = 0.6$, what does this imply?

**Type:** Calculation

??? success "Show Answer"
    $$\hat{\rho} \approx 1 - DW/2 = 1 - 0.6/2 = 1 - 0.3 = \mathbf{0.7}$$

    $\hat{\rho} = 0.7$ indicates **strong positive serial correlation** — each error predicts 70% of the next error. $DW = 0.6 \ll 2$ is well below the "no autocorrelation" value of 2.

    DW ranges:
    - $DW \approx 2$: no serial correlation ($\hat{\rho} \approx 0$) ✓
    - $DW \approx 0$: strong positive serial correlation ($\hat{\rho} \approx 1$) ✗
    - $DW \approx 4$: strong negative serial correlation ($\hat{\rho} \approx -1$) ✗

---

## Question 4

*Lesson L02 · DW Limitations*

The Durbin-Watson test is invalid when:

**Type:** Multiple Choice

- **A)** The sample size exceeds 100
- **B)** A lagged dependent variable $y_{t-1}$ appears as a regressor
- **C)** The regressors are trending
- **D)** The errors are heteroskedastic

??? success "Show Answer"
    **Answer: B**

    The DW test assumes that regressors are strictly exogenous. When $y_{t-1}$ is a regressor, it is correlated with $u_{t-1}$ by construction (since $y_{t-1}$ depends on $u_{t-1}$). This violates strict exogeneity and biases the DW test — it tends to be biased toward 2 (appearing to find no autocorrelation even when it exists).

    **Alternative:** Use the **Breusch-Godfrey (BG) LM test**, which is valid with lagged dependent variables and can test for higher-order serial correlation ($p$ lags).

---

## Question 5

*Lesson L02 · Breusch-Godfrey Test*

**[Short Answer]** Describe the Breusch-Godfrey test procedure for AR($p$) serial correlation.

**Type:** Short Answer

??? success "Show Answer"
    **Steps:**

    1. Estimate the original regression by OLS; obtain residuals $\hat{u}_t$
    2. Regress $\hat{u}_t$ on the original regressors $\mathbf{x}_t$ **and** $p$ lagged residuals $\hat{u}_{t-1}, \hat{u}_{t-2}, \ldots, \hat{u}_{t-p}$
    3. Compute LM statistic: $LM = (n-p) \cdot R^2_{\text{aux}} \sim \chi^2_p$ under $H_0$
    4. Reject $H_0$: $\rho_1 = \rho_2 = \cdots = \rho_p = 0$ if $LM > \chi^2_{p,\alpha}$

    **Advantages over DW:**
    - Valid when lagged $y$ appears as a regressor
    - Tests for any order $p$ of serial correlation
    - Based on standard asymptotic chi-squared distribution (no special tables needed)

---

## Question 6

*Lesson L02 · BG Test — Calculation*

**[Calculation]** You run the BG test with $p = 2$ lags. The auxiliary regression of $\hat{u}_t$ on $x_t$, $\hat{u}_{t-1}$, $\hat{u}_{t-2}$ gives $R^2 = 0.12$ with $n = 100$ observations. Test at the 5% level. $\chi^2_{2, 0.05} = 5.99$.

**Type:** Calculation

??? success "Show Answer"
    $$LM = (n - p) \cdot R^2 = (100 - 2) \times 0.12 = 98 \times 0.12 = \mathbf{11.76}$$

    Since $LM = 11.76 > \chi^2_{2, 0.05} = 5.99$, **reject $H_0$** at the 5% level. There is significant evidence of serial correlation up to order 2. OLS standard errors are unreliable — use Newey-West (HAC) standard errors or GLS.

---

## Question 7

*Lesson L03 · Newey-West Standard Errors*

Newey-West (HAC) standard errors are valid in the presence of serial correlation. They:

**Type:** Multiple Choice

- **A)** Change the OLS coefficient estimates to remove the serial correlation bias
- **B)** Correct the reported standard errors to be valid asymptotically under serial correlation (and heteroskedasticity), without changing $\hat{\beta}$
- **C)** Are only valid for AR(1) processes
- **D)** Require knowing the order of serial correlation

??? success "Show Answer"
    **Answer: B**

    Newey-West SEs use a **heteroskedasticity and autocorrelation consistent (HAC)** variance estimator that accounts for both serial correlation and heteroskedasticity in the OLS residuals. Like robust SEs for cross-sectional data, they correct the uncertainty estimate but not the point estimates themselves — OLS is still used for $\hat{\beta}$.

    The "bandwidth" parameter determines how many lags of autocovariance are included in the estimator. A common rule of thumb: use $\lfloor 4(n/100)^{2/9} \rfloor$ lags. Valid under weak dependence (not with unit roots).

---

## Question 8

*Lesson L03 · GLS / Quasi-Differencing*

Under AR(1) errors $u_t = \rho u_{t-1} + e_t$, the GLS transformation produces a model with uncorrelated errors. Describe the quasi-differenced model.

**Type:** Short Answer

??? success "Show Answer"
    For the model $y_t = \beta_0 + \beta_1 x_t + u_t$ with $u_t = \rho u_{t-1} + e_t$:

    **Step 1:** Multiply the lagged equation by $\rho$: $\rho y_{t-1} = \rho\beta_0 + \rho\beta_1 x_{t-1} + \rho u_{t-1}$

    **Step 2:** Subtract from the original:
    $$\underbrace{y_t - \rho y_{t-1}}_{\tilde{y}_t} = \beta_0(1-\rho) + \beta_1 \underbrace{(x_t - \rho x_{t-1})}_{\tilde{x}_t} + \underbrace{u_t - \rho u_{t-1}}_{e_t}$$

    The transformed model $\tilde{y}_t = \beta_0(1-\rho) + \beta_1 \tilde{x}_t + e_t$ has i.i.d. errors $e_t$ — OLS on this model is BLUE (GLS estimator).

    **Feasible GLS (FGLS):** Since $\rho$ is unknown, estimate $\hat{\rho}$ from the OLS residuals: $\hat{\rho} = \sum_{t=2}^T \hat{u}_t \hat{u}_{t-1} / \sum_{t=2}^T \hat{u}_{t-1}^2$. Substitute $\hat{\rho}$ and apply the quasi-differencing transformation.

---

## Question 9

*Lesson L03 · Prais-Winsten vs Cochrane-Orcutt*

Prais-Winsten estimation is preferred over Cochrane-Orcutt when:

**Type:** Multiple Choice

- **A)** The sample size is large
- **B)** Efficiency matters for small $n$ — Prais-Winsten retains the first observation (in transformed form) while Cochrane-Orcutt discards it
- **C)** $\rho$ is close to 1 (near unit root)
- **D)** There are multiple lags of serial correlation

??? success "Show Answer"
    **Answer: B**

    Cochrane-Orcutt drops the first observation after quasi-differencing (the transformed $\tilde{y}_1$ requires $y_0$ which is unavailable). Prais-Winsten keeps it using the transformation: $\tilde{y}_1 = \sqrt{1-\rho^2} \cdot y_1$, which is valid under stationarity.

    For large $n$, losing one observation is negligible. For small $n$, Prais-Winsten is more efficient. When $\rho$ is close to 1, both methods struggle — the transformation becomes near-differencing and loses information.

---

## Question 10

*Lesson L01 · Detecting Serial Correlation*

A residual plot of $\hat{u}_t$ against time shows long runs of positive residuals followed by long runs of negative residuals. This pattern suggests:

**Type:** Multiple Choice

- **A)** Heteroskedasticity
- **B)** Positive serial correlation — the sign of errors persists over time
- **C)** Omitted variable bias
- **D)** Negative serial correlation

??? success "Show Answer"
    **Answer: B — Positive serial correlation**

    Long "runs" (many consecutive residuals of the same sign) are the visual signature of positive autocorrelation — each error tends to be followed by an error of the same sign. This is consistent with $\hat{\rho} > 0$ and $DW < 2$.

    **Negative** serial correlation would appear as alternating positive/negative residuals (fast oscillation), corresponding to $\hat{\rho} < 0$ and $DW > 2$.

    **Heteroskedasticity** appears as changing spread (fan pattern), not persistent runs of same-sign residuals.

---

## Question 11

*Lesson L03 · When to Use Each Remedy*

Match each situation to the appropriate remedy for serial correlation.

**Type:** Short Answer

??? success "Show Answer"
    | Situation | Recommended remedy |
    |---|---|
    | Serial correlation present, want valid inference with minimal assumptions | **Newey-West (HAC) standard errors** — valid asymptotically; simple to implement |
    | Serial correlation present, want efficient estimates (BLUE) | **FGLS / Cochrane-Orcutt / Prais-Winsten** — transforms the model for efficiency |
    | Lagged dependent variable in model, suspecting serial correlation | **Breusch-Godfrey test** to detect; then **Newey-West SEs** (GLS won't work cleanly with LDV) |
    | Serial correlation due to stochastic trend (unit root) | **First-difference** the series — removes the integrated component, leaving a stationary model |
    | Serial correlation may be due to omitted lagged variables | **Add FDL terms** ($x_{t-1}$, $x_{t-2}$) — correct the dynamic misspecification |

---

## Question 12

*Lesson L01 · Australian Context*

**[Short Answer]** A researcher regresses Australia's quarterly inflation on the RBA cash rate and gets significant positive serial correlation ($\hat{\rho} = 0.72$, $DW = 0.56$). What are two economic explanations for this serial correlation and what should the researcher do?

**Type:** Short Answer

??? success "Show Answer"
    **Economic explanations:**

    1. **Omitted slowly-changing variables:** Supply-side factors (oil prices, productivity growth, global inflation) change gradually and affect Australian inflation persistently but are not included as regressors. Their effects show up as correlated errors.

    2. **Misspecified dynamics / adaptive expectations:** Inflation expectations are formed adaptively from past inflation, creating persistence. The static model ignores that current inflation depends on past inflation ($\pi_t = f(\pi_{t-1}, \ldots)$), leaving this persistence in the error.

    **What to do:**

    1. **Short-run fix:** Report **Newey-West HAC standard errors** to get valid inference without changing the model
    2. **Better model:** Add lagged inflation $\pi_{t-1}$ as a regressor (or lagged cash rate) to absorb the dynamic effects — if the serial correlation disappears, the dynamic misspecification was the cause
    3. **Test formally:** Run Breusch-Godfrey with $p = 4$ lags (quarterly data, seasonal consideration) before deciding on the remedy
    4. **Check stationarity:** If inflation has a unit root (unusual but possible in high-inflation periods), first-differencing may be needed
