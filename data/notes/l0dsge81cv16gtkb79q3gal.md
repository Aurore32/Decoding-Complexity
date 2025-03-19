### Serrano and Boguna

The World Trade Network satisfies the properties of a complex network.

****

### Definition of a complex network

> <span style="background-color: #03cafc; color: black;">Definition</span>. A  **complex network** demonstrates the following properties:

- A **scale-free** degree distribution, where the fraction of nodes with degree $k$, $P(k)$, follows an inverse power-law distribution $P(k) \propto k^{-\gamma}$, where $2<\gamma\leq 3$. 
    - <span style="background-color: #ffb812; color: black;">Interpretation</span>. This implies that there are far fewer nodes with a higher degree than a lower degree; the network will be centered around a few "hubs", i.e. nodes which are much more well-connected than others.
- The **small-world** property, where the **average path length** between any pair of nodes grows logarithmically with the graph size.
    - <span style="background-color: #ffb812; color: black;">Interpretation</span>. The size of the graph could be very large (say 1000 nodes), but any two randomly selected nodes will have a small distance on average (e.g. 3) due to the logarithmic relationship between graph size and distance.
- A high **clustering coefficient**, defined for a node $i$ to be
    $$
    \frac{2n_i}{k_i(k_i-1)} = \frac{n_i}{(\frac{k_i(k_i-1)}{2})} 
    $$
    where $n_i$ is the number of pairs of nodes connected to $i$ that are themselves connected, and $k_i$ is the degree of $i$, i.e. the number of nodes connected to $i$
    - <span style="background-color: #ffb812; color: black;">Interpretation</span>. $(\frac{k_i(k_i-1)}{2})$ is the total number of possible pairs of nodes connected to $i$ (= $k_i\choose 2$); thus, the **clustering coefficient** is the ratio between the pairs which are connected to the total number of pairs.
- Recently, a **degree-degree correlation** has also been added to the list of properties: the network should be either **assortative**, i.e. high-degree vertices are connected to other high-degree vertices, or **disassortiative**, i.e. high-degree vertices are connected to low-degree vertices

### The World Trade Web is a complex network

> <span style="background-color: #bc42f5; color: black;">Method</span>. The adjacency matrix for the World Trade Web in this paper is **unweighted** and is defined for countries $i$, $j$ to be

$$
A_{ij} = \frac{1}{1+\delta_{I_{ij},E_{ij}}}(I_{ij}+E_{ij})
$$

> where $I_{ij}$ is $1$ if there are **imports** to $i$ from $j$ beyond a certain threshold, and $E_{ij}$ is $1$ if there are **exports** from $i$ to $j$ beyond a certain threshold. $\delta$ denotes the Kronecker delta function.

> <span style="background-color: #ffb812; color: black;">Interpretation</span>. $A_{ij}$ is zero if there are no imports or exports between $i$ and $j$ at all, but one otherwise (given the Kronecker delta). It thus represents whether there are trade relationships between $i$ and $j$.

Consequently, the adjacency matrix addressed in this paper is **symmetrical**. 

- There are 179 vertices and 7510 directed links.
- The average degree is 30.9.

> <span style="background-color: #12ffd7; color: black;">Takeaways</span>.

- **Reciprocity**: the fraction of trade relationships which are reciprocal is 0.61; this is (apparently) enough to think of the global trade network as reciprocal enough to be undirected (?)
- **In- and out-degree correlation.** If in-degree is defined as importing nations and out-degree is exporting nations, the in-out correlation is 0.91.
- If the network is symmetrized based on the above definition, the average degree $\langle k \rangle$ is 43, which is very high; if the network is instead symmetrized based on bi-directionality, i.e. $A_{ij}=1$ only if both import and export links exist, then $\langle k \rangle$ is only 18.

****

- **Degree distribution**. The proportion of the degree $k$ peaks at $k \approx 20$ and decays according to a power law distribution $P(k) \propto k^{-2.6}$ after that; the network is thus **scale-free** for $k > 20$, but not below that.
- Degree is positively correlated with country per capita GDP (0.65 correlation); some countries, like China, Brazil, and Russia, are relatively low in per-capita GDP but high in degree.
- **Clustering distribution**. The clustering coefficient $c$ is positively correlated with $k$ by $c \propto k^{-0.7}$. The average clustering coefficient is 0.65, which is 2.7 times greater than the random expectation.

****

- **Degree-degree correlation**. Defined formally as $P(k'|k)$, the probability of the degree of a node being $k'$ conditioned upon the degree of a connected node being $k$. This can be measured by **average nearest neighbor degree** (ANND), the average degree of a node's connected given that it has a certain degree. If there is no degree-degree correlation, then ANND is unaffected by degree; if there is a correlation, then ANND is dependent on degree. A power law decay $ANND \propto k^{-0.5 \pm 0.05}$ was found; this indicates **disassortativity** (ANND inversely propotional to degree; high-degree nodes connected to low-degree ones).

****

- **Overall topology**. 
    - Size 179, average degree 43, average path length 1.8.
    - **Reciprocity**. In-degree and out-degree correlation (unsymmetrized) is 0.91; highly reciprocal.
    - **Degree distribution**. Peaks at $k=20$; follows scale-free distribution $k^{-\gamma}$ with $\gamma = 2.6$ affterwards. A few large hubs with many small countries with little trade.
    - **Clustering distribution**. $c\propto k^{-\omega}$ with $\omega = 0.7$. 2.7 times as clustered as a random graph (clustering coefficient $0.65$.)
    - **Average nearest neighbor degree.** Disassortative behavior with $ANND \propto k^{-v_k}$ and $v_k = 0.5$. Leads to conclusion that the World Trade Network has a few large hubs connected to small countries.
        - Could be that WTN is split into several clusters, with hub countries connecting these clusters. 