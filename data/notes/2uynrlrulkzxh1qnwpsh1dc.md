### **Kali et al., 2009**

This paper applies the product space techniques from [[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]]. They use a firm-level agent decision model to simulate moving to new products in the Product Space and conclude that the product space of a nation must exhibit "small-world" properties before it can exhibit high levels of growth.

***

## Literature review

- Relationship between trade and economic growth has, until recently, been undisputed (World Bank, IMF, OECD, Krueger 1998, Stiglitz 1998, Fischer 2000, Dollar 1992, Sachs and Warner 1995, Ben-David 1993, Frankel and Romer 1999)
- However, there has been some controversy in recent studies (Rodriguez and Rodrik 2000, Harrison and Hanson 1999)
    - Waczairg and Welch 2008 now caution against a one-size-fits-all approach for all countries despite confirming a generally positive relationship between openness and GDP growth
- Following Hausman and Bailey 2007 and Hidalgo et al. 2007 [[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]], this paper uses a network analysis of the Product Space to discover patterns in country production before growth acceleration
- "Small world" property of networks seems to be optimal (Watts and Strogatz 1998) - path length grows logarithmically vs. number of nodes
    - **Hypothesis/conjecture**: before experiencing high levels of growth/growth acceleration, a country's product space needs to exhibit the small-world property
    - Why?
        - Short path lengths due to small-world allow for easier leaps to higher-value products in product space
    
## Methods

1. Evolution of topology of product space over time, 1965-2000
2. Analysis of country-level product space; derivation of spillover effects and distance; formalization of small-world theory
3. Multivariate regressions to confirm small-world theory

- Past results on Product Space:  
    - Hidalgo et al. 2007 identify high heterogeneity in product space: some parts are dense while others are sparse
    - Poor countries have difficulty in traversing product space because their production lies in the periphery (which is sparse)
    - Growth accelerations, identified in Hausman 2005: not correlated with determinants like economic reform or political change, but fairly frequent (60 out of 110 countries had growth acceleration from 1957 to 1992)

### Product space

See [[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]], with the following additions:
- The **country-level product specialization** is the subset of the product space produced by a country (i.e. the comparative advantage of the country)
- Small-world properties arise in many networks in nature, e.g. US power grid, scientific collaborations, earthworm neural network; considered an "optimal" topology for successful networks
- Product space may move to small-world configuration before faster growth

### Small-world model

- At time $t$, a country has RCA in products $R = \{y_1, ..., y_n\}$
    - Each product faces a corresponding world price $p_{y_i}$
    - Cost of production affected by **positive spillovers**: if country produces other products similar to product $i$, then there is less cost due to economies of scale
    - Suppose that this is captured by a cost function $c_{y_i} = c(\sum \phi_{ij})$ where $\sum\phi_{ij}$ is the proximity of all other products the country produces to $i$. 
    - Assume $c' > 0$ and $c'' > 0$, and that $c(0)$ is some average cost $\bar{c}$.
- A graph is formed from the pairwise proximities of products produced by the country
    - Leaping to a new product in the Product Space can be modeled with the following three-period firm-based model:
1. Period 1: initial period of product. Firm cannot choose to make a leap. Cost of production is $p_{y_i} - c(y_i)$.
2. Period 2: Suppose that the cost of moving 1 unit on the Product Space is $\theta$ and that the nearest product on the product space is a distance $d$ away. The firm needs to makes enough profit in Period 1 to traverse the cost $d\theta$:
$$
p_{y_i} - c_{y_i} \geq d\theta.
$$
If the firm transitions to product $k$, there will be positive spillover effects associated with this transition. However, the positive spillover effects that come from this new product will not be immediately evident, so the cost is simply $p_{y_k} - \bar{c}$.

3. Period 3: The spillover effects from period 2 appear. New costs are $p_{y_k} - c(y_k)$.

This leads to three scenarios:
1. The firm does not move to a new product in period 2. Total profit is $\Pi(I) = 3(p_{y_i} - c(y_i))$ across three periods. This is "stagnation".
2. The firm moves to a product in period 2 but moves back to old product in period 3. Total profit is $\Pi(II) = 2(p_{y_i} - c_{y_i}) + p_{y_k} - \bar{c}$. This is "slow growth".
3. Firm moves to new product in period 2 and stays there in period 3. Total profit is $\Pi(III) = p_{y_i} - c_{y_i} + 2(p_{y_k}) - \bar{c} - c_{y_k}$. This is "growth acceleration".

The **leap incentive** is the function
$$
\Pi(III) - \Pi(I) = 2(p_{y_k} - p(y_i)) + 2c_{y_i} - \bar{c} - c_{y_i}- c_{y_k}
$$
i.e. the additional profit to be gained from growth acceleration; additionally, we have $p_{y_i} - c_{y_i} \geq \theta d$, known as "leap feasibility".

If current spillovers increase, meaning that the cost $c_{y_i}$ decreases, the leap incentive decreases but leap feasibility increases. Leap feasibility is a supply-side condition; leap incentive is demand-side. The size of the region satisfying the leap incentive and leap feasibility is the probability that growth acceleration will occur.

This leads to the following propositions:
- If the product is in a sparse region of the Product Space, leap feasibility is low.
- If the product is in a dense region of the product space, leap incentive is high while leap feasibility is also high.

## Results

### Evolution of product space, 1965-2000

- Look at correlation coefficient for proximities of products thorugh time
    - 1962 to 1970: correlation 0.9
    - 1970 onwards: 15 years apart - correlation below 0.5
    - Community structure algorithm (QCUT) and Jaccard index (compares two sets $S_1$ and $S_2$ over time, equals the ratio between intersection of $S_1$ and S_2$ and union of $S_1$ and $S_2$) suggests that:
        - Manufactured cluster growing
        - Overlaps with chemicals and machinery increasing


### Network measures of spillover and distance

- Product centrality, defined as $\frac{\sum_{j}^J \phi_{ij}}{J}$ for product $i$ - avg of proximity to all other products in Product Space
- Nation centrality, i.e. product centrality weighted by exports

