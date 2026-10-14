# Module M01 Quiz: Probability & Statistics Review

*18 questions · Graduate (ECMT5001) · MCQ, calculation, short answer*

!!! tip "How to use"
    Attempt each question before clicking **Show Answer**. Write out working for calculations.

---

## Question 1

*Lesson L01 · Summation*

Which summation identity is ALWAYS true?

**Type:** Multiple Choice

- **A)** $\sum_{i=1}^n x_i y_i = \left(\sum_{i=1}^n x_i\right)\left(\sum_{i=1}^n y_i\right)$
- **B)** $\sum_{i=1}^n (x_i - \bar{x}) = 0$
- **C)** $\sum_{i=1}^n c \cdot x_i = c^n \sum_{i=1}^n x_i$
- **D)** $\sum_{i=1}^n x_i^2 = \left(\sum_{i=1}^n x_i\right)^2$

??? success "Show Answer"
    **Answer: B**

    $\sum_{i=1}^n (x_i - \bar{x}) = \sum x_i - n\bar{x} = n\bar{x} - n\bar{x} = 0$. Deviations from the mean sum to zero — a fundamental property underpinning OLS. Option A is wrong: $\sum x_i y_i \neq (\sum x_i)(\sum y_i)$ — products do NOT distribute through sums.

---

## Question 2

*Lesson L01 · Variance*

Why does the sample variance formula divide by $n-1$ rather than $n$?

**Type:** Multiple Choice

- **A)** To make calculations easier
- **B)** Because we lose one degree of freedom estimating $\bar{x}$ — dividing by $n-1$ makes $s^2$ an unbiased estimator of $\sigma^2$
- **C)** Because the formula applies only to samples of size $> 1$
- **D)** Convention — either divisor is equally valid

??? success "Show Answer"
    **Answer: B**

    $E(s^2) = \sigma^2$ only when we divide by $n-1$. We estimate the mean $\bar{x}$ from the data, which consumes one degree of freedom. Using $n$ in the denominator gives a *biased* estimator: $E\!\left(\frac{\sum(x_i-\bar{x})^2}{n}\right) = \frac{n-1}{n}\sigma^2 < \sigma^2$. In econometrics OLS residuals similarly lose $k+1$ degrees of freedom (one per estimated coefficient), so $\hat{\sigma}^2 = \text{SSR}/(n-k-1)$.

---

## Question 3

*Lesson L01 · Descriptive Statistics*

**[Calculation]** For the dataset $\{2, 4, 6, 8, 10\}$, compute:
(a) sample mean $\bar{x}$, (b) sample variance $s^2$, (c) sample standard deviation $s$.

**Type:** Calculation

??? success "Show Answer"
    **(a)** $\bar{x} = (2+4+6+8+10)/5 = 30/5 = \mathbf{6}$

    **(b)** Deviations: $-4, -2, 0, 2, 4$. Squared: $16, 4, 0, 4, 16$. Sum $= 40$.
    $s^2 = 40/(5-1) = \mathbf{10}$

    **(c)** $s = \sqrt{10} \approx \mathbf{3.162}$

---

## Question 4

*Lesson L02 · Probability*

Which statement correctly distinguishes population parameters from sample statistics?

**Type:** Multiple Choice

- **A)** $\mu$ is estimated by $\bar{x}$; $\sigma^2$ is estimated by $s^2 = \sum(x_i-\bar{x})^2/(n-1)$
- **B)** Population parameters are always known; sample statistics are unknown
- **C)** $\bar{x}$ is fixed; $\mu$ is random
- **D)** Population variance uses $n-1$; sample variance uses $n$

??? success "Show Answer"
    **Answer: A**

    Population parameters ($\mu$, $\sigma^2$) are fixed but unknown constants. Sample statistics ($\bar{x}$, $s^2$) are random variables (they vary across samples) used to estimate the parameters. Option D has the divisors backwards — population variance divides by $N$; the *unbiased sample* variance divides by $n-1$.

---

## Question 5

*Lesson L04 · Probability*

The Law of Iterated Expectations states $E[E(Y \mid X)] = E(Y)$. Which interpretation is correct?

**Type:** Multiple Choice

- **A)** The expected value of $Y$ given $X$ equals the unconditional mean only when $X$ and $Y$ are independent
- **B)** To find the unconditional mean of $Y$, you can first compute the conditional mean $E(Y|X)$ for each value of $X$ and then average over $X$ — the result equals $E(Y)$
- **C)** $E(Y|X) = E(Y)$ always
- **D)** The law only applies to normally distributed random variables

??? success "Show Answer"
    **Answer: B**

    The LIE says: $E_X[E(Y|X)] = E(Y)$. You average the conditional expectation over the marginal distribution of $X$. It holds for any joint distribution — not just the independent case. In econometrics it is used constantly: e.g. $E(\hat{\beta}) = E[E(\hat{\beta}|X)] = \beta$ (law of iterated expectations applied to prove unbiasedness conditional on regressors).

---

## Question 6

*Lesson L03 · Normal Distribution*

**[Calculation]** $X \sim N(50, 16)$ (mean 50, variance 16). Find $P(X > 54)$.

**Type:** Calculation

??? success "Show Answer"
    Standardise: $z = (54 - 50)/\sqrt{16} = 4/4 = \mathbf{1.0}$

    $P(X > 54) = P(Z > 1.0) = 1 - \Phi(1.0) = 1 - 0.8413 = \mathbf{0.1587} \approx 15.9\%$

    From standard normal tables: $\Phi(1.0) = 0.8413$.

---

## Question 7

*Lesson L05 · Sampling*

In a population with mean $\mu = 200$ and variance $\sigma^2 = 400$, what is the approximate distribution of the sample mean $\bar{x}$ for $n = 100$?

**Type:** Multiple Choice

- **A)** $N(200, 400)$
- **B)** $N(200, 4)$
- **C)** $N(200, 40)$
- **D)** $t(99)$ distribution

??? success "Show Answer"
    **Answer: B**

    By the Central Limit Theorem, $\bar{x} \sim N(\mu, \sigma^2/n) = N(200, 400/100) = N(200, 4)$. The standard error of the mean is $\sigma/\sqrt{n} = 20/10 = 2$. For large $n$ (here $n=100$), the normal approximation is excellent regardless of the population distribution.

---

## Question 8

*Lesson L06 · Hypothesis Testing*

A Type I error is:

**Type:** Multiple Choice

- **A)** Failing to reject $H_0$ when $H_1$ is true (false negative)
- **B)** Rejecting $H_0$ when $H_0$ is true (false positive)
- **C)** Using the wrong test statistic
- **D)** A computational mistake in calculating the p-value

??? success "Show Answer"
    **Answer: B**

    Type I error = false positive = rejecting a true null. Probability = $\alpha$ (significance level). Type II error = false negative = failing to reject a false null. Probability = $\beta$. Power = $1 - \beta$ = probability of correctly rejecting a false null. In econometrics we typically set $\alpha = 0.05$ or $0.01$, accepting a small probability of false rejection.

---

## Question 9

*Lesson L06 · Hypothesis Testing*

A study finds a coefficient with $p = 0.03$. With significance level $\alpha = 0.05$, the correct conclusion is:

**Type:** Multiple Choice

- **A)** Fail to reject $H_0$ — the result is not significant
- **B)** Reject $H_0$ — the result is statistically significant at the 5% level
- **C)** The effect is practically important
- **D)** $H_0$ is false with probability 97%

??? success "Show Answer"
    **Answer: B**

    Since $p = 0.03 < \alpha = 0.05$, we reject $H_0$. Option C is wrong — statistical significance does not imply practical importance (the effect could be tiny but precisely estimated). Option D is the common "probability that $H_0$ is true" misconception: a p-value is $P(\text{data this extreme} \mid H_0 \text{ true})$, not $P(H_0 \text{ true} \mid \text{data})$.

---

## Question 10

*Lesson L06 · t-Test*

**[Calculation]** A two-tailed t-test yields $t = 2.40$ with $n = 25$ observations and $\alpha = 0.05$. The degrees of freedom are $df = 24$. The critical value $t_{0.025, 24} = 2.064$. Do you reject $H_0$?

**Type:** Calculation

??? success "Show Answer"
    Since $|t| = 2.40 > t_{0.025,24} = 2.064$, **reject $H_0$** at the 5% level (two-tailed).

    Equivalently, the p-value $= 2 \times P(T_{24} > 2.40) \approx 2 \times 0.012 = 0.024 < 0.05$ → reject.

---

## Question 11

*Lesson L04 · Correlation*

**[Calculation]** $\text{Cov}(X,Y) = 12$, $\text{Var}(X) = 9$, $\text{Var}(Y) = 16$. Calculate Pearson's $r$.

**Type:** Calculation

??? success "Show Answer"
    $$r = \frac{\text{Cov}(X,Y)}{\sqrt{\text{Var}(X) \cdot \text{Var}(Y)}} = \frac{12}{\sqrt{9 \times 16}} = \frac{12}{\sqrt{144}} = \frac{12}{12} = \mathbf{1.0}$$

    A correlation of 1.0 indicates a perfect positive linear relationship. In practice $r = 1$ is extreme; any value requires checking for data errors or a mechanical relationship.

---

## Question 12

*Lesson L04 · Correlation*

Ice cream sales and drowning deaths are positively correlated. The correct interpretation is:

**Type:** Short Answer

??? success "Show Answer"
    **Correlation does not imply causation.** Both variables have a common cause: hot weather. In summer, more people buy ice cream AND more people swim (raising drowning risk). The correlation is spurious — driven by the confounding variable (temperature/season), not a causal link. In econometrics, failing to control for confounders leads to omitted variable bias.

---

## Question 13

*Lesson L04 · Covariance*

If $E(XY) = 15$, $E(X) = 3$, $E(Y) = 4$, what is $\text{Cov}(X,Y)$?

**Type:** Multiple Choice

- **A)** $3$
- **B)** $15$
- **C)** $-12$
- **D)** $12$

??? success "Show Answer"
    **Answer: A**

    $\text{Cov}(X,Y) = E(XY) - E(X)E(Y) = 15 - (3)(4) = 15 - 12 = \mathbf{3}$

---

## Question 14

*Lesson L04 · Independence*

If $X$ and $Y$ are statistically independent, then $\text{Cov}(X,Y) = $?

**Type:** Multiple Choice

- **A)** $1$
- **B)** Cannot be determined without more information
- **C)** $0$
- **D)** $E(X) \cdot E(Y)$

??? success "Show Answer"
    **Answer: C**

    Independence implies $E(XY) = E(X)E(Y)$, so $\text{Cov}(X,Y) = E(XY) - E(X)E(Y) = 0$. **Important:** the converse is false — zero covariance does NOT imply independence (only for the normal distribution does zero correlation imply independence).

---

## Question 15

*Lesson L04 · Variance*

**[Calculation]** $a=2$, $b=3$, $\text{Var}(X)=4$, $\text{Var}(Y)=9$, $\text{Cov}(X,Y)=0$. Find $\text{Var}(aX + bY)$.

**Type:** Calculation

??? success "Show Answer"
    $$\text{Var}(aX + bY) = a^2\text{Var}(X) + b^2\text{Var}(Y) + 2ab\,\text{Cov}(X,Y)$$
    $$= (4)(4) + (9)(9) + 2(2)(3)(0) = 16 + 81 + 0 = \mathbf{97}$$

---

## Question 16

*Lesson L02 · Bayes' Rule*

**[Calculation — adapted from MIT 14.32]** A diagnostic test has 95% sensitivity (P(positive | disease) = 0.95) and 90% specificity (P(negative | no disease) = 0.90). Disease prevalence is 1% (P(disease) = 0.01). A patient tests positive. What is the probability they actually have the disease?

**Type:** Calculation

??? success "Show Answer"
    Apply Bayes' Rule: $P(D \mid +) = \dfrac{P(+ \mid D) \cdot P(D)}{P(+)}$

    **Numerator:** $P(+ \mid D) \cdot P(D) = 0.95 \times 0.01 = 0.0095$

    **Denominator:** $P(+) = P(+\mid D)P(D) + P(+\mid \neg D)P(\neg D)$
    $= 0.95 \times 0.01 + 0.10 \times 0.99 = 0.0095 + 0.099 = 0.1085$

    $$P(D \mid +) = \frac{0.0095}{0.1085} \approx \mathbf{0.0876 \approx 8.8\%}$$

    Despite a positive test, only ~8.8% of positive-testers actually have the disease — because the disease is rare. This is the **base rate fallacy**. Low-prevalence diseases produce many false positives even with accurate tests.

---

## Question 17

*Lesson L06 · Hypothesis Testing*

When should you use a one-tailed test instead of a two-tailed test?

**Type:** Short Answer

??? success "Show Answer"
    Use a **one-tailed test** when economic theory gives a clear directional prediction *before* seeing the data — e.g. "education raises wages" (testing $H_1: \beta > 0$) or "a tax increase reduces quantity" ($H_1: \beta < 0$). The one-tailed test has more power to detect an effect in the predicted direction.

    Use a **two-tailed test** when you have no strong prior about the direction — testing $H_1: \beta \neq 0$. This is the default in most econometric applications and is more conservative (harder to reject). **Caution:** choosing one-tailed after seeing a result that's only marginally significant two-tailed is p-hacking.

---

## Question 18

*Lesson L05 · Experimental Design — MIT 14.32 style*

**[Calculation]** An experiment assigns $n_1$ subjects to treatment and $n_0 = n - n_1$ to control. Both groups have variance $\sigma^2$. Show that the variance of the difference in sample means is $\sigma^2\!\left(\frac{1}{n_1} + \frac{1}{n_0}\right)$, and find the proportion $p = n_1/n$ that minimises this variance.

**Type:** Short Answer / Calculation

??? success "Show Answer"
    **Variance of difference:**
    $$\text{Var}(\bar{Y}_1 - \bar{Y}_0) = \frac{\sigma^2}{n_1} + \frac{\sigma^2}{n_0} = \sigma^2\!\left(\frac{1}{n_1} + \frac{1}{n_0}\right) \checkmark$$

    **Minimise over $n_1$:** Let $p = n_1/n$, so $n_1 = pn$ and $n_0 = (1-p)n$.

    $$V(p) = \frac{\sigma^2}{pn} + \frac{\sigma^2}{(1-p)n} = \frac{\sigma^2}{n}\left(\frac{1}{p} + \frac{1}{1-p}\right)$$

    Take derivative and set to zero: $\frac{dV}{dp} = \frac{\sigma^2}{n}\left(-\frac{1}{p^2} + \frac{1}{(1-p)^2}\right) = 0$

    $\Rightarrow (1-p)^2 = p^2 \Rightarrow p = \mathbf{0.5}$

    **Equal allocation** ($n_1 = n_0 = n/2$) minimises the variance of the treatment-control difference. This is the standard recommendation for randomised experiments when costs are equal.