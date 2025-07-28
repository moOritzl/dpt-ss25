# Test Statistics

- $Z = \frac{\bar{X}_n - \mu_0}{\sigma / \sqrt{n}}$(z-test, known $\sigma^2$)
- $T = \frac{\bar{X}_n - \mu_0}{S / \sqrt{n}}$(t-test, unknown $\sigma^2$)
  with $S^2 = \frac{1}{n - 1} \sum_{i = 1}^n (X_i - \bar{X}_n)^2$
- $C = \frac{(n - 1) S^2}{\sigma_0^2}$($\chi^2$-test for variance)

 ---

| Test Type          | $H_0$                      | $H_1$                      | Reject if                                                                                                           |
|--------------------|----------------------------|----------------------------|---------------------------------------------------------------------------------------------------------------------|
| One-sided z        | $\mu \leq \mu_0$           | $\mu > \mu_0$              | $Z > z_\alpha$                                                                                                      |
| Two-sided z        | $\mu = \mu_0$              | $\mu \neq \mu_0$           | $\|Z                                                                 \| > z_{\alpha/2}$                             |
| One-sided t        | $\mu \leq \mu_0$           | $\mu > \mu_0$              | $T > t_{n-1, \alpha}$                                                                                               |
| Two-sided t        | $\mu = \mu_0$              | $\mu \neq \mu_0$           | $                                                                                       \|T \| > t_{n-1, \alpha/2}$ |
| One-sided $\chi^2$ | $\sigma^2 \leq \sigma_0^2$ | $\sigma^2 > \sigma_0^2$    | $C > \chi^2_{n - 1, \alpha}$                                                                                        |
| Two-sided $\chi^2$ | $\sigma^2 = \sigma_0^2$    | $\sigma^2 \neq \sigma_0^2$ | $C < \chi^2_{n - 1, 1 - \alpha/2}$ or $C > \chi^2_{n - 1, \alpha/2}$                                                |