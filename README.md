# Distributions

| Distribution          | Domain            | pdf/pmf                                                            | cdf                                                                                  | $\mu$           | $\sigma^2$           | cf                                     | mle                                                                              | Comment                              |
|-----------------------|-------------------|--------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------|----------------------|----------------------------------------|----------------------------------------------------------------------------------|--------------------------------------|
| **Bernoulli**         | $\{0, 1\}$        | $p^x (1-p)^{1-x}$                                                  | $\text{0 if } x < 0,\quad 1 - p \text{ if } 0 \le x < 1,\quad 1 \text{ if } x \ge 1$ | $p$             | $p(1 - p)$           | $(1 - p) + pe^{it}$                    | $\hat{p} = \bar{X}_n = \frac{1}{n} \sum X_i$                                     | Special case of Binomial ($n=1$)     |
| **Geometric**         | $\mathbb{N}_{>0}$ | $(1-p)^{k-1}p$                                                     | $1 - (1 - p)^k$                                                                      | $1/p$           | $\frac{1-p}{p^2}$    | $\frac{pe^{it}}{1 - (1 - p)e^{it}}$    | $\hat{p} = \frac{1}{\bar{X}_n}$                                                  | Number of trials until first success |
| **Poisson**           | $\mathbb{N}_0$    | $\frac{e^{-\lambda} \lambda^k}{k!}$                                | $e^{-\lambda} \sum_{i=0}^k \frac{\lambda^i}{i!}$                                     | $\lambda$       | $\lambda$            | $e^{\lambda (e^{it} - 1)}$             | $\hat{\lambda} = \bar{X}_n$                                                      | Model for rare events                |
| **Exponential**       | $\mathbb{R}_{>0}$ | $\lambda e^{-\lambda x}$                                           | $1 - e^{-\lambda x}$                                                                 | $1/\lambda$     | $1/\lambda^2$        | $\frac{\lambda}{\lambda - it}$         | $\hat{\lambda} = \frac{1}{\bar{X}_n}$                                            | Waiting time until first event       |
| **Normal (Gaussian)** | $\mathbb{R}$      | $\frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$ | $\Phi\left( \frac{x - \mu}{\sigma} \right)$                                          | $\mu$           | $\sigma^2$           | $e^{i\mu t - \frac{1}{2}\sigma^2 t^2}$ | $\hat{\mu} = \bar{X}_n$, $\hat{\sigma}^2 = \frac{1}{n} \sum (X_i - \bar{X}_n)^2$ | Most common due to CLT               |
| **Gamma**             | $\mathbb{R}_{>0}$ | $\frac{\beta^\alpha}{\Gamma(\alpha)} x^{\alpha - 1} e^{-\beta x}$  | —                                                                                    | $\alpha/\beta$  | $\alpha/\beta^2$     | $(1 - it/\beta)^{-\alpha}$             | No closed-form                                                                   | Sum of exponentials                  |
| **Binomial**          | $\{0,\dots,n\}$   | $\binom{n}{k} p^k (1-p)^{n-k}$                                     | $\sum_{i=0}^k \binom{n}{i} p^i (1-p)^{n-i}$                                          | $np$            | $np(1 - p)$          | $(1 - p + p e^{it})^n$                 | $\hat{p} = \frac{1}{n} \sum X_i$ (for fixed $n$)                                 | Number of successes in $n$ trials    |
| **Uniform**           | $[a, b]$          | $\frac{1}{b - a}$                                                  | $\frac{x - a}{b - a}$ for $x \in [a,b]$                                              | $\frac{a+b}{2}$ | $\frac{(b-a)^2}{12}$ | $\frac{e^{itb} - e^{ita}}{it(b - a)}$  | $\hat{\theta} = \max\{X_1, ..., X_n\}$ for Unif$(0, \theta)$                     | Equal probability in an interval     |

# Gaussian Tests Overview

Let $X_1, \dots, X_n \sim \mathcal{N}(\mu, \sigma^2)$, significance level $\alpha$:

### 1. One-sided z-test (known $\sigma^2$)

- $H_0$: $\mu \leq \mu_0$,$H_1$: $\mu > \mu_0$
- $Z = \dfrac{\bar{X}_n - \mu_0}{\sigma / \sqrt{n}} \sim \mathcal{N}(0,1)$
- Reject if $Z > z_\alpha$

### 2. Two-sided z-test (known $\sigma^2$)

- $H_0$: $\mu = \mu_0$,$H_1$: $\mu \neq \mu_0$
- Reject if $|Z| > z_{\alpha/2}$

### 3. One-sided t-test (unknown $\sigma^2$)

- $H_0$: $\mu \leq \mu_0$, $H_1$: $\mu > \mu_0$
- $T = \dfrac{\bar{X}_n - \mu_0}{S / \sqrt{n}} \sim t_{n-1}$
- Reject if $T > t_{n-1, \alpha}$

### 4. Two-sided t-test (unknown $\sigma^2$)

- $H_0$: $\mu = \mu_0$,$H_1$: $\mu \neq \mu_0$
- Reject if $|T| > t_{n-1, \alpha/2}$

### 5. One-sided $\chi^2$-test (variance)

- $H_0$: $\sigma^2 \leq \sigma_0^2$,$H_1$: $\sigma^2 > \sigma_0^2$
- $C = \dfrac{(n - 1) S^2}{\sigma_0^2} \sim \chi^2_{n - 1}$
- Reject if $C > \chi^2_{n - 1, \alpha}$

### 6. Two-sided $\chi^2$-test (variance)

- $H_0$: $\sigma^2 = \sigma_0^2$,$H_1$: $\sigma^2 \neq \sigma_0^2$
- Reject if $C < \chi^2_{n - 1, 1 - \alpha/2}$ or $C > \chi^2_{n - 1, \alpha/2}$

### 7. Two-sample t-test (equal variances)

- $H_0$: $\mu_X = \mu_Y$,$H_1$: $\mu_X \neq \mu_Y$
- $T = \dfrac{\bar{X} - \bar{Y}}{S_p \sqrt{1/n_X + 1/n_Y}} \sim t_{n_X + n_Y - 2}$
- $S_p^2 = \dfrac{(n_X - 1) S_X^2 + (n_Y - 1) S_Y^2}{n_X + n_Y - 2}$
- Reject if $|T| > t_{n_X + n_Y - 2, \alpha/2}$
