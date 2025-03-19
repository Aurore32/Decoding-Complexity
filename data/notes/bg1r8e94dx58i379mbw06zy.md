### Bhattacharya et al.

Analysis of the weighted WTN reveals a log-normal distribution of scaled link weights; power-law growth of trade strenght with GDP holding true for all countries; **"rich-club coefficient"** analysis reveals that the size of the rich club (countries controlling top 50% of all trade) is shrinking. Simple dynamical model based on gravity model reproduces properties of WTN.

****

## Methods and Results

- Dataset is bilateral trade over 53 years
    - Number of links and nodes grew systematically
    - Link density roughly constant
- Adjacency matrix used is $\frac{e_{ij}+e_{ji}+i_{ij}+i_{ji}}{2}$ where $e$ is exports and $i$ is imports, to smooth ouut inconsistencies between $e_{ji}$ and $i_{ij}$; this graph is symmetrical
    - Distribution of weights broad; smallest less than $1M\$$, largest more than $100000M$$
    - Majority of links are small, with a few large links
    - Average weight per link grows from 15.54 million dollars to 308.8 million dollars in 2000
- **Probability density distribution** of link weights
    - Log-log plots of link weight vs frequency have linear regions which are interpreted as a power law relationship for the PDF
    - However, more accurate fits are given by a log-normal distribution
        - Corroborated by Fagiolo et al. 2007 and Serrano 2007
- Strength distribution of nodes
    - Define $\gamma = \frac{\partial \log s}{\partial \log G}$ with $G$ being GDP and $s$ being the strength of a country in the WTN. This results in the log-log relationship between $s$ and $G$, which is found to be positive and constant (i.e. a power law) for a single country over time
    - Distribution of $\gamma$ for different countries:
         - 12 countries larger than 2 - these countries are countries born after the dissolution of the USSR (makes sense because new trade relationships, i.e. strength in the graph, was created faster than GDP was gained)
        - Avg is 1.26 (1.06 if 12 countries not taken into account)
        - Irwin (2002) observes that GDP-world trade volume power law coefficient $\approx 1.16$, close to country-average value
- **Rich club coefficient**

> <span style="background-color: #03cafc; color: black;">Definition</span>. **Rich-club and rich-club coefficient**.

- A "rich club" is a subset of $n_k$ nodes whose degree values are at least $k$
- The "rich-club coefficient" of these nodes is defined as 
$$
\phi(k) = \frac{2E_k}{n_k(n_k-1)}
$$
i.e. the density of the club.
- Empirically, this definition has been shown to be insufficient: a randomly generated graph can occasionally display a rich-club effect

- It is suggested that a **maximally random network** (MRN) with degrees equal to the WTN needs to be created, leading to a set of rich-club values $\phi_{random}(k)$
    - Then, the ratio $\rho(k)=\frac{\phi(k)}{\phi_{random}(k)}$ is observed to check how significant the rich-club effect of the WTN is vs. a randomly generated control
- The binary WTN does not display significant rich-club effects ($\phi \approx 1$, no difference from a random network)
- The weighted WTN can have a similar rich-club coefficient defined as 
$$
\phi(s) = \frac{2\sum_{i,j}w_{ij}}{n_s(n_s-1)}
$$
for the $n_s$ nodes above node strength $s$.

> <span style="background-color: #ffb812; color: black;">Interpretation</span>. The rich-club coefficient is a measure of the weighted density of the rich club.

- Correspondingly, a MRN is generated with both $k$ (degree) and $s$ (strength) preserved and with a symmetric weight matrix.
- A self-iterative method is used:

1. Arbitrary numbers to weights $w_{ij}$ are assigned, maintaining that $w_{ji} = w_{ij}$.
2.  For every node $i$, the difference $\delta_{i} = s_i - \sum_{j} w_{ij}$ is calculated (i.e. how far away the current node strength is from the desired node strength)
3. Weights for $i$ are updated as $w_{ij} \to w_{ij} + \delta_{i}\frac{w_{ij}}{\sum_{j} w_{ij}}$ such that $i$ has strength $s_i$.
4. Repeat the above until weights converge.

- A MRN generated with this method again yields $\rho(k) \approx 1$, i.e. rich club coefficients of the WTN are insignificant; this does not mean that rich clubs do not exist, and can be explained by the fact that the MRN and the ITN share 85% of elements (nodes have same degree and strengths)

- A rich club effect can be demonstrated by simply considering the proprotion (% of trade volume owned by rich club countries).
    - Top 19% of countries owned top 50% of trade in 1948; now 8% in 2000
- **Dynamical model based on gravity model.**
    - Basic model is the gravity model of trade $F_{ij} = \frac{G m_i m_j}{l^2_{ij}}$; generalized to a parametric form

    $$
    F_{ij} = m^{\alpha}_i (\frac{m_j^{\beta}}{l_{ij}^{\theta}} / \sum_{k\neq i}\frac{m_k^{\beta}}{l_{ik}^{\beta}})
    $$
    i.e. the base gravity model, w/ free parameters $\alpha, \beta, \theta$, and considering the GDP/distances of every other country in the network aside from just $i$ and $j$.
    - Want to recreate WTN from randomized graph through different timesteps:
    1. Randomly assign distance and GDP data to nodes: a unit square represents the world, $N$ points are chosen in the square, and GDPs $m_1, m_2, ..., m_N$ are randomly assigned to them which sum to $1: \sum_{i=1}^N m_i = 1$.
    2. Randomly choose a country pair $(i, j)$.
    3. Calculate magnitude of transaction by gravity model.
    4. Adjust GDPs based on transaction:
        - Define $\tilde{F}_{ij}$ as $F_{ij}+F_{ji}$.
        - Country $i$ loses GDP equal to its exports to $j$: $m_i = m_i - F_{ij}$.
        - Country $j$ loses GDP equal to its exports to $i$; $m_j = m_j - F_{ji}$.
        - Country $i$ gains a share $\epsilon$ of $\tilde{F_{ij}}$; country $j$ gains a share $1-\epsilon$.
        - Finally we thus have
        $$
        \begin{cases}
        m_i = m_i - F_{ij} + \epsilon \tilde{F}_{ij} + \Delta_i \\
        m_j = m_j - F_{ji} + (1-\epsilon) \tilde{F}_{ij} + \Delta_j \\
        \end{cases}
        $$
        in which $\Delta_i$ and $\Delta_j$ are correction terms added to ensure that the GDPs do not become negative (countries cannot hold debts).
        - $\epsilon$ is randomly chosen for each interaction.
    5. GDPs are rescaled so that they sum to 1.

- This dynamical model eventually converges to a stationary state with the average square GDP fluctuating around a mean.
- A graph is constructed after the model completes, with link weights equal to the total value of transactions $\tilde{F}_{ij}$ between two countries over the iterations. The model is stopped when a desired density is reached.
- The constructed graph has similar properties to the real WTN:
    - GDP distribution consistent to Pareto law (Pareto 1987)
    - Strength-strength correlation (strength of two connected nodes $s_i$ and $s_j$) is $w_{ij}^{\nu}$ with $\nu = 0.98$ in the large weight limit; this is similar to the real WTN with $w_{ij}^\nu = 0.65 \to 0.9$ for lower and higher weights respectively.

    