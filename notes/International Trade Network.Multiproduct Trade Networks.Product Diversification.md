---
id: wb1dpz7av6fr4hht0phsls8
title: Product Diversification
desc: ''
updated: 1741944942303
created: 1741932868996
---


### Desmarchelier et al., 2018

This paper uses an agent-based decision model to simulate nations' movements through the product space and models China's public policy decisions through it.


## Literature review
- Economic development is not binary; countries grow unequally, with convergence clubs (countries that have similar growth rates; Galor 1996, Phillips and Sul 2009), growth miracles and disasters (Nelson and Pack 1999; Diamond 2011)
- There are multiple equilibrium states for economic development, suggesting a non-convex macroeconomic production function (Romer 1986)
- External shocks and internal factor endowments both affect these equilibria (Azariadis and Stachurski 2005)
- Hidalgo and Hausmann propose the Product Space as an alternative explanation for countries getting stuck in sub-optimal equilibria: their position in the periphery of the Product Space make it difficult to traverse through it
- This integrates network theory methods into economic growth
    - [[International Trade Network.Economic Growth.Networks in Growth]] show that proximity of country's export basket to other products + wellc-onnectedness (small-world property) of basket both increase a country's chance of experiencing growth acceleration
    - Poncet and Waldemar 2013 find that Chinese firms are more productive when well-connected to the productive core
- As such, growth does not happen at random; it happens as a result of diversification into more advanced products, which can be affected by public policy decisions
- This paper uses a dataset from East Asia (11 countries, 4716 products, firm-level, 1995 to 2014)
    - Countries modeled as group of firms making individually optimal decisions
    - East Asia known for export-led growth, e.g. Nelson and Pack 1995 highlight role of export incentives in success of South Korea and Taiwan
    - Rodrik 2006 attributes China's growth to its capacity of exporting goods which are more advanced than China's GDP would suggest
- Model also simulates range of public policies, using China as a case study:
    - Export subsidies over fixed set of targeted products
    - Export subsidies over variable set of products
    - Innovation-enhancing policies

## Methods

### East Asia's product space
- Endogenous growth theory (Romer 1987): diversity of products -> faster GDP growth because increased specialization leads to positive externalities
    - Hidalgo et al. 2007 ([[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]]) develops the notion of proximity to explain this, $\phi_{ij}$ (see link)

- Building the Product Space
    - Visual analysis shows that the Product Space has changed from 1995 to 2014:
        - Clusters are textiles, manufactured products, chemicals and crude materials
        - Crude materials are moving into the periphery
        - Manufactured products form distinct and tight cluster
    - China exhibits unusual position because it produces both textiles (low complexity) and chemical products (sophisticated)
    - China occupies 46% of product space in 2014 vs. 33% in 1995
    - Product connectivity decreasing, statistically significant according to Kolmogorov-Smirnov test; this means that countries are specializing more and more
    - Difference in number of exported products from 11 East Asian countries: large gap in 1995, reduced over time (e.g. Vietnam catches up quickly) but ranking in 1995 is maintained in 2014
    - **Path dependency**: taking a different direction in the product space means different rooutes of development
- Metrics in the product space
    - **Competition** between two countries is measured by overlap in their export basket; lower in 2014 than in 1995 except for Japan, which increases overlap with all other countries -> competition in East Asia decreases over time

### Model of product diversification

- Holland and Miller (1991): economies are complex adaptive systems - 
    - Network of interacting agents
    - Dynamic aggregate behaviors that emerge from individual actions
    - Aggregate behaviors can be described without detail on individual agents
    - Agents self-optimize their payoff/profit/utility/market share
- The export landscape
    - 4716 total products; model runs for 20 timesteps to see the evolution of each product's exports
    - Exports normalized by
    $$
    \Omega_{i, t} = \frac{X_{i, t}}{X_{max}} \times 100
    $$
    where $X_{max}$ is the maximum value of exports for any product during the entire timeframe, deflated via US GDP CPI
    - Descriptive statistics of the export landscape:
        - Mean value increased 2.64 times from 1995 to 2014 - annual growth of 4.9 percent
- Local export landscapes
    - Firms cannot see the entire export landscape, but only the landscape closest to them
    - E.g. if a firm can only see the 5 closest products to its position, it may reach sub-optimal local positions; this is a "rugged landscape" effect
- Initial conditions
    - Each country $k$ is initialized with a number of firms $N_{k,i}$ producing product $i$, given by
    $$
    N_{k,i} = M_{k,i,1995} \times 100
    $$
    where $M$ is the market share of $k$ in product $i$ in the start year 1995. This is further multiplied by 
    $$
    \frac{\Omega_{i,1995}}{\bar{\Omega}_{1995}}
    $$
    i.e. how much $i$ is exported compared to the average; this penalizes products which are not exported often and rewards products which are exported often
- Countries can experience economic growth in two ways:
    - More firms
    - Firms producing higher-quality products, moving through the product space

### Firm exploration

- Firms' decisions to move from one product to another are influenced by competitiveness of the market for the new product, the product proximity, and the shape of the export landscape
- Let:
    - $j$ be the new product firms move to
    - $D$ be the maximum walking distance (top number of closest products firms look at), set at random to an integer between 1 and 5
    - Firms want to maximize their own profits; the desirability of moving to another product $i$ is proportional to its export value $\Omega_i$ and inversely proportional to the level of competition $N_{i}$ at time $t$.
    - Thus, a firm decides between
    $$
    (\frac{\Omega_{i,t}}{N_{i,t-1}})^\alpha
    $$
    where $\alpha$ is a tunable parameter between 0 and 1 for the current product, and
    $$
    (\frac{\Omega_{j,t}}{N_{j,t-1}+1})^\alpha \phi_{ij}
    $$
    for the $D$ closest products to $i$ where the $+1$ originates from there being one more firm after the firm itself joins the market of the new product.

## Results

### Simulation results

- w/ parameter $p$ representing percentage of firms that want to decide based on the above equation, and a value $p = 0.15$ or $p = 0.25$, the model captures the monotonic increase of East Asian export market share from 20% to 34$ from 1995 to 2014
- Model can predict situations like China's export diversification, Korea's rise, Vietnam's stagnation after 2007
- The "quiescence trap" (Hidalgo and Hausmann) refers to when the distance towards reaching a new product is too high, and firms do not change products at all, remaining at their current position in the product space
    - Arises for two reasons in this model: scale difference in number of firms across countries, first-mover advantage where first firm to enter a market reaps the rewards and later firms suffer from increased competition

### Public policies

- Subsidies
    - Fixed subsidies subsidize a list of products in 1999 and remain the same; variable/adaptive subsidies change their list of products every year
    - Products selected based on two criteria:
    1. Four-year (1995-1998) average export market share of country (China) in product lower than world average
    2. Four-year average value/competitiveness ratio ($\Omega/N$) higher than product average