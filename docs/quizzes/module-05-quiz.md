# Module M05 Quiz: Functional Forms & Dummy Variables

*14 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. For interpretation questions, state the units carefully.

---

## Question 1

*Lesson L01 · Log-Log Model*

The regression $\ln(\text{sales}) = 2.1 + 0.7 \cdot \ln(\text{price})$ is estimated. The coefficient $-0.7$ (assuming price has a negative effect) or $0.7$ here represents:

**Type:** Multiple Choice

- **A)** Sales increase by 0.7 units for each \$1 increase in price
- **B)** A 1% increase in price is associated with a 0.7% change in sales — the price elasticity of sales
- **C)** Sales increase by 70% for each unit increase in price
- **D)** The slope of the demand curve

??? success "Show Answer"
    **Answer: B**

    In a **log-log** model $\ln(y) = \beta_0 + \beta_1 \ln(x) + u$, the coefficient $\beta_1$ is the **elasticity** of $y$ with respect to $x$: a 1% increase in $x$ is associated with a $\beta_1$% change in $y$. Here, 0.7 means a 1% increase in price is associated with a 0.7% increase in sales — an inelastic response. If this were a demand function, we'd expect a negative sign ($\beta_1 < 0$).

---

## Question 2

*Lesson L01 · Log-Level Model*

$\ln(\text{wage}) = 1.0 + 0.09 \cdot \text{educ}$. The coefficient 0.09 means:

**Type:** Multiple Choice

- **A)** Each additional year of education raises wages by \$0.09
- **B)** Each additional year of education raises wages by approximately 9%
- **C)** Wages are multiplied by 0.09 per year of education
- **D)** The log of wages increases by 9 units per year of education

??? success "Show Answer"
    **Answer: B**

    In a **log-level** model $\ln(y) = \beta_0 + \beta_1 x$, $\beta_1 \approx$ the proportional change in $y$ per unit change in $x$. So $100 \times 0.09 = 9\%$ wage increase per year of education (approximate, exact: $e^{0.09}-1 \approx 9.4\%$). This approximation works well for small $|\beta_1|$.

---

## Question 3

*Lesson L01 · Level-Log Model*

$\text{wage} = 5 + 2.3 \cdot \ln(\text{experience})$. Interpret the coefficient 2.3.

**Type:** Multiple Choice

- **A)** Wages increase by \$2.30 for each additional year of experience
- **B)** A 1% increase in experience is associated with a \$0.023 increase in wage ($= 2.3/100$)
- **C)** Wages increase by 2.3% for each additional year of experience
- **D)** Experience elasticity of wages is 2.3

??? success "Show Answer"
    **Answer: B**

    In a **level-log** model $y = \beta_0 + \beta_1 \ln(x)$, a 1% increase in $x$ is associated with a $\beta_1/100$ unit change in $y$. So a 1% increase in experience raises wages by $2.3/100 = \$0.023$. Equivalently, a doubling of experience ($\approx 100\%$ increase) raises wages by approximately \$2.30. This functional form captures diminishing returns: each extra year of experience adds less to wages at higher experience levels.

---

## Question 4

*Lesson L01 · Choosing a Functional Form*

You expect wages to increase with experience but at a **decreasing rate** (diminishing returns). Which functional form is most appropriate?

**Type:** Multiple Choice

- **A)** Linear: $\text{wage} = \beta_0 + \beta_1 \text{exper}$
- **B)** Level-log: $\text{wage} = \beta_0 + \beta_1 \ln(\text{exper})$ or quadratic with negative $\beta_2$
- **C)** Log-log: $\ln(\text{wage}) = \beta_0 + \beta_1 \ln(\text{exper})$ with $\beta_1 > 1$
- **D)** Linear with $\beta_1 < 0$

??? success "Show Answer"
    **Answer: B**

    Diminishing returns means the marginal effect of experience decreases as experience grows. Two options work: (1) **Level-log**: $\text{wage} = \beta_0 + \beta_1 \ln(\text{exper})$ — the log transformation compresses large values and naturally produces diminishing returns. (2) **Quadratic**: $\text{wage} = \beta_0 + \beta_1 \text{exper} + \beta_2 \text{exper}^2$ with $\beta_2 < 0$ — creates an inverted-U (wages eventually fall; consistent with retirement/obsolescence). The log-log with $\beta_1 > 1$ would imply *increasing* returns.

---

## Question 5

*Lesson L02 · Quadratic — Turning Point*

**[Calculation]** Estimated model: $\text{wage} = 3 + 0.50 \cdot \text{exper} - 0.01 \cdot \text{exper}^2$. At what years of experience does wage reach its maximum?

**Type:** Calculation

??? success "Show Answer"
    The turning point (maximum) of $y = \beta_0 + \beta_1 x + \beta_2 x^2$ is at:

    $$x^* = -\frac{\hat{\beta}_1}{2\hat{\beta}_2} = -\frac{0.50}{2 \times (-0.01)} = -\frac{0.50}{-0.02} = \mathbf{25 \text{ years}}$$

    Since $\hat{\beta}_2 = -0.01 < 0$, this is a **maximum** (the parabola opens downward). Wages rise for the first 25 years of experience, then fall — consistent with skill obsolescence or physical decline. At $x^* = 25$: wage $= 3 + 0.5(25) - 0.01(625) = 3 + 12.5 - 6.25 = \$9.25$.

---

## Question 6

*Lesson L03 · Dummy Variable Interpretation*

The regression $\ln(\text{wage}) = 1.2 + 0.08 \cdot \text{educ} + 0.15 \cdot \text{female}$. Interpret the female dummy coefficient.

**Type:** Multiple Choice

- **A)** Females earn \$0.15 more per hour than males with the same education
- **B)** Females earn approximately 15% more than males with the same education
- **C)** Females earn approximately 15% less than males with the same education
- **D)** The female dummy has no interpretation without knowing the base wage

??? success "Show Answer"
    **Answer: B** — but note: the sign is *positive* here, so females earn **more**.

    With a log-level dependent variable and a dummy regressor: $100 \times \hat{\beta}_\text{female} = 100 \times 0.15 = 15\%$ wage premium for females relative to males (holding education constant). More precisely: $e^{0.15} - 1 \approx 16.2\%$.

    **Typical finding:** in most wage regressions, the female coefficient is *negative* (gender pay gap). Here the positive sign is unusual — possibly because this dataset controls for certain occupations or industries where women are better represented. Always report the sign carefully.

---

## Question 7

*Lesson L04 · Dummy Variable Trap*

You have 4 education categories (no diploma, high school, some college, college degree). With an intercept, how many dummies can you include?

**Type:** Multiple Choice

- **A)** 4
- **B)** 3
- **C)** 2
- **D)** As many as needed

??? success "Show Answer"
    **Answer: B — 3 dummies**

    Include $k - 1 = 4 - 1 = 3$ dummies, omitting one **base/reference group**. Including all 4 creates perfect multicollinearity (the dummy variable trap): the 4 dummies sum to 1 for every observation, which is a perfect linear combination of the intercept column. The omitted category becomes the baseline — its mean is captured by $\hat{\beta}_0$, and each dummy coefficient measures the mean difference relative to that baseline.

---

## Question 8

*Lesson L03 · Base Group Interpretation*

A regression includes dummies for "high school" ($D_{HS}$), "some college" ($D_{SC}$), "college degree" ($D_{CD}$), with "no diploma" as the omitted base group. Interpret the intercept $\hat{\beta}_0$.

**Type:** Short Answer

??? success "Show Answer"
    The intercept $\hat{\beta}_0$ represents the **estimated mean outcome for the base group** — here, workers with no diploma — when all other continuous regressors are at zero (or their base values if there are no other regressors).

    In a wage regression with only education dummies: $\hat{\beta}_0 = \bar{y}_{no\ diploma}$ (the mean wage for workers with no diploma). Each dummy coefficient $\hat{\beta}_{HS}$, $\hat{\beta}_{SC}$, $\hat{\beta}_{CD}$ measures the mean wage *difference* relative to the no-diploma group. Changing the base group changes the intercept and all dummy coefficients, but not the fit of the model ($R^2$, SSR, etc.).

---

## Question 9

*Lesson L05 · Interaction Terms*

In the model $\ln(\text{wage}) = \beta_0 + \beta_1 \cdot \text{educ} + \beta_2 \cdot \text{female} + \beta_3 \cdot (\text{educ} \times \text{female}) + u$, what does $\beta_3$ represent?

**Type:** Short Answer

??? success "Show Answer"
    $\beta_3$ is the **interaction effect**: the difference in the return to education between females and males.

    - For males ($\text{female} = 0$): marginal effect of education $= \beta_1$
    - For females ($\text{female} = 1$): marginal effect of education $= \beta_1 + \beta_3$

    So $\beta_3 = (\text{return to educ for females}) - (\text{return to educ for males})$.

    If $\beta_3 > 0$: each year of education has a *larger* wage effect for women than men.
    If $\beta_3 < 0$: education raises wages by *less* for women than men.
    If $\beta_3 = 0$: equal returns to education (parallel wage-education profiles).

    Interactions allow slopes to differ by group — a key tool when studying heterogeneous effects.

---

## Question 10

*Lesson L05 · Interaction Calculation*

**[Calculation]** Model: $\ln(\text{wage}) = 1.0 + 0.10 \cdot \text{educ} + 0.20 \cdot \text{female} + 0.03 \cdot (\text{educ} \times \text{female})$. For a **female** worker with **16 years of education**, what is predicted $\ln(\text{wage})$?

**Type:** Calculation

??? success "Show Answer"
    For female = 1, educ = 16:

    $$\ln(\hat{\text{wage}}) = 1.0 + 0.10(16) + 0.20(1) + 0.03(16 \times 1)$$
    $$= 1.0 + 1.60 + 0.20 + 0.48 = \mathbf{3.28}$$

    Predicted wage: $e^{3.28} \approx \$26.58$ per hour.

    For comparison, a **male** with 16 years of education: $\ln(\hat{\text{wage}}) = 1.0 + 1.60 + 0 + 0 = 2.60 \Rightarrow e^{2.60} \approx \$13.46$. The female premium at 16 years of education is $e^{3.28}/e^{2.60} = e^{0.68} \approx 97\%$ — a very large positive gap (unusual in practice).

---

## Question 11

*Lesson L01 · Comparing Models*

Can you compare $R^2$ between the model $\ln(y) = X\beta + u$ and $y = X\beta + u$ to decide which fits better?

**Type:** Multiple Choice

- **A)** Yes — the model with higher $R^2$ always fits better
- **B)** No — $R^2$ from a log-dependent model measures the proportion of variance in $\ln(y)$ explained, while the other measures variance in $y$ — they are not comparable
- **C)** Yes, but only if the sample sizes are equal
- **D)** No, because $R^2$ is undefined for log-linear models

??? success "Show Answer"
    **Answer: B**

    $R^2$ measures the share of variance in the *dependent variable* explained. If the dependent variable is $\ln(y)$ in one model and $y$ in another, the benchmarks differ — you are comparing $\text{Var}(\ln y)$ explained vs $\text{Var}(y)$ explained. These are incomparable quantities.

    To compare models with different dependent variable transformations, use alternative criteria such as comparing actual vs predicted $y$ values (after transforming $\hat{y}$ back from log scale), AIC/BIC, or simply plotting residuals.

---

## Question 12

*Lesson L01 · Log Approximation*

In a log-level model, if $\hat{\beta} = 0.05$, the approximate percentage effect of a one-unit increase in $x$ on $y$ is:

**Type:** Multiple Choice

- **A)** 0.05%
- **B)** 5%
- **C)** 50%
- **D)** $e^{0.05} \approx 105.1\%$

??? success "Show Answer"
    **Answer: B — approximately 5%**

    For the log-level model $\ln(y) = \beta_0 + \beta_1 x$: $\Delta \ln(y) \approx \% \Delta y / 100$. So a one-unit increase in $x$ changes $\ln(y)$ by 0.05, implying approximately $100 \times 0.05 = 5\%$ change in $y$. Exact: $e^{0.05} - 1 = 5.13\%$. The approximation $100\hat{\beta}\%$ works well for $|\hat{\beta}| \lesssim 0.2$.

---

## Question 13

*Lesson L03 · Seasonal Dummies*

A quarterly time-series regression includes dummies $Q1$, $Q2$, $Q3$ with $Q4$ as the base. What does the coefficient on $Q1$ represent?

**Type:** Short Answer

??? success "Show Answer"
    The $Q1$ coefficient represents the **mean difference in the outcome between Q1 and Q4** (the base quarter), holding any other regressors constant.

    For example, if the outcome is electricity demand and $\hat{\beta}_{Q1} = -15$, this means electricity demand in Q1 is on average 15 units lower than in Q4 (all else equal). Q4 is the reference — its seasonal effect is absorbed into the intercept. This is how seasonal adjustment is achieved via regression: the seasonal pattern is estimated and can be "partialled out" if needed.

---

## Question 14

*Lesson L02 · ECMT5001-style*

**[Short Answer]** A wage regression is estimated: $\ln(\text{wage}) = \beta_0 + \beta_1 \text{educ} + \beta_2 \text{exper} + \beta_3 \text{exper}^2 + \beta_4 \text{union} + u$

where union = 1 if union member, 0 otherwise.

(a) Interpret each coefficient $\beta_1, \beta_2, \beta_3, \beta_4$.
(b) What turning point in experience does the quadratic imply? What does this mean?

**Type:** Short Answer

??? success "Show Answer"
    **(a) Interpretations:**

    - $\beta_1$: An additional year of education raises wages by approximately $100\beta_1\%$, holding experience and union membership constant.
    - $\beta_2$: The marginal effect of experience on log-wages when $\text{exper} = 0$; the instantaneous return to the first year of experience ($\approx 100\beta_2\%$). Note: the full marginal effect at experience level $e$ is $\beta_2 + 2\beta_3 e$.
    - $\beta_3$: Captures non-linearity in the experience-wage profile. Expected sign: $\beta_3 < 0$ (diminishing returns — each year of experience adds less as workers age).
    - $\beta_4$: Union members earn approximately $100\beta_4\%$ more than non-union workers with the same education and experience (the union wage premium).

    **(b) Turning point:**

    $$\text{exper}^* = -\frac{\hat{\beta}_2}{2\hat{\beta}_3}$$

    This is the experience level at which wages peak (if $\hat{\beta}_3 < 0$). For example, if $\hat{\beta}_2 = 0.04$ and $\hat{\beta}_3 = -0.0007$, then $\text{exper}^* = 0.04 / (2 \times 0.0007) \approx 28.6$ years. Workers with more than ~29 years of experience see declining log-wages — consistent with the Mincer earnings profile observed in Australian labour force data.
