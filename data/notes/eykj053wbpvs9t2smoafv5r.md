### Hoppe and Rodgers, 2015

This paper investigates the fitness model of the WTN and offers a new definition of node fitness.

***

## Literature review
- Generally agreed that fitness model best fits WTN: Caldarelli et al. 2002 (scale-free networks), Servedio et al. 2004, [[International Trade Network.Modeling + Predicting the WTN.Fitness]] and [[International Trade Network.Modeling + Predicting the WTN.Fitness.Fitness-Dependent Topological Properties]]
- Dynamic models via fitness have been investigated in Besedes and Prusa 2011 (extensive and intensive margins) and [[International Trade Network.Modeling + Predicting the WTN.ERGM.Stochastic Trade Networks]]
- Gravity models fail because trade is shown to be less and less correlated with distance as time goes on (Picciolo et al. 2012, Chiarucci et al. 2014, Lawless 2010)
- Network effects are worth investigating because they show how trade can affect economic welfare:
    - Kali and Reyes, "The architecture of globalization: a network approach to international economic integration", 1% increase in centrality increases nation GDP by 0.27%
    - [[International Trade Network.Crisis Propagation.Financial Contagion in the WTN]] and Garas et al., "Worldwide spreading of economic crisis", suggest that the WTN can help identify crisis vulnerabilities

## Methods

### Static fitness model

- Fitness model endows every node in the network of $N$ nodes and $M$ edges with a fitness $x$
- The probability that a link exists between two nodes $x$ and $y$ is $f(x,y)$
- This may be understood as a static process; if a new node is created, then the probability that it is between $i$ and $j$ is $\frac{f(i,j)}{\sum f(k,l)}$ where the denominator is the total probability across all nodes
    - This leads to repeated links and edges, but not an issue in sparse networks
- Call the matrix containing the probabilities $C(i,j)$ the *microscopic structure* of the network
- Fitness can be defined in multiple ways: 
    - $x_i = \theta(w_i) = \frac{1}{N}\sum_{i=1}^N H(w_i - w_j)$ where $H$ is the Heaviside step function, i.e. the number of countries whose GDP is lower than $i$'s normalized by $N$
        - Empirically, there is a near-exponential relationship between fitness using this definition and node degree
    - Alternatively, in [[International Trade Network.Modeling + Predicting the WTN.Fitness.Fitness-Dependent Topological Properties]] we have $x_i = \frac{w_i}{\sum_{i=1}^N w_i}$ or $x_i = \frac{w_i}{N\ \sum_{i=1}^N w_i}$.

### Role of fitness in creation of edges

- *Activity* is defined, for a country $i$ during some time period $t$, as 
$$
\frac{\text{number of edges gained during $t$}}{\text{total number of edges gained by all countries}}
$$
- However, there is no clear relationship between fitness and activity
    - Instead of appearing between high fitness, 1990-2000 shows that links form between high-fitness and low-fitness countries
    - This implies some additive component to the attachment function $f(x,y)$
    - Probability of node formation is nonzero at the edges (when the fitness of one country is zero)