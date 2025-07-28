# Distributions

Most relevant columns for the cheatsheet are
- pdf/pmf
- cdf
- $\mu$
- $\sigma^2$

The other columns are mostly for understanding.

---

| Distribution          | Notation                    | Domain            | pdf/pmf                                                            | cdf                                                        | $\mu$           | $\sigma^2$           | cf                                     | mle                                                                              | Comment                              |
|-----------------------|-----------------------------|-------------------|--------------------------------------------------------------------|------------------------------------------------------------|-----------------|----------------------|----------------------------------------|----------------------------------------------------------------------------------|--------------------------------------|
| **Bernoulli**         | Ber($p$)                    | $\{0, 1\}$        | $p^x (1-p)^{1-x}$                                                  | $0$ if $x < 0$, $1 - p$ if $0 \le x < 1$, $1$ if $x \ge 1$ | $p$             | $p(1 - p)$           | $(1 - p) + pe^{it}$                    | $\hat{p} = \bar{X}_n = \frac{1}{n} \sum X_i$                                     | Special case of Binomial ($n=1$)     |
| **Geometric**         | Geo($p$)                    | $\mathbb{N}_{>0}$ | $(1-p)^{k-1}p$                                                     | $1 - (1 - p)^k$                                            | $1/p$           | $\frac{1-p}{p^2}$    | $\frac{pe^{it}}{1 - (1 - p)e^{it}}$    | $\hat{p} = \frac{1}{\bar{X}_n}$                                                  | Number of trials until first success |
| **Poisson**           | Poi($\lambda$)              | $\mathbb{N}_0$    | $\frac{e^{-\lambda} \lambda^k}{k!}$                                | $e^{-\lambda} \sum_{i=0}^k \frac{\lambda^i}{i!}$           | $\lambda$       | $\lambda$            | $e^{\lambda (e^{it} - 1)}$             | $\hat{\lambda} = \bar{X}_n$                                                      | Model for rare events                |
| **Exponential**       | Exp($\lambda$)              | $\mathbb{R}_{>0}$ | $\lambda e^{-\lambda x}$                                           | $1 - e^{-\lambda x}$                                       | $1/\lambda$     | $1/\lambda^2$        | $\frac{\lambda}{\lambda - it}$         | $\hat{\lambda} = \frac{1}{\bar{X}_n}$                                            | Waiting time until first event       |
| **Normal (Gaussian)** | $\mathcal{N}(\mu,\sigma^2)$ | $\mathbb{R}$      | $\frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$ | $\Phi\left( \frac{x - \mu}{\sigma} \right)$                | $\mu$           | $\sigma^2$           | $e^{i\mu t - \frac{1}{2}\sigma^2 t^2}$ | $\hat{\mu} = \bar{X}_n$, $\hat{\sigma}^2 = \frac{1}{n} \sum (X_i - \bar{X}_n)^2$ | Most common due to CLT               |
| **Gamma**             | $\Gamma(\alpha,\beta)$      | $\mathbb{R}_{>0}$ | $\frac{\beta^\alpha}{\Gamma(\alpha)} x^{\alpha - 1} e^{-\beta x}$  | —                                                          | $\alpha/\beta$  | $\alpha/\beta^2$     | $(1 - it/\beta)^{-\alpha}$             | No closed-form                                                                   | Sum of exponentials                  |
| **Binomial**          | Bin($n, p$)                 | $\{0,\dots,n\}$   | $\binom{n}{k} p^k (1-p)^{n-k}$                                     | $\sum_{i=0}^k \binom{n}{i} p^i (1-p)^{n-i}$                | $np$            | $np(1 - p)$          | $(1 - p + p e^{it})^n$                 | $\hat{p} = \frac{1}{n} \sum X_i$ (for fixed $n$)                                 | Number of successes in $n$ trials    |
| **Uniform**           | Unif($a, b$)                | $[a, b]$          | $\frac{1}{b - a}$                                                  | $\frac{x - a}{b - a}$ for $x \in [a,b]$                    | $\frac{a+b}{2}$ | $\frac{(b-a)^2}{12}$ | $\frac{e^{itb} - e^{ita}}{it(b - a)}$  | $\hat{\theta} = \max\{X_1, ..., X_n\}$ for Unif $(0, \theta)$                    | Equal probability in an interval     |
