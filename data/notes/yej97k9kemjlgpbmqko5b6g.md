### De Benedictis and Tajoli 

A complex-network analysis of three issues in the World Trade Network: the effects of the WTO on trade integration, the value of network indices vs. the gravity model of trade, and the structural difference between intensive and extensive margins of trade.

****

## Methods

### Definition of the WTN

- Paper considers simple binary directed WTN for the most part; some models consider the weight matrix $W$

### Summary network statistics

- In-degree; out-degree
- Clustering coefficient
- **Density** $\gamma = \frac{2\ * \text{ no. of links in graph}}{n(n-1)}$ where $n\choose{2}$ $= \frac{n(n-1)}{2}$ is the maximum possible number of links in a graph with $n$ nodes.
- **Ego-density** is density for a specific sub-graph of the graph.
- Centrality:
    - Degree centrality (in-degree or out-degree divided by $n-1$ for $n$ total nodes)
    - Closeness centrality (geodesic distance) = reciprocal of average distance between node and other nodes
    - Betweenness centrality
- Centralization:

> <span style="background-color: #03cafc; color: black;">Definition</span>. **Centralization metrics** extend centrality metrics to the entire network: in-degree, out-degree, closeness, and betweenness centralization.

- Degree centralization: $C^d = \frac{\sum_{i=1}^n |C^d_i - C^*|}{(n-2)(n-1)}$ for a graph with $n$ nodes, where $C^d_i$ is the degree centrality (either in- or out-degree) of node $i$ and $C^*$ is the maximum degree centrality of a nodee in the graph.

> <span style="background-color: #ffb812; color: black;">Interpretation</span>. For a graph with $n$ nodes, degree centralization is the cumulative difference of the degree centrality of the nodes to the maximum centrality of the graph, divided by the maximum possible centralization score $(n-2)(n-1)$. Essentially, it is the variance of the centrality.
- The minimum degree centralization is zero; this is if all nodes have the same degree. The maximum degree centralization is one; this is if one node has the highest degree and all other nodes have zero degree (e.g. a star).

- Closeness centralization: $C^c = \frac{\sum_{i=1}^n |C^c_i - C^*|}{(n-1)(n-2)/(2n-3)}$ where $C^c_i$ denotes the closeness centrality of node $i$ and the denominator is again the maximum possible value of the numerator.

- Betweenness centralization: $C^b = \sum_{i}^n |C^b_i - C^*|$ as above.

> <span style="background-color: #03cafc; color: black;">Definition</span>. The **intensive margin of trade** refers to changes in a trade link that has already been established; the **extensive margin of trade** refers to the creation of nonexistent trade links.

### Literature review
- Complex network properties of WTN ([[International Trade Network.Network Analysis.Topology of the World Trade Web]])
    - Scale-free degree distribution (inverse power law)
    - Small-world property (distance grows logarithmically with graph size)
    - High clustering coefficient
    - Degree-degree 
- Complex network finding implied that WTN linkages reflect some underlying distribution and are not created randomly

- Kali and Reyes (Trade Structures and Economic Growth) - WTN strongly **hierarchical** (community structures), scale-free, dissortative
- Fagolio et al. ([[International Trade Network.Network Analysis.Topology of the World Trade Web.Fagiolo et al]]) - links weighted by average of exports and imports; disassortative network; large hubs vs. majority of weakly connected countries

## Results

### Extent of changes in the WTN from 1950-2000

- **Dataset**: IMF direction of trade statistics; 1950-2000, bilateral imports (aggregated), deflated by US CPI

    - World trade concentrated in sub-group of countries:
        - In 1950, 20.6% of trade flows made up 90% of trade; in 2000, 7% made up 90% of trade
            - Small trade flows have increased
        - In 1950, the top 1% of trade flows made up 29.25% of trade; in 2000, it made up for 58% of trade
        - Trade more and more top-concentrated over time
    - Correlation between GDP and number of trade partners positive but not strong ($R = 0.55$)
    - Dataset adjustments: kept number of countries constant from 1950-1990 (157). 1990-2000 had 176 countries (new countries created from dissolution of USSR). Missing observations counted as zero.

- Properties of the WTN and changes over time:
    - Rising density: 0.0673 in 1950 to 0.3876 in 2000
        - Still much lower than a complete network (density 1)
    - Reduction in average distance between nodes
    - In-degree closeness centralization rises over time until 1980s then falls
        - Indicates the existence of a core, concentrated group of markets (1980s), then a more diversified import group
    - In-degree centralization larger than out-degree centralization; imports different from exports
    - Decline in betweenness centralization from 1960 to 2000 indicating reduction of hubs
    - Shape of WTN degree distribution changes over time
        - Out-degree: initially left-skewed, bimodal w/ one large peak at the left (small exporters) and one smaller peak at the right (large hubs). Then left peak tends more and more towards center -> large number of average-sized exporters with small number of hubs
        - This indicates that the WTN is divided into a group of small exporters, a group of large hubs, and a continuum of countries in between -> not simply a core-periphery structure
    - WTN is statistically significantly not a complete network, but increases in WTN density are statistically dismissable (level of confidence $p = 0.173$)

### Countries' positions in the WTN

- 1960: US highest out-degree; UK highest in-degree (colonialism)
- 1980: EU rises; UK highest both out- and in-degree; first places all taken by EU countries
- 2000: US first in both degrees; developing countries now rapidly increasing in degrees; SEA rises
- Centrality:
    - EU highest for all centralities in 1960s
    - In-degree and out-degree correlation positive, 0.95 in 2000; increases over time, world no longer divided into "importers" and "exporters", biggest exporters are biggest importers
    - Closeness centrality and betweenness centrality correlated at 0.62 in 2000
    - HK, France, India, Morocco, Switzerland "regional hubs" - i.e. highest beetwenness centrality in region
    
![alt text](image.png)

### Gravity model corroboration

> <span style="background-color: #12ffd7; color: black;">Model</span>. The **gravity model of trade** predicts the following relationship between two countries' GDP, their distance, and the magnitude of their bilateral trade:
$$
L_{ij} = A\frac{GDP_i * GDP_j}{D_{ij}}
$$
> where $A$ is a constant, $L_{ij}$ denotes bilateral trade between $i$ and $j$, and $D_{ij}$ denotes distance between $i$ and $j$.

- Gravity model predicts a complete network (density 1) because distances are not infinite; however, density in 2000 is only 0.5. Why do some pairs of countries not have existing trade links?

> <span style="background-color: #12ffd7; color: black;">Model</span>. **Heckscher-Ohlin model**. According to this model, two countries will have no trade if their products are perfect substitutes: they do not need the products of the other country. Thus we have

$$
L_{ij} = \frac{GDP_i * GDP_j}{GDP_W} (1+\sum_{k} \lambda_k \alpha_{ik}\beta_{jk})
$$

> where $GDP_W$ is world GDP, $k$ are products produced by $i$ and $j$, $\lambda_k$ are weights assigned to the products, and $\alpha_{ik}$ and $\beta_{jk}$ are how much the production of product $k$ by country $i$ (the exporter) deviates from the world average and how much the consumption of product $k$ by country $i$ (the importer) deviates from the world average, reflecting how much $k$ matters to the countries.

E.g. if $\alpha_{ik} = 1$ (100% deviation) and $\beta_{ik} = -1$ (-100% deviation), reflecting a scenario where $i$ is a great producer of $k$ but $j$ is not a consumer of $k$ at all, the summed term is $-1$ and $L_{ij} = 0$.

Essentially, the model states that if $i$ and $j$ have heterogeneous (different) tastes in production and consumption, they will not trade; thus they will have no trade link on the WTN. The increase in links in the WTN reflects a greater homogenization in country preferences.

Another explanation is given by Helpman et al. (2008):
- Some costs are specific to a certain country-country pair
- Fixed costs of exporting; difference in productivity/efficiency between countries
- Some firms are not productive enough to serve every single country in the world
- This theory posits that reductions in trade costs over time (globalization) explains increase in trade links/creation of new trade links

A reduction in global trade costs have different (heterogeneous) effects on countries, according to all above models: 
- Creates new connections via lessening fixed costs of exporting (**extensive margin of trade**)
- Reduces friction between products

### Network analysis contributions to the gravity model

- **Multilateral resistance terms** in the gravity model are terms that represent the transaction costs from country $i$ to $j$, as well as supply costs in $i$ and demand costs in $j$
- Analysis via gravity model doesn't usually include these terms; instead, they are analyzed on a country-to-country basis
- Network analysis of the WTN can replace such terms:
    - In-degree reflects demand costs of $j$, the importer (higher in-degree = $j$ handles imports from more countries = less importing costs)
    - Out-degree reflects supply costs, as above
    - Centralities (e.g. closeness) reflect transaction costs
- Results of regression w/ gravity model and network metrics:
    - Pos. correlation between both in-degree and out-degree centrality and trade flows
    - Distance term in gravity model less important (centrality reflects distance but only partially)
    - Importer GDP reduced significantly in importance -> position of country in WTN reflects trade more than GDP
    - WTO membership parameter becomes statistically indistinguishable from 0 -> position in WTN reflects WTO membership
        - WTO contributes to trade, but not directly; it affects country's position in WTN
    - WTO membership becomes significant when network metrics are removed

### Role of WTO in world trade network
- Subramanian and Wei (2007): WTO promotes trade, strongly but unevenly
- Network analysis can show WTO impact on entire system
- Network constructed from WTO members:
    - Denser than regular WTN
    - Increases in size over time (more countries join WTN)
    - More closely interconnected
    - Higher number of linkages than regular network - lower entry costs to markets? Creates new trade links, e.g. by increasing cost transparency
    - Less centralized (more even in centrality) than WTN
    - Center of WTN are all WTO members by 2000 (with China joining in 2001)

### Regionalization of international trade

- Are there more trade flows between geographically close countries (e.g. in the same continent)?
- Continental subnetworks of trade:
    - Density higher than world density (except Africa)
    - Intra-continent trade flows only 27% of total
    - Density index in continents decline while world increases (e.g. Europe - density decreases from 1980 to 2000), perhaps due to dissolution of USSR
    - The EU has density 1; non-EU countries in Europe are not well-connected
    - Most continents have "central hubs" (e.g. Mexico, the US and Canada for the Americas)

### Extensive and intensive margins of trade
- Felbermayr and Kohler (2005): 60% of world trade growth from 1950 to 1997 has been in the intensive margin (not newly created trade links)
- Lawless (2008): for gravity models, country-country indices like language, geography, infrastructure etc. only affect the extensive margin (i.e. whether or not trade is created) and distance is a much larger barrier to the extensive than the intensive margin
- Systemically, the two margins can be studied using a decomposition of the WTN into an intensive and extensive network:
    - 1980 to 1990:
        - Extensive network: if no trade between $i$ and $j$ in 1980 but trade created by 1990, link between $i$ and $j$; otherwise no link
        - Intensive margin:
            - Positive component = positive changes in trade in existing relationships from 1980 to 1990
            - Negative component = negative changes in trade
    - Transformed to binary directed networks via nonzero values = 1
    - Intensive margin graph denser; higher average degrees; less centralized
    - Extensive margin represents creation of trade. Less dense than intensive margin = not as much trade is being created as existing trade is being supplemented. More centralized than intensive margin = a small number of countries are creating trade (China, Mexico, Nigeria, Tunisia).

## Connected research

[[International Trade Network.Modeling + Predicting the WTN.World Trade Network.Modeling the ITN - A Gravity Approach]]