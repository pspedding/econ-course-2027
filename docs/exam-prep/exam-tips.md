# Exam Tips — ECMT5001

!!! tip "How to Use This Guide"
    These tips are based on USYD ECMT5001 past papers (including the 2022 S2 mid-semester) and the structure of Wooldridge's *Introductory Econometrics*. The mid-semester focuses on probability and statistics (M01); the **final exam** covers regression (M02–M10+). Adjust your study emphasis accordingly.

---

## General Exam Strategy

!!! tip "Work shown = marks earned"
    ECMT5001 exams are **entirely written/worked problems** — no multiple choice. Every numerical answer requires full working. Even if your final number is wrong, correct intermediate steps earn partial credit. Never skip steps.

!!! tip "Read units carefully"
    Marks are regularly lost by ignoring variable units. If $y = \ln(\text{wage})$ and $x = \text{educ}$ (years), the coefficient is a **semi-elasticity** (approximately a percentage): "one additional year of education increases wage by $100\hat{\beta}_1$ percent." If you write "increases wage by $\hat{\beta}_1$" you will lose interpretation marks.

!!! tip "Two decimal places as default"
    Past papers expect answers to **2 d.p.** unless stated. Round at the final step — carry full precision through intermediates.

!!! tip "State your assumptions"
    When asked to perform a hypothesis test, always state: (a) $H_0$ and $H_a$, (b) the test statistic and its distribution under $H_0$, (c) the critical value or $p$-value, (d) your conclusion in plain English. Missing any of these costs marks.

---

## Module 01 — Statistics Review

!!! tip "Variance of a linear combination"
    The most common computational error in M01 questions is **forgetting the covariance term**:
    
    $$\text{Var}(aX + bY) = a^2\text{Var}(X) + b^2\text{Var}(Y) + 2ab\,\text{Cov}(X,Y)$$
    
    If a question gives you a correlation $\rho_{XY}$, convert: $\text{Cov}(X,Y) = \rho_{XY}\,\sigma_X\,\sigma_Y$.

!!! tip "Independence vs zero correlation"
    **Zero correlation does not imply independence** (unless both variables are jointly normal). If a question asks whether $X$ and $Y$ are independent, zero covariance is a *necessary* but not *sufficient* condition. Always check whether the question says "jointly normal" before using $\text{Cov} = 0 \Rightarrow$ independent.

!!! tip "Conditional probability traps"
    For events $A$ and $B$: $P(A \mid B) = P(A \cap B) / P(B)$. A common trap is confusing $P(A \mid B)$ with $P(B \mid A)$ (the prosecutor's fallacy). Draw a Venn diagram or probability table to keep track.

!!! warning "Binomial vs Normal approximation"
    For small $n$ or $p$ far from 0.5, use the **exact binomial**. The normal approximation ($np \geq 5$, $n(1-p) \geq 5$) is only used in large-sample proportion tests. Do not use the $z$-test for proportions when $n$ is small.

---

## Module 02 — Simple Regression

!!! tip "Know what each formula gives you"
    There are four key formulas for simple regression: $\hat{\beta}_1$, $\hat{\beta}_0$, $SE(\hat{\beta}_1)$, and $R^2$. You must be able to compute these from raw $\sum x_i^2$, $\sum y_i^2$, $\sum x_iy_i$, $\bar{x}$, $\bar{y}$, and $n$. Practise these by hand — the exam will not give you a regression printout.

!!! tip "Ceteris paribus interpretation"
    The coefficient $\hat{\beta}_1$ measures the effect of a one-unit increase in $x$ on $y$ **holding all else constant**. In simple regression, "all else" is the error term $u$. When asked to interpret a coefficient, always say "holding other factors constant" or "ceteris paribus" — even in simple regression.

!!! warning "Causality vs association"
    OLS estimates an *association*, not necessarily a causal effect. If a question asks "does this regression show that $x$ causes $y$?", the answer requires discussing whether MLR.4 holds — i.e., whether there are omitted variables, reverse causality, or measurement error. Simply reporting $\hat{\beta}_1 \neq 0$ is not sufficient to claim causality.

!!! warning "$R^2$ cannot be compared across different dependent variables"
    If one model uses $y$ and another uses $\ln(y)$, the $R^2$ values are computed against different $SST$s and are **not comparable**. Do not use $R^2$ to pick between a linear and a log-linear model.

---

## Module 03 — Multiple Regression

!!! tip "OVB direction: memorise the table"
    In the exam, you will almost certainly be asked to determine the direction of OVB. Use:
    
    $$\text{Bias} = \beta_2 \cdot \tilde{\delta}_1$$
    
    Same signs of $\beta_2$ and $\tilde{\delta}_1$ → upward bias (overestimate). Opposite signs → downward bias (underestimate). Write out the table if you need it.

!!! tip "BLUE requires MLR.1–MLR.5, not MLR.6"
    A common exam error is stating that MLR.6 (normality) is needed for BLUE. It is **not**. Gauss–Markov requires only MLR.1–MLR.5. MLR.6 is needed for exact finite-sample $t$- and $F$-tests.

!!! tip "$\bar{R}^2$ formula — know both versions"
    You may need to compute $\bar{R}^2$ from either $SSR$ directly or from $R^2$:
    
    $$\bar{R}^2 = 1 - \frac{SSR/(n-k-1)}{SST/(n-1)} = 1 - \frac{n-1}{n-k-1}(1-R^2)$$
    
    Both are equivalent. Choose whichever is easier given the information provided.

!!! warning "Multicollinearity ≠ bias"
    **Multicollinearity does not bias OLS.** It inflates standard errors and makes it hard to detect significance, but $E(\hat{\beta}_j) = \beta_j$ still holds under MLR.1–MLR.4. If an exam question asks "what is the consequence of multicollinearity for OLS estimates?", the answer is *large standard errors and wide confidence intervals*, **not** bias.

!!! danger "Perfect collinearity is catastrophic — imperfect is merely inconvenient"
    Perfect collinearity (MLR.3 violated) means OLS **cannot be computed**. Imperfect collinearity allows OLS but inflates variances. Know the difference and know how to detect each:
    
    - Perfect: redundant variable (dummy trap, exact definitional relationship)
    - Imperfect: VIF $> 10$ (or 5, depending on threshold used)

!!! danger "Adding an endogenous control can make things worse"
    A common mistake is to think that adding any control variable reduces bias. If the control is **itself endogenous** (e.g., job type in a wage regression where job is caused by education), adding it introduces a new bias (the "bad control" problem). Only add controls that you believe are exogenous and belong in the model on theoretical grounds.

---

## Hypothesis Testing — Common Pitfalls

!!! tip "Two-sided vs one-sided tests"
    Always check whether the question specifies a direction for $H_a$. For a one-sided test at 5% significance, the critical value is $t_{0.05}$ (not $t_{0.025}$). Using the wrong critical value is a common exam error.

!!! tip "Degrees of freedom in the $t$-test"
    For OLS with $k$ regressors and $n$ observations, the $t$-statistic has $n - k - 1$ degrees of freedom (not $n - k$ or $n - 1$). In large samples this distinction is minor, but in exams with small $n$, use the correct d.f.

!!! warning "$p$-value and significance"
    A $p$-value is **not** the probability that the null hypothesis is true. It is the probability of observing a test statistic as extreme as the one computed, *assuming the null is true*. Always state the conclusion in terms of "reject $H_0$" or "fail to reject $H_0$" — never "accept $H_0$".

---

## Exam-Day Reminders

!!! tip "Budget your time"
    Past mid-semester: 40 marks in ~50 minutes ≈ 1.25 minutes per mark. If a question is worth 3 marks, spend no more than 4 minutes. Move on and return if stuck.

!!! tip "Formula sheet policy"
    Check the exam instructions — ECMT5001 may provide a formula sheet. If it does, focus your memorisation on **interpretation** and **conceptual** content rather than rote formula recall. If no sheet is provided, the formulas in this document are the priority ones to memorise.

!!! tip "Check dimensionality"
    Before finalising a numerical answer, do a quick dimensional check. If your estimated wage premium is "300 AUD per extra year of education" when the mean wage is 40 AUD/hr, something has gone wrong — check your formula application.

!!! tip "Use economic intuition"
    If you're unsure about the sign of an OVB or the direction of a bias, reason from economics. "Does more of the omitted variable mean higher or lower $y$? Does more of $x_1$ mean more or less of the omitted variable?" Getting the intuition right will guide you to the correct formula application.
