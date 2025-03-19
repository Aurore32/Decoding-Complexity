## Concentration of control in networks
- <span style="background-color: #12ffd7; color: black;">Model</span>. Generalized concentration model.
    - Suppose a population has $N$ members, each with a wealth $X_i$ ($i=1,2,...,N$)
    - Each $X_i$ is randomly distributed with an arbitrary distribution (e.g. $X_i\sim N(\mu,\sigma^2)$)
    - Denote the total wealth as $X_{tot}=\sum_{i}^{N}X_i$
    - Without loss of generality, sort the population data so that $X_1 > X_2 > ... > X_N$
    - Thus define a **cumulative concentration curve** of the population $(\eta(n), \theta(n))$ such that:
    $$
    \begin{cases}
    \eta(n) = \frac{n}{N} \\
    \theta(n) = \frac{\sum_{i=1}^{n} X_i}{X_{tot}}
    \end{cases}
    $$
    - <span style="background-color: #ffb812; color: black;">Interpretation</span>. $\eta(n)$ is the proportion of the population that the first $n$ people occupy, while $\theta(n)$ is the proportion of the total wealth that the first $n$ people hold.
        - The above defines a Lorenz curve in economics, a measure of wealth inequality
    - This can be generalized to any distribution for $X$, and any variable (e.g. ownership or control)

> Fin!