# Past Exam Questions

Practice with real ECMT5001 and ECMT1020-style exam material. Work each question before revealing the answer.

## ECMT5001 In-Semester Exam (2022 S1)

### Question 1
*[Module: M01 — Random Variables, Normal Distribution, Variance Rules]*

Bob is the proud owner of the restaurant "Hungry Bob." The only product Hungry Bob sells is Bob's burger, which is priced at $10 each. The number of Bob's burgers sold on a day, denoted $N$, follows a normal distribution with mean 400 and standard deviation 50.

**(a)** What is the probability that the daily revenue exceeds $5,000$?

It is known that the total daily cost, denoted $C$, follows a normal distribution with mean $1,000$ and standard deviation $300$. The correlation between $C$ and $N$ is $0.8$. Let $P$ denote total daily profit.

**(b)** Express $P$ in terms of $C$ and $N$.

**(c)** Compute $E(P)$.

**(d)** Compute $Var(P)$.

??? answer "Show Answer"
    **(a)** Daily revenue is $10N$. Revenue exceeds $5,000$ when:

    $$10N > 5000 \Rightarrow N > 500$$

    Standardise:

    $$z = \frac{500 - 400}{50} = 2$$

    Therefore:

    $$P(N > 500) = P(Z > 2) \approx 0.0228$$

    **Answer:** about **2.28%**.

    **(b)** Profit equals revenue minus cost:

    $$P = 10N - C$$

    **(c)** Use linearity of expectation:

    $$E(P) = 10E(N) - E(C) = 10(400) - 1000 = 3000$$

    **Answer:** expected daily profit is **$3,000**.

    **(d)** Use the variance rule:

    $$Var(aX+bY)=a^2Var(X)+b^2Var(Y)+2abCov(X,Y)$$

    Here $P=10N-C$, so:

    $$Var(P)=100Var(N)+Var(C)-20Cov(N,C)$$

    First compute:

    $$Var(N)=50^2=2500,\quad Var(C)=300^2=90000$$

    $$Cov(N,C)=Corr(N,C)\sigma_N\sigma_C=0.8(50)(300)=12000$$

    Therefore:

    $$Var(P)=100(2500)+90000-20(12000)=100000$$

    **Answer:** $Var(P)=100,000$. The standard deviation of profit is $\sqrt{100000}\approx316.23$.

---

### Question 2
*[Module: M01 — Binomial Distribution and Hypothesis Testing]*

The government reported that the infection rate of COVID-19 is $0.2$. Let $Y$ denote the number of people infected with COVID-19 in a random sample of 5 individuals.

**(a)** What is the distribution of $Y$? Name the distribution and specify its parameter(s).

**(b)** Compute $P(Y>1)$.

**(c)** Compute $P(Y>2 \mid Y>1)$.

**(d)** Simon wanted to test whether the true infection rate is higher than $0.2$. He collected a random sample of 100 individuals. It was found that 27 individuals were infected with COVID-19. Carry out a hypothesis test for Simon at the 5 percent significance level. Show all steps.

??? answer "Show Answer"
    **(a)** Each person is infected or not infected, with probability $p=0.2$, across $n=5$ people:

    $$Y \sim Binomial(5,0.2)$$

    **(b)** Use the complement:

    $$P(Y>1)=1-P(Y=0)-P(Y=1)$$

    $$P(Y=0)=0.8^5=0.32768$$

    $$P(Y=1)=\binom{5}{1}(0.2)(0.8)^4=0.40960$$

    $$P(Y>1)=1-0.32768-0.40960=0.26272$$

    **Answer:** $0.2627$.

    **(c)** Conditional probability:

    $$P(Y>2 \mid Y>1)=\frac{P(Y>2)}{P(Y>1)}$$

    Compute:

    $$P(Y=2)=\binom{5}{2}(0.2)^2(0.8)^3=0.20480$$

    $$P(Y>2)=1-0.32768-0.40960-0.20480=0.05792$$

    Therefore:

    $$P(Y>2 \mid Y>1)=\frac{0.05792}{0.26272}=0.2205$$

    **Answer:** about **0.22**.

    **(d)** Let $p$ be the true infection rate.

    $$H_0:p=0.2,\quad H_1:p>0.2$$

    The sample proportion is:

    $$\hat{p}=\frac{27}{100}=0.27$$

    Under $H_0$, use the one-sample proportion test:

    $$z=\frac{\hat{p}-p_0}{\sqrt{p_0(1-p_0)/n}}$$

    $$z=\frac{0.27-0.20}{\sqrt{0.2(0.8)/100}}=\frac{0.07}{0.04}=1.75$$

    For a one-sided 5% test, the critical value is approximately $1.645$.

    Since $1.75>1.645$, reject $H_0$.

    **Conclusion:** there is evidence at the 5% significance level that the true infection rate is higher than 0.2.

---

### Question 3
*[Module: M01 — Discrete Distributions, Moments, Correlation, Independence]*

Carol is a trader for an investment bank on Wall Street. She is studying the tick movement of a blue chip stock. Let $X$ denote the price change, measured in number of ticks. The probability density function of $X$ is:

| $x$ | $f(x)$ |
|---:|---:|
| -2 | 0.02 |
| -1 | 0.08 |
| 0 | 0.80 |
| 1 | 0.08 |
| 2 | 0.02 |

**(a)** Compute:

1. $E(X)$
2. $E(X^2)$
3. $sd(X)$

Let $S$ denote the sign of $X$:

$$
S=
\begin{cases}
-1 & \text{if } X \text{ is negative}\\
0 & \text{if } X=0\\
1 & \text{if } X \text{ is positive}
\end{cases}
$$

Let $|X|$ denote the absolute value of $X$.

**(b)** Compute:

1. $Corr(S,|X|)$
2. $Corr(S,X)$
3. Are $S$ and $|X|$ independent? Why or why not?

??? answer "Show Answer"
    **(a)(i)** By symmetry:

    $$E(X)=(-2)(0.02)+(-1)(0.08)+0(0.80)+1(0.08)+2(0.02)=0$$

    **(a)(ii)**

    $$E(X^2)=4(0.02)+1(0.08)+0+1(0.08)+4(0.02)=0.32$$

    **(a)(iii)** Since $E(X)=0$:

    $$Var(X)=E(X^2)-[E(X)]^2=0.32$$

    $$sd(X)=\sqrt{0.32}=0.5657$$

    **(b)(i)** $S$ indicates direction while $|X|$ indicates size. The distribution is symmetric, so positive and negative signs are equally likely at each non-zero magnitude. Therefore:

    $$Cov(S,|X|)=0$$

    and:

    $$Corr(S,|X|)=0$$

    **(b)(ii)** Because $SX=|X|$:

    $$Cov(S,X)=E(SX)-E(S)E(X)=E(|X|)$$

    $$E(|X|)=2(0.02)+1(0.08)+1(0.08)+2(0.02)=0.24$$

    Also:

    $$Var(S)=E(S^2)=0.02+0.08+0.08+0.02=0.20$$

    $$sd(S)=\sqrt{0.20}=0.4472,\quad sd(X)=\sqrt{0.32}=0.5657$$

    Therefore:

    $$Corr(S,X)=\frac{0.24}{0.4472 \times 0.5657}=0.9487$$

    **(b)(iii)** $S$ and $|X|$ are independent in this symmetric distribution. For example:

    $$P(S=1)=0.10,\quad P(|X|=2)=0.04$$

    $$P(S=1,|X|=2)=P(X=2)=0.02$$

    But:

    $$P(S=1)P(|X|=2)=0.10(0.04)=0.004$$

    This does **not** match $0.02$, so by this check they are **not independent**. The zero correlation in part (b)(i) does not imply independence.

    *(Exam trap: zero correlation is not the same as independence.)*

## Key Exam Formulas (Quick Reference)

| Topic | Formula |
|---|---|
| Expectation | $E(aX+bY)=aE(X)+bE(Y)$ |
| Variance | $Var(aX+bY)=a^2Var(X)+b^2Var(Y)+2abCov(X,Y)$ |
| Covariance | $Cov(X,Y)=E(XY)-E(X)E(Y)$ |
| Correlation | $Corr(X,Y)=\frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}$ |
| Binomial probability | $P(Y=y)=\binom{n}{y}p^y(1-p)^{n-y}$ |
| Proportion test | $z=\frac{\hat{p}-p_0}{\sqrt{p_0(1-p_0)/n}}$ |
| Simple OLS slope | $\hat{\beta}_1=\frac{\sum(x_i-\bar{x})(y_i-\bar{y})}{\sum(x_i-\bar{x})^2}$ |
| Simple OLS intercept | $\hat{\beta}_0=\bar{y}-\hat{\beta}_1\bar{x}$ |
| $R^2$ | $R^2=1-\frac{SSR}{SST}$ |
| Adjusted $R^2$ | $\bar{R}^2=1-\frac{SSR/(n-k-1)}{SST/(n-1)}$ |
| Omitted variable bias | $E(\tilde{\beta}_1)=\beta_1+\beta_2\tilde{\delta}_1$ |
| Robust inference | Use heteroskedasticity-robust SEs for cross-sectional data |
| Serial correlation | For AR(1), $u_t=\rho u_{t-1}+e_t$ |
| IV estimator | $\hat{\beta}^{IV}_1=\frac{Cov(z,y)}{Cov(z,x)}$ |

