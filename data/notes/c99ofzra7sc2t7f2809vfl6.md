### Fan et al.

Six different centrality measures are used to describe the relative importance of countries in the WTN. Countries are grouped into three different communities. The EU is considered as a standalone vertex and found to be the most important trading partner in the world. A method of **bootstrap percolations** is used to measure the impact of a country suffering a trade crisis on the rest of the WTN.

****

### Literature review

- The first studies of the WTN used a simple binary adjacency matrix (1 if trade exists, 0 otherwise). See *Topology of the World Trade Network*. 
- Later studies found that the WTN is approximately symmetrical and uses a symmetrized export-volume weighted adjacency matrix 
- Weighted WTN less disassortative than unweighted, node strength distribution right-skewed (few big hubs), power-law correlation between trade strength and GDP
- Formation of *trade islands* studied through community structures; mixed evidence for globalization
- **Robustness** of the WTN has been investigated, i.e. how sensitive the stability of the system is to shocks to one country; this has been investigated through **extinction analysis**
    - Crisis amplified if the country experiencing a shock is more integrated into the WTN; not dependent on GDP/size, but on position in network

### Adjacency matrix used

$$
w_{ij} = \tilde{w}_{ij} + \tilde{w}_{ji}
$$

where $\tilde{w}_{ij}$ is the proportion of country $i$'s exports to country $j$ to **total international trade volume**. $w$ is thus a symmetrical adjacency matrix.

### Network properties

- 183 vertices, 20051 links (2010 WTN)
- Small-world property, 0.05 higher clustering coefficient than previous studies
- Disassortativity; unweighted network more disassortative than weighted network
- WTN has **core-periphery** (bowtie) structure

### Community structures (clustering)

> <span style="background-color: #03cafc; color: black;">Definition</span>. **Modularity** is the metric most clustering algorithms seek to optimize, and is defined as
$$
Q = \frac{1}{2w}\sum_{i,j} (w_{ij}-\frac{w_i w_j}{2w})\delta_{c_i, c_j}
$$
> where $w$ is half the total link weight of the network, $w_i$ and $w_j$ are the **node strengths** of $i$ and $j$ (sum of weights attached to $i$ and $j$), $w_{ij}$ is the link weight from $i$ to $j$, and $c_i$, $c_j$ are the **communities** assigned to $i$ and $j$.

> <span style="background-color: #ffb812; color: black;">Interpretation</span>. $Q$ is the difference between the actual weight $w_{ij}$ minus its expected value, averaged across all the weights; this difference is taken account if $i$ and $j$ are from the same community, and not taken account if from different communities (per the delta function).

> <span style="background-color: #bc42f5; color: black;">Method</span>. This paper contributes the **weighted extremal optimization** (WEO) algorithm for optimizing modularity. Define the **modularity contribution** of a node $i$ as
$$
q_i = w_{r(i)} - w_i a_{r(i)}
$$
> where $w_{r(i)}$ is the sum of the weights of all links to nodes connected to $i$, and in the same community as $i$; and $a_{r(i)}$ is the expected value of a link in that community. We thus write $Q = \frac{1}{2w}\sum_{i}q_i$. Define **node fitness** of $i$, $\lambda_i$, as $\frac{q_i}{w_i}$; this is a normalization step such that the fitness value is between $-1$ and $1$. The WEO proceeds as follows:

1. Randomly divide graph into two equally sized communities.
2. Identify the node with the lowest fitness and move it to the other community. 
3. Re-calculate fitness for all nodes.
4. Repeat steps 2 and 3 until a maximum for $Q$ is reached.
5. Repeat the above to divide into more communities, until an absolute maximum for $Q$ is found.

> To escape from local maxima, the WEO algorithm does not select the absolute lowest-fitness node at every time-step, but instead selects nodes with probability
$$
P(q) \propto q^{-\tau}
$$
> where $q$ is the rank of the node (lowest fitness = rank 1) and $\tau$ is a constant on the order $1 + \frac{1}{\ln N}$ where $N$ is the total number of nodes. This is such that lowest-fitness nodes are more probably chosen, but not with certainty.


> <span style="background-color: #12ffd7; color: black;">Results</span>.

1. The WTN can be split into three parts: left, middle, right.
    - The left community is led by the US, and contains almost all countries in North and South America, and several other developing countries such as Nigeria, Congo, Israel and Afghanistan.
    - The right community is led by Japan and China, and contains Asia and East Africa.
    - The middle community is led by the UK and Germany, and contains Europe.
- The middle community is more clustered and has more nodes (72), vs. 42 nodes in the left and 69 in the right.
- Trade flows between communities make up 35.7% of all trade.
- All communities also exhibit their own core-periphery structures.

****

### Node centrality methods

> <span style="background-color: #bc42f5; color: black;">Method</span>. This paper presents six methods of observing node centralities for a node $i$:

1. **Degree centrality** $k_i$. $k_i = \sum_{j} \frac{A_{ij}}{N-1}$, where $A_{ij}$ is 1 if $i$ is connected to $j$ and 0 if not and $N$ is the total number of nodes.

    > <span style="background-color: #ffb812; color: black;">Interpretation</span>. Degree centrality is simply the out-degree of the node normalized by the maximum possible out-degree $N-1$.

2. **Strength centrality** $S_i$. $S_i = \sum_{j}w_{ij}$ where $w_{ij}$ is now the weight of the outgoing links. 
    > <span style="background-color: #ffb812; color: black;">Interpretation</span>. As $w_{ij}$ is now defined as the share of the export link $ij$ in the entire world market, strength centrality measures the share of $i$ in total exports.

3. **Closeness centrality** $C_i = \frac{N-1}{\sum_{j=1}^N d_{ij}}$ where $d_{ij}$ is the distance between nodes $i$ and $j$. The lower the distance, the higher the closeness centrality.

4.  **Eigenvector centrality** $E = AE$ for adjacency matrix $A$ and vector $E$. Defined in "Ownership Networks".

5. **Betweenness centrality**. $B_i = \frac{2}{n(n-1)} \sum_{j,k} \frac{\sigma(j,k|i)}{\sigma(j,k)}$  where $\sigma(j,k|i)$ is the weighted number of paths which pass from $j$ to $k$ through $i$ and $\sigma(j,k)$ is the weighted numbeer of paths that pass from $j$ to $k$.

    > <span style="background-color: #ffb812; color: black;">Interpretation</span>. The betweenness centrality of node $i$ is the proportion of shortest paths from one node to another which pass through $i$, weighted by the total possible number of paths ($\frac{2}{n(n-1)}$).

6. **Community importance**. Classifies nodes into "bridge" and "core". Bridge nodes bridge two communities; core nodes serve as trade hubs for their communities.

> <span style="background-color: #12ffd7; color: black;">Results</span>.

- US ranks first in strength, eigenvector and community centralities. China ranks second; large gap between China and other countries.
- Large degree centralities for most countries.
- Large portion of strength centrality concentrated in small number of countries.
- Closeness centrality shows that most countries are fairly well-connected and close.
- Strong correlation (0.968) between strength and eigenvector centralities; i.e. countries which take up large share of world trade have important trading partners.
- Low betweenness values for most countries. 
- High correlation between core nodes in communities and high strength centralities.


****

- **Role of the EU**. If taken as an aggregated vertex, the EU ranks ahead on all metrics. The UK has little trading incentive to leave the EU.

### Cascading failure and bootstrap percolation

> <span style="background-color: #bc42f5; color: black;">Method</span>. The **bootstrap percolation** method is applied to measure the cascading effects of a trading crisis for one country on the rest of the WTN. 

- Nodes are defined to be either **normal** or **abnormal**: normal represents stable exports/imports from that country, abnormal represents a trading crisis
1. All countries are initially normal.
2. Suppose that the trading link between $i$ and $j$ fails, making $i$ and $j$ both abnormal.  For each normal country, the proportion
$$
\frac{(\text{abnormal imports})}{(\text{normal imports})}
$$
is found, i.e. the proportion of its imports from abnormal countries to its imports from normal countries. If this proportion exceeds the **defense threshold** value, that country becomes abnormal.
3. Repeat until there is no change to the WTN.

> <span style="background-color: #12ffd7; color: black;">Results</span>.

- Failure propagation is measured by **scope of impact**, i.e. the proportion of countries that become abnormal.
- Scope of impact is sensitive to defense threshold: if defense threshold is 0.1, a random disconnection yields a scope of impact of 0.1 (18 countries), while if defense threshold is 0.3, only 2 countries are affected on average.
- Exports from the EU to Japan are found to be particularly important.

