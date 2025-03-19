---
id: 5f3h3jfl8evxs2reqsteqrp
title: Fitness-Dependent Topological Properties
desc: ''
updated: 1741854874145
created: 1740547194182
---

### Garlaschelli and Loffredo, 2004

*Also see: **Interplay between topology and dynamics in the World Trade Web**, Garlaschelli et al. 2007; **Structure and evolution of the world
trade network**, Garlaschelli and Loffredo 2005*


This paper (alongside the two papers mentioned above) describes the fitness model and uses it to predict the topological properties of the WTN.

****

## Literature review

- How does the WTN evolve?
    - "Rich get richer"/preferential attachment mechanism: well-connected nodes get further connected
    - "Good get richer" hypothesis: some hidden variable intrinsic to each node, named **fitness**, determines the rate at which nodes form connections

## Methods and results

- GDP per capita and total GDP of a nation is a good candidate for fitness:
$$
x_i = \frac{w_i}{\bar{w}}
$$
where $\bar{w}$ is average world GDP, $x_i$ is fitness of country $i$ and $w_i$ is its total GDP.

- Fitness distributed with inverse power law distribution (probability density $\propto x^{-2}$.)

- Expected topological properties of the WTN can be predicted based on the probability distribution of fitness:
$$
f(x_i, x_j) = \frac{\delta x_i x_j}{1 + \delta x_i x_j}
$$
where $\delta$ is a free parameter, and $f(x_i,x_j)$ denotes the probability that $i$ and $j$ are connected.
- If fitness hypothesis is true, WTN formation depends only on degree (and all the higher-order properties are based off of degree).

- Expected properties are:
    - Number of links, which has expected value $L = \frac{1}{2}\sum_{i,j}^N f(x_i, x_j)$ using fitness
    - Mean degree, which via number of links equals $\bar{k} = \frac{2L}{N}$ -> when the free parameter $\delta = 80N^2$, the mean degree corresponds to the actual mean degree in the WTN
    - Expected degree of each vertex, $\sum_{j\neq i}f(x_i, x_j)$
    - Average nearest neighbor degree, $K_i = \frac{\sum_{j\neq i}\sum_{k \neq j}f(x_i, x_j)f(x_j, x_k)}{N}$
    - Clustering coefficient

### Interplay between GDP and WTN
- A more generalized fitness equation is given by
$$
f(x_i,x_j) = \frac{\alpha x_i x_j}{1 + \beta x_i x_j}
$$
where $\alpha$ and $\beta$ are free parameters fixed via the expected number of links. As there are now two free parameters, we also expect
$$
L_{r} = \sum_{i, j}f(x_i, x_j)f(x_j, x_i) 
$$
i.e. the number of reciprocated links, to match the actual network statistics.

- This yields a good agreement between fitness and WTN, which is surprising as fitness is derived from GDP only and WTN from trade statistics only.

- The effects of the WTN on GDP are derived from the equation
$$
GDP = I + F
$$
where $F$ is some measure of *flow* of trade towards a country $i$; in other words, the GDP of a country $i$ depends on an endogenous factor $I$ and an exogenous (world trade) factor $F$.
- This can be observed via the WTN as a weighted network, which represents trade flows:
    - Binary WTN decides which entries of the weighted WTN is nonzero
    - Nonzero weights of weighted WTN determine GDP
    - GDP determines binary WTN
- An agent evolution model of trade flows:
    - Wealth $w_i$ of the $i$th agent changes dynamically from time $t$ to $t+1$ via
    $$
    w_i(t+1) = w_i(t) + \xi_i(t) + \eta_i(t)w_i(t) + \sum_{j}(J_{ji}(t)w_j(t) - J_{ij}(t)w_i(t))
    $$
    where $\xi$ is an additive noise term, $\eta$ is a multiplicative noise term (both are free parameters), and $J_{ji}$ is the fraction of the wealth of agent $j$ being transferred to $i$, making the sum the net transfer of wealth from other agents to $i$.
    - $\xi$ and $\eta$ are usually taken to be Gaussian variables; commonly $\xi = 0$ and $\eta$ is Gaussian; $J_{ij}(t)$ is taken to be some variable
    $$
    \begin{cases}
    q_{ij}(t)\text{ if link between $i$ and $j$} \\
    0\text{ otherwise}
    \end{cases}
    $$
