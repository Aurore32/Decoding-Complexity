

### Vidmer et al., 2015

A diffusion algorithm is used to predict the evolution of the multiproduct WTN, using a new measure of WTN fitness and product similarity.

***

## Literature review

- Complex network properties of the WTN first exhibited in [[International Trade Network.Network Analysis.Topology of the World Trade Web]]
- Gravity model fitted to WTN in [[International Trade Network.Modeling + Predicting the WTN.Gravity]] and [[International Trade Network.Clustering.Rich-Club Phenomenon]]
- Product Space in [[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]] + Economic Complexity in Hausmann et al. 2006
- Export predictions done in Hummels and Klenow 2005
- A **recommender system** can be used to predict future exports and exported products ([[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]], Tacchella et al. 2013, "A new measure for countries' fitness and product complexity")
    - Originally used in online systems/social media networks (Lv and Zhou 2011, "Link prediction in complex networks: a survey")
    - Use heat diffusion/mass diffusion model + economic complexity

## Methods

- NBER-UN dataset w/ 65 countries and 770 products
- Matrix construction: if $RCA > 1$ for country $i$ and product $\alpha$, link exists
- $i,j$ denote countries, $\alpha,\beta$ products
- Links added from year $t$ to $t+1$ is $C^t \backslash C^{t+1}$

### Product space metrics

- **Proximity** between two products $\phi_{\alpha\beta}$ defined as
$$
\min (P(\alpha \in C_i | \beta \in C_i), P(\beta \in C_i | \alpha \in C_i))
$$
- Proximity of country $i$ to product $\alpha$ =
$$
\frac{1}{k_i}\sum_{\beta \in C_i}\phi_{\beta \alpha}
$$
where $k_i$ is out-degree of $i$.

- **Causality** (newly defined) between $\alpha$ and $\beta$ defined as
$$
\frac{\text{number of times $\alpha$ and $\beta$ were in the same country's export basket}}{\text{total number of export baskets}}
$$
during a time period $t$.
- Fitness and product complexity, defined iteratively.

### Diffusion algorithm

- Let $f$ be the vector containing the RCA information of country $i$ at time $t$: 
$$
f = \begin{bmatrix}
a_{i1} \\
a_{i2} \\
\vdots \\
a_{iM}
\end{bmatrix}
$$
where there are $M$ products and $a_{i\alpha}$ is $1$ if $RCA_{i\alpha} > 1$, $0$ otherwise.

- The diffusion algorithm modifies $f$ based on
$$
f_{new} = Wf
$$
where $W$ is the product-to-product matrix with elements
$$
W_{\alpha \beta} = \frac{1}{k_{\alpha}^\lambda k_{\beta}^{1-\lambda}}\sum_{j=1}^N \frac{a_{j \alpha} a _{j \beta}}{k_j}
$$
which can be interpreted as "all countries who export both $\alpha$ and $\beta$ ($a_{j\alpha} a_{j\beta}$) give their resources evenly to all other countries".
- Further multiply each $f_{i\alpha}$ by $\psi_{i\alpha}$, the causality averaged over the export basket of a country towards $i$.

### Link prediction

- Prediction list built with top 20 products predicted by vector $f$ above to exceed $RCA = 1$
- Consider: percentage of predictions that are correct (precision), percentage of actual added links correctly predicted (recall), average complexity rank of predicted products over a country, inter-list Hamming metric $1 - \frac{q_{ij}(L)}{L}$ where $q_{ij}$ is the number of common products in the predicted and actual lists

- Precision $P = 0.3$ for best-performing method (causality + diffusion)

