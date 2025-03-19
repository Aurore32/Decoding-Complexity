### He and Deem

The WTN exhibits a modular/hierarchical structure that has become less clustered over time as a result of globalization, measured through the **cophenetic correlation coefficient** (CCC). In the past 40 years, the authors demonstrate the following results: (1) the WTN's decreasing hierarchy leads to more sensitivity to recessionary shocks, and (2) the hierarchy of the WTN increases as a response to these shocks.

****

## Literature review

- Evolving systems like the WTN tend to settle into **modular structures** (i.e. modules which are highly clustered) - Sun and Deem 2007
    - The speed of such a state being reached depends on three factors:
        1. The network being a "glassy landscape" (i.e. slow to respond to change due to network complexity)
        2. The network experiencing outside change
        3. The network's agents (countries) exchanging information
    - The WTN satisfies all of the above
- **Hypothesis.** More modular structure increases resistance to recessions; weaker modular structure (due to globalization) reduces resistance to recessions

## Methods


- Comtrade UN trade data from 1962 to 2007
- Nodes = countries, links = trade value (not scaled by GDP)
-  A **distance matrix** for the WTN is calculated by $d_{ij} = \max(M_{ij}) - M_{ij}$ i.e. minimum distance for closest trade link. 

> <span style="background-color: #12ffd7; color: black;">Model</span>.  **Average linkage hierarchical clustering algorithm**. For a distance matrix $D$, the clustering algorithm depends on the metric

$$
L(r,s)= \frac{1}{n_r n_s} \sum_{i \in r}\sum_{i \in s} D_{ij}
$$
> i.e. the pairwise distance between points in the clusters $r$ and $s$, averaged across the number of pairs. The algorithm is as follows:

1. Take all the nodes in the WTN. Find the pair with the smallest pairwise distance.
2. The above pair of nodes are merged, and beccomes a new "node" (cluster).
3. Repeat step 1 and 2 until all pairs are found.

Repeat until all pairs are found. This creates a "hierarchy" of nodes (lowest layer = size-2 clusters, highest layer = size-$N$ clusters with $N$ being the number of nodes). 

Using this hierarchy, a **cophenetic matrix** $C$ is found where $c_{ij}$ is the height/layer of the hierarchy diagram (treelike dendrogram) where $i$ and $j$ are merged together. For instance, if China and the US are merged on the first step, then their cophenetic distance is 1. This matrix will be lower triangular.

Finally, a **cophenetic correlation coefficient** (CCC) is calculated representing how closely the cophenetic distance matrix and the actual distance matrix match:

$$
CCC = \frac{\sum_{i < j} (d_{ij}-\bar{d})(c_{ij}-\bar{c})}{\sqrt{\sum_{i<j} (d_{ij}-\bar{d})^2 \sum_{i<j} (c_{ij}-\bar{c})^2}}
$$
where $\bar{c}, \bar{d}$ are the average cophenetic distance and actual distances. Hierarchical datasets have a high CCC while non-hierarchical datasets have lower CCC.

## Results

- World trade divided into continental modules

![alt text](image-2.png)

- Globalization has decreased the hierarchical nature of the WTN

![alt text](image-1.png)

- Years of recession increase the CCC (e.g. 2000); marked with red bars
    - Recessions promote trade protectionism and regional integration
    - Free trade promotes globalization and decreases hierarchy
- CCC increased in all 7 recessions from 1980 to 2007; trade to GDP ratio not as affected, showing that recessions cause a reduction in CCC and not the trade to GDP ratio (trade openness)
- Decreases in hierarchy due to globalization weakens the WTN to shocks
    - Ratio of world GDP decrease to US GDP decrease in financial crisis negatively correlated with CCC: world less hierarchical -> world more impacted by financial recessions in the US
- Dynamical model of recession spread confirms increased sensitivity due to globalization
    - Recession assumed to start in the US
    - For each country $i$, its GDP at time $t$ is denoted $Y_i (t)$; the exports of country $i$ to country $j$ as $X_{ij}(t)$; the total exports of $i$ as $X_{i}(t)$
    - $Y_i(t+1)$ is updated by $Y_i(t+1) = Y_i(t) + P_i(\frac{X_{i}(t)-X_{i}(t-1)}{X_i(t-1)})$, where $P_i$ is the export to GDP ratio of country $i$; i.e. new GDP = old GDP + export-to-GDP ratio times rate of change of exports
    - $X_{ij}(t+1)$ is updated by $X_{ij}(t+1) = X_{ij}(t) (\frac{Y_i(t+1)}{Y_i(t)})$, i.e. old exports times rate of change of GDP
    - The model converges to a steady state
    - Impact of recession in 2006 found to be 6 times greater than impact in 1968
    - Recovery from recession slower when hierarchy is lower
