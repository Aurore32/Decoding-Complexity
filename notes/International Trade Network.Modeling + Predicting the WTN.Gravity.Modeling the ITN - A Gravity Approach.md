---
id: ri1v3iy7mn3fmyj54o54m0b
title: Modeling the ITN - A Gravity Approach
desc: ''
updated: 1739539860372
created: 1739526110738
---
### Duenas and Fagolio

Using the gravity model of trade fitted on bilateral trade flows, this paper **predicts** links and weights in the WTN and analyzes the properties of the resulting network.

****

## Literature review

- The topology of the WTN is an important topic for several reasons:
    - Trade is an important channel of interaction between countries
    - Trade links are good models for international phenomena such as economic crises
    - Reyes et al. (2010) suggests that country centrality in the ITN is a better measure of economic liberalization than other traditional metrics
- Properties of WTN have been well-studied
    - Complex network -> disassortativity, partners of well-connected countries less interconnected than partners of poorly-connected countries (hierarchical nature)
    - Garlaschelli and Loffredo (2005): these properties are stable over time; casts doubts on globalization in last 30 years
    - Node-degree skewed; countries not evenly participating in trade
- Weighted WTN has also been studied due to some authors believing that a binary approach does not ocmpensate for strength of trade links
    - Fagolio et al. (2008) finds that weighted WTN exhibits different properties than binary
        - Right-skewed strength distribution (a few intense trade connetions; a majority are low-intensity)
    - Size of group controlling half of all world trade has decreased in last 30 years (Bhattacharya et al. 2007)
    - Fagolio et al. (2009) finds that these properties have been stable and highlight interesting regularities:
        - Richest countries are most globally central in WTN; they trade with many partners but only form a few intense connections; these intensely connected countries are also very intensely interconnected (**rich club effect; triangular trade**)

## Methods

- Why is the WTN shaped the way it is?
    - Canonical trade model - gravity model of trade; may be used to predict trade links in the WTN
    - Can be augmented with country-specific variables (population, landlocking, area) and bilateral variables (language barrier, religion, trade agreements)
    - Can be fitted to data using least-squares or two-stage Poisson
    - Achieves high level of success in terms of $R^2$ coefficients
- Paper uses gravity model to predict weighted representation of WTN and compare to observed one, with **static** and **dynamic** approaches
    - **Static approach**: do **not** refit gravity model parameters to data for different years. Fit GM (gravity model) once, then use it to predict all subsequent years.
    - **Dynamic approach**: use time as a variable in GM.
    - Both approaches obtain weighted link predictions for every given year in the WTN
- Findings: GM can predict weights well if told whether a trade link exists; GM does not predict both binary architecture (whether trade exists between two countries) and trade volume well

***

## Methods

- **Dataset**: IMF bilateral trade data. Uses years 1970, 1975, ..., 2000. $w_{ij}(t)$ represents exports from $i$ to $j$ at year $t$ and $N(t)$ represents the number of countries reporting positive trade flow in year $t$.
- Descriptive statistics for dataset:
    - Rising density
    - New trade links increase at a greater than quadratic rate
    - Number of countries controlling half of trade flows remains stable
    - Number of countries controlling 90% of trade has substantially decreased -> concentration
- Definition for associated graphs:

> <span style="background-color: #03cafc; color: black;">Definition</span>. **Observed weighted WTN**: graph with adjacency matrix $W = \{w_{ij}(t)\}$.

> <span style="background-color: #03cafc; color: black;">Definition</span>. **Observed binary WTN**: graph with $A = \{a_{ij}(t)\}$, which is $0$ if trade does not exist between $i$ and $j$ and $1$ otherwise.

Studied in [[International Trade Network.Network Analysis.World Trade Network]].

- Gravity model specifications:
    - Trade flows between two countries proportional to product of GDPs of two countries and inversely proportional to distance between them
    - Consistent with product-by-product trade models like Hecksher-Ohlin ([[International Trade Network.Network Analysis.World Trade Network]])
    - Modern empircal usage includes more variables (see above)
- This paper employs the model

> <span style="background-color: #12ffd7; color: black;">Model</span> (General gravity model).
$$
w_{ij}(t) = \alpha_0 Y_i(t)^{\alpha_1} Y_j(t)^{\alpha_2}d_{ij}^{\alpha_3} X_{ij}(t) D_{ij}(t)Z_{ij}(t)\eta_{ij}(t)
$$
This is a model in several parts. $\alpha_0 Y_i(t)^{\alpha_1} Y_j(t)^{\alpha_2}d_{ij}^{\alpha_3}$ is the standard gravity model, except that the parameters $\alpha_0, \alpha_1, \alpha_2, \alpha_3$ are to be fitted. $X_{ij}(t)$ are $K$ country size variables $X_{i1}, X_{i2},  ..., X_{iK}$:
$$
X_{ij}(t) = \prod_{k=1}^K X_{ik}(t)^{\beta_{1k}} X_{jk}(t)^{\beta_{2k}} 
$$
i.e. the product of all $K$ country size variables for both countries, with parameters $\beta$ to be fitted. Typically we use $K=2$ (two size variables, area and population). 

$D_{ij}(t)$ are $H$ bilateral relationship variables $D_{ij1}, D_{ij2}, ..., D_{ijh}$ with parameter to be fitted $\theta_{1}, \theta_{2}, ..., \theta_h$ (common language, religion, colonial ties etc.):

$$
D_{ij}(t) = e^{\sum_{h=1}^H\theta_h D_{ijh}(t)}
$$

$Z_{ij}(t)$ are $L$ country-specific variables $Z_{i1}, Z_{i2}, ..., Z_{il}$ with parameter to be fitted $\delta$ (landlocking, continents etc.):

$$
Z_{ij}(t) = e^{\sum_{l=1}^L(\delta_{1l} Z_{il}(t) + \delta_{2l}Z_{jl}(t))}
$$

And finally, $\eta$ is an error variable.

> <span style="background-color: #ffb812; color: black;">Remarks</span>. 
1. The above formula does not permit for zero trade flows, which in reality are quite frequent. This makes the GM unsuited for estimating whether a trade relationship exists.

### Estimating gravity model

- Straightforward approach: log-linearizing equation and use least-squares to estimate parameters
    - Problematic due to **bias in zero-valued flows** (relevant to paper)
    - Log-linearizing implies nonzero flows as log does not take $0$ as a value
    - Need to tell model the binary structure $A(t)$
- Can use two-stage Poisson pseudo-maximum likelihood models
    - Stage one: is the trade flow between two countries zero? -> Use logistic regression
    - Stage two: if nonzero, predict trade flow volume
- Approach used: tell model binary structure -> OLS; PPML -> Poisson

## Results

### The predicted WTN

- Statistics studied:
    - Basic weighted statistics (total node strength, ANNS, clustering)
    - Directed weighted statistics (in-degree/strength, out strength)
    - Binary WTN

- Basic weighted statistics:
    - GM near-perfectly matches node strength, but less successful (yet still effective) for ANNS and clustering; 95% precision
    - OLS is more successful for ANNS
        - This is because OLS preserves the existing binary structure, while Poisson predictions don't
        - GM always has a positive value so Poisson predictions assign a full binary network (density = 1), which overestimates the numberr of nodes connected to any given node
        - As such, average nearest neighbor node strength is vastly underestimated because the number of neighbors is overestimated
        - Kolmogorov-Smirnov tests confirm that OLS predictions and original WTN come from the same distribution, but Poisson predictions do not
        - As a result, OLS correctly predicts disassortativity (negative correlation between degree and ANNS) but Poisson does not
        - Both predictions can get in- and out-strength distributions correct
- Binary network statistics:
    - Logistic/softmax model used; outputs $P(\text{trade relationship exists}) \in (0,1)$
    - **Density-induced** prediction: if $P > \gamma =$ density of WTN, then trade relationship exists
    - Bernoulli predictions also used

