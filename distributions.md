# Distributions

Most relevant columns for the cheatsheet are

- pdf/pmf
- cdf
- $\mu$, $\sigma^2$

The other columns are mostly for understanding.

---

| Distribution                                | pdf / pmf                                                        | cdf                                              | $\mu$, $\sigma^2$                     | cf                                     | MLE                                                                             | Notes                   |
|---------------------------------------------|------------------------------------------------------------------|--------------------------------------------------|---------------------------------------|----------------------------------------|---------------------------------------------------------------------------------|-------------------------|
| $\mathcal{N}(\mu,\sigma^2)$ on $\mathbb{R}$ | $\frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ | $\Phi\left( \frac{x - \mu}{\sigma} \right)$      | $\mu$, $\sigma^2$                     | $e^{i\mu t - \frac{1}{2}\sigma^2 t^2}$ | $\hat{\mu} = \bar{X}_n$, $\hat{\sigma}^2 = \frac{1}{n} \sum(X_i - \bar{X}_n)^2$ | CLT, test stats         |
| Unif($a,b$) on $[a,b]$                      | $\frac{1}{b-a}$                                                  | $\frac{x - a}{b - a}$                            | $\frac{a+b}{2}$, $\frac{(b-a)^2}{12}$ | $\frac{e^{itb} - e^{ita}}{it(b-a)}$    | $\hat{\theta} = \max(X_i)$ (Unif$(0,\theta)$)                                   | Equal probs in interval |
| Exp($\lambda$) on $\mathbb{R}_{>0}$         | $\lambda e^{-\lambda x}$                                         | $1 - e^{-\lambda x}$                             | $1/\lambda$, $1/\lambda^2$            | $\frac{\lambda}{\lambda - it}$         | $\hat{\lambda} = 1/\bar{X}_n$                                                   | Waiting time            |
| Bin($n,p$) on $\{0,\dots,n\}$               | $\binom{n}{k}p^k(1-p)^{n-k}$                                     | $\sum_{i=0}^k \binom{n}{i} p^i(1-p)^{n-i}$       | $np$, $np(1-p)$                       | $(1 - p + p e^{it})^n$                 | $\hat{p} = \frac{1}{n} \sum X_i$                                                | # of successes          |
| Poi($\lambda$) on $\mathbb{N}_0$            | $\frac{e^{-\lambda} \lambda^k}{k!}$                              | $\sum_{i=0}^k \frac{e^{-\lambda} \lambda^i}{i!}$ | $\lambda$, $\lambda$                  | $e^{\lambda(e^{it} - 1)}$              | $\hat{\lambda} = \bar{X}_n$                                                     | Rare events             |
| Ber($p$) on $\{0,1\}$                       | $p^x(1-p)^{1-x}$                                                 | $\frac{x-a}{b-a}$ if $0 \leq x < 1$              | $p$, $p(1 - p)$                       | $(1 - p) + pe^{it}$                    | $\hat{p} = \bar{X}_n$                                                           | Bin($n=1$)              |
| Geo($p$) on $\mathbb{N}_{>0}$               | $(1-p)^{k-1}p$                                                   | $1 - (1 - p)^k$                                  | $1/p$, $\frac{1-p}{p^2}$              | $\frac{pe^{it}}{1 - (1 - p)e^{it}}$    | $\hat{p} = 1/\bar{X}_n$                                                         | Trials until success    |
| $\Gamma(\alpha,\beta)$ on $\mathbb{R}_{>0}$ | $\frac{\beta^\alpha}{\Gamma(\alpha)}x^{\alpha-1}e^{-\beta x}$    | —                                                | $\alpha/\beta$, $\alpha/\beta^2$      | $(1 - it/\beta)^{-\alpha}$             | —                                                                               | Sum of exponentials     |
