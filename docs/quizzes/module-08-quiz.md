# Module M08 Quiz: Time Series — Stationarity, Trends & Distributed Lags

*12 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. Time-series questions often require careful thought about the direction of causality and stationarity.

---

## Question 1

*Lesson L01 · Data Types*

Which feature distinguishes time series data from cross-sectional data?

**Type:** Multiple Choice

- **A)** Time series data always has more observations
- **B)** In time series, observations are ordered by time and serial correlation in errors is a realistic concern; randomness of sampling cannot be assumed
- **C)** Time series data cannot be used for regression
- **D)** Cross-sectional data has more variables

??? success "Show Answer"
    **Answer: B**

    In cross-sectional data, observations are assumed to be independently drawn from a population (random sampling). In time series, each observation follows the previous one chronologically — errors are likely correlated across time (serial correlation), and the random sampling assumption (MLR.2) is replaced by a stationarity/weak dependence assumption. The ordering also means we must be careful about temporal causality (past causes present, not vice versa).

---

## Question 2

*Lesson L01 · Strict vs Weak Exogeneity*

Strict exogeneity requires $E(u_t \mid x_1, x_2, \ldots, x_T) = 0$ for all $t$. This is violated when:

**Type:** Multiple Choice

- **A)** The error has a non-normal distribution
- **B)** A lagged dependent variable $y_{t-1}$ appears as a regressor, or when there is feedback from $y_t$ to future $x_{t+1}$
- **C)** The regressors are correlated with each other
- **D)** The sample size is small

??? success "Show Answer"
    **Answer: B**

    If $y_{t-1}$ is a regressor: $y_{t-1} = \beta_0 + \beta_1 x_{t-1} + u_{t-1}$, so $y_{t-1}$ depends on $u_{t-1}$. But the strict exogeneity condition requires $\text{Cov}(u_{t-1}, x_t) = 0$ for ALL lags/leads — which fails if $x_t$ depends on $y_{t-1}$ through feedback. Similarly, if government policy ($x$) responds to last period's GDP (which contains $u_{t-1}$), strict exogeneity fails. **Contemporaneous exogeneity** $E(u_t \mid x_t) = 0$ is weaker and more plausible.

---

## Question 3

*Lesson L04 · Stationarity*

A weakly stationary time series requires:

**Type:** Multiple Choice

- **A)** $E(y_t) = \mu$ (constant mean), $\text{Var}(y_t) = \sigma^2$ (constant variance), and $\text{Cov}(y_t, y_{t-s})$ depends only on the lag $s$ (not on $t$)
- **B)** All observations are normally distributed
- **C)** No serial correlation: $\text{Cov}(y_t, y_{t-s}) = 0$ for all $s > 0$
- **D)** Constant mean only

??? success "Show Answer"
    **Answer: A**

    Weak (covariance) stationarity requires three conditions:
    1. Constant mean: $E(y_t) = \mu$ for all $t$
    2. Constant variance: $\text{Var}(y_t) = \sigma^2 < \infty$ for all $t$
    3. Autocovariance depends only on lag: $\text{Cov}(y_t, y_{t-s}) = \gamma(s)$ — not on when you are in the series, only on how far apart

    Option C (no serial correlation) is much stronger — white noise has zero autocovariance, but stationary series can have nonzero autocovariance (they just need it to depend only on $s$, not $t$).

---

## Question 4

*Lesson L04 · AR(1) Stationarity*

**[Calculation]** For an AR(1) process $y_t = \rho y_{t-1} + e_t$ with $e_t$ i.i.d., stationarity requires $|\rho| < 1$. If $\rho = 1$ (random walk), what happens to $\text{Var}(y_t)$ as $t \to \infty$?

**Type:** Calculation

??? success "Show Answer"
    For a random walk ($\rho = 1$): $y_t = y_0 + \sum_{s=1}^t e_s$

    $$\text{Var}(y_t) = \sum_{s=1}^t \text{Var}(e_s) = t \cdot \sigma_e^2 \to \infty$$

    The variance grows linearly with time — the series **wanders** without bound and never returns to a fixed mean. This is the defining feature of non-stationarity for a random walk.

    Contrast: for $|\rho| < 1$ (stationary AR(1)):
    $$\text{Var}(y_t) = \frac{\sigma_e^2}{1 - \rho^2} \quad \text{(finite and constant)}$$

---

## Question 5

*Lesson L03 · Spurious Regression*

A researcher regresses non-stationary GDP on non-stationary CO₂ emissions and gets $R^2 = 0.91$, $t = 24.3$ (highly significant). What is the most likely explanation?

**Type:** Short Answer

??? success "Show Answer"
    **Spurious regression.** Both GDP and CO₂ emissions have upward trends (they are non-stationary, likely $I(1)$ — integrated of order 1). When two trending series are regressed on each other, OLS will find a strong statistical relationship even if they are **completely unrelated** (driven by independent random walks with drift).

    The high $R^2$ and large $t$-statistic are artefacts of the shared trend, not a causal link. Standard OLS inference is completely invalid here — $t$-statistics don't follow $t$ distributions with non-stationary variables.

    **Remedies:**
    - Test for a unit root (ADF test)
    - If both are $I(1)$, first-difference both series and re-estimate
    - Or test for cointegration (if they share a common stochastic trend, the error-correction model is appropriate)

---

## Question 6

*Lesson L02 · Static vs FDL Models*

A Finite Distributed Lag (FDL) model $y_t = \alpha + \delta_0 x_t + \delta_1 x_{t-1} + \delta_2 x_{t-2} + u_t$ is preferred over a static model $y_t = \alpha + \delta_0 x_t + u_t$ when:

**Type:** Multiple Choice

- **A)** The sample size is small
- **B)** The effect of $x$ on $y$ takes time to materialise — there are delayed or persistent effects
- **C)** $x$ and $y$ are both stationary
- **D)** Heteroskedasticity is suspected

??? success "Show Answer"
    **Answer: B**

    The FDL captures **dynamic effects**: the impact of a change in $x$ at time $t$ on $y$ at times $t$, $t+1$, $t+2$, etc. Classic examples:
    - Monetary policy: interest rate change affects output with a 12–18 month lag
    - Advertising: spending in one month affects sales across multiple future months

    $\delta_0$ = **impact multiplier** (immediate effect)
    $\delta_0 + \delta_1 + \delta_2$ = **long-run multiplier** (total cumulative effect after 2 periods)

    The static model ($\delta_1 = \delta_2 = 0$) is misspecified if lagged effects exist — OVB results from omitting $x_{t-1}$ and $x_{t-2}$.

---

## Question 7

*Lesson L02 · Long-Run Multiplier*

**[Calculation]** FDL(2) model: $y_t = 1 + 0.4x_t + 0.3x_{t-1} + 0.1x_{t-2} + u_t$. Calculate the impact multiplier, the 1-period dynamic multiplier, and the long-run multiplier.

**Type:** Calculation

??? success "Show Answer"
    - **Impact multiplier** $\delta_0 = \mathbf{0.4}$: a one-unit increase in $x_t$ immediately raises $y_t$ by 0.4, holding all else fixed

    - **1-period dynamic multiplier** $\delta_0 + \delta_1 = 0.4 + 0.3 = \mathbf{0.7}$: the cumulative effect after one additional period

    - **Long-run multiplier** $= \sum_{j=0}^{2} \delta_j = 0.4 + 0.3 + 0.1 = \mathbf{0.8}$: total cumulative effect of a permanent one-unit increase in $x$ on $y$ after 2 periods

    Interpretation: a permanent \$1 increase in advertising spending raises sales by \$0.40 immediately, \$0.70 within one period, and \$0.80 in the long run.

---

## Question 8

*Lesson L04 · Detrending*

A time-series regression of $y_t$ on $x_t$ produces spuriously high $R^2$ because both series trend upward. What are two remedies?

**Type:** Short Answer

??? success "Show Answer"
    **Remedy 1 — Include a time trend $t$:**

    Add $t$ (a linear time index) as a regressor: $y_t = \beta_0 + \beta_1 x_t + \beta_2 t + u_t$. This "detrends" both $y$ and $x$ within the regression — $\hat{\beta}_1$ now measures the relationship after removing common linear trend effects. Works when trends are deterministic (constant slope).

    **Remedy 2 — First-difference:**

    Estimate $\Delta y_t = \beta_1 \Delta x_t + \Delta u_t$ where $\Delta y_t = y_t - y_{t-1}$. Differencing removes a stochastic (random-walk) trend. More appropriate than detrending when the trend is stochastic (unit root present). If $y$ and $x$ are both $I(1)$, $\Delta y$ and $\Delta x$ are $I(0)$ (stationary) and OLS on the differenced model is valid.

---

## Question 9

*Lesson L04 · Unit Root Intuition*

An AR(1) with $\rho = 0.95$ is stationary. An AR(1) with $\rho = 1.00$ is a random walk (non-stationary). In practice, these are hard to distinguish. What test is used?

**Type:** Multiple Choice

- **A)** Breusch-Pagan test
- **B)** Augmented Dickey-Fuller (ADF) test
- **C)** Durbin-Watson test
- **D)** White test

??? success "Show Answer"
    **Answer: B — Augmented Dickey-Fuller (ADF) test**

    The ADF tests $H_0: \rho = 1$ (unit root, non-stationary) vs $H_1: |\rho| < 1$ (stationary). The test statistic does not follow a standard $t$-distribution under $H_0$ — special critical values (Dickey-Fuller critical values) are needed.

    "Augmented" means the regression includes lagged differences $\Delta y_{t-1}, \ldots$ to absorb serial correlation in errors. The ADF is known for **low power** — it often fails to reject $H_0$ even when $\rho$ is close to but below 1. This is why non-stationarity tests should be interpreted carefully alongside graphical inspection.

---

## Question 10

*Lesson L03 · Spurious Regression Detection*

After estimating a time-series regression, which diagnostic would most directly reveal if the results are spurious (due to both variables trending)?

**Type:** Multiple Choice

- **A)** High $R^2$ and significant $t$-statistics (these are signs of spurious regression, not diagnostics for it)
- **B)** Plot residuals over time: if the residuals show strong persistence (slow mean reversion), this suggests the regression is spurious — the residuals themselves look like a random walk
- **C)** Breusch-Pagan test for heteroskedasticity
- **D)** RESET test for functional form

??? success "Show Answer"
    **Answer: B**

    In a valid cointegrating regression, residuals are stationary (mean-reverting). In a spurious regression, the residuals look like a random walk — they drift far from zero and take a long time to return. Visual inspection of the residual plot, together with a unit root test on the residuals (Engle-Granger cointegration test), is the standard diagnostic.

    High $R^2$ and significant $t$-statistics are actually warning signs of spurious regression, not confirmations of a genuine relationship — the counterintuitive opposite of cross-sectional data.

---

## Question 11

*Lesson L01 · Weak Dependence*

OLS is consistent in time series under weak exogeneity and **weak dependence** (rather than the i.i.d. assumption). What does weak dependence require?

**Type:** Short Answer

??? success "Show Answer"
    **Weak dependence** requires that the correlation between $y_t$ and $y_{t-s}$ decays to zero as the lag $s \to \infty$: $\gamma(s) \to 0$ as $s \to \infty$.

    This ensures that distant observations are "nearly independent," allowing a Law of Large Numbers and Central Limit Theorem to apply to time-series data. It is satisfied by:
    - Stationary ARMA processes with $|\rho| < 1$
    - Most stable economic time series with short-lived shocks

    It is **violated** by random walks ($\rho = 1$) — shocks never die out, so observations arbitrarily far apart remain strongly correlated. This is why non-stationary processes require special treatment (differencing, cointegration).

---

## Question 12

*Lesson L02 · FDL Application*

**[Short Answer]** A government spending shock of $\$1$ billion occurs at time $t$. Using the FDL model $\Delta\text{GDP}_t = 0.6\Delta G_t + 0.3\Delta G_{t-1} + 0.1\Delta G_{t-2}$, what is the total multiplier effect on GDP over 3 periods?

**Type:** Short Answer

??? success "Show Answer"
    The Keynesian fiscal multiplier through a distributed-lag model:

    - Period $t$: $\Delta\text{GDP}_t = 0.6 \times 1 = \mathbf{\$0.6B}$
    - Period $t+1$: $\Delta\text{GDP}_{t+1} = 0.3 \times 1 = \mathbf{\$0.3B}$
    - Period $t+2$: $\Delta\text{GDP}_{t+2} = 0.1 \times 1 = \mathbf{\$0.1B}$

    **Total (long-run multiplier) = 0.6 + 0.3 + 0.1 = \$1.0B**

    This is a fiscal multiplier of 1.0 — each dollar of government spending raises GDP by \$1 in total over 3 periods (the effect is fully transmitted but with delays). Note this is below the simple Keynesian multiplier of $k = 1/(1-c)$ because we are not modelling the full income-expenditure dynamics here — just the direct statistical relationship from the FDL.
