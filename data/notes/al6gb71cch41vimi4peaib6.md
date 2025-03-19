### Fagiolo et al.

The authors investigate **null models** of the WTN: randomly generated graphs that preserve some features of the WTN, like node degree or strength, to be compared against by the actual WTN to determine whether or not its properties are significant. 

***

## Literature review

### Introduction to null models

- The properties of the WTN are well-studied, but the mechanisms that produce its properties aren't
- In order to determine whether these properties (clustering, centrality, degree etc.) are genuinely caused by economic effects or just statistically random, we compare against **null models**: randomly generated models that preserve some property of the original WTN (e.g. node strength) but are otherwise completely randomized
- Such null models are either generated **computationally** (through an iterative algorithm; demands high computation time) or **analytically** (through direct formulas)
- One problem with null models in the WTN is that they will always generate nonzero links, which does not match the reality of the WTN; this makes the WTN an impossible outcome of the null model
- Squartini et al. (2011) states that the binary WTN properties & architecture are reproducible by null models, but not the weighted WTN (specifically, network disassortiativity and clustering are not reproducible)
- In essence, the **number** of trading partners of a country in the WTN sufficiently explains the position of the country in the network; but its **total imports and exports** do not explain its position in the weighted WTN.

### Properties of the WTN

- Most surveys conducted via binary models:
    - Serrano and Boguna (2003) - disassortative pattern, hierarchical arrangements
    - Garlaschelli and Loffredo (2005) - these patterns are stable over time; node-degree distributions skewed
- Some papers survey the WTN using weighted approaches:
    - Fagiolo et al. (2008) show that the properties of the weighted WTN differ from its unweighted counterpart; node-strength distribution left-skewed
    - Fagiolo et al. (2009) show that the WTN architecture has been stable from 1981-2000; node degree correlates with country GDP; well-connected countries trade intensely with other well-connected countries; form few but intensive trade clusters
- WTN properties are useful in explaining economic phenomena:
    - Kali and Reyes (2010) show that trade structure properties like node degree and concentration are good predictors for GDP growth
- However, no models have been introduced that explain why the WTN exhibits those properties
- This paper tests the **null hypothesis** that the properties of the WTN arise from random generation rather than actual economic causes, focusing on node in/out degree and strength constraints
    - If yes, then the properties of the WTN cannot be described by **first-order** properties like node strength alone; second-order properties like clustering have to be studied

## Methods

- Computational methods for generating null models have the downside of being time-intensive, e.g. the rewiring algorithm, which is performed in $O(N^2)$ for a graph of $N$ nodes
    - This is worsened by the need to take an average value between the randomly generated graphs to obtain what the "expected" null model would look like

- As such, an analytical **maximum-entropy random graph** mmodel is used:

> <span style="background-color: #12ffd7; color: black;">Model</span>. **Maximum-entropy random graph generation model**.

For an original real-world graph with $N$ nodes, the ultimate goal of the model is to generate a **probability distribution** over all possible $N$-node graphs $G$, $P(G)$. In particular, we want:
- The actual real-world graph to be the most probable outcome of this random model, such that the model recaptures the real-world graph.
- Some constraint to be specified, e.g. the node degree of any graph $G$ corresponds with that of the actual real-world graph.

To generate such a probability distribution, we refer to the notion of **entropy**:

$$
S = -\sum_{G} P(G)\ln P(G)
$$

and more specifically, the **maximum-entropy principle**, which states that as higher-entropy systems contain less information, we want to maximize the entropy of the random graphs so that they contain as little information (i.e. order) as possible:
$$
P(G) \text{ maximizes $S$}.
$$
The solution to this is analytically given by
$$
P(G) = \frac{e^{-H(G)}}{\sum_{G} e^{-H(G)}}
$$
where the denominator is a normalization term to ensure that the probabilities sum to 1, and $H(G)$ is the *energy term*
$$
H(G) = \sum_{a} \theta_a C_a(G)
$$
with $C_a$ being the constrained network measures, e.g. degrees of nodes of $G$, and $\theta_a$ being parameters to be determined. In particular, $\theta_a$ are determined by 
$$
\max_{\theta} P(G^*)
$$
where $G^*$ is the real-world graph (the WTN in this case), i.e. the set of parameters $\theta$ is the set that maximizes the probability of the real-world graph being the outcome of the model. 

> Garlaschelli and Loffredo 2008 show that this is mathematically equivalent to ensuring that the constrained measures (e.g. node degree) are equivalent to the real graph.

Finally, the averaged properties over the generated $G$ (e.g. node centrality, clustering, etc., etc.) can be simply found by
$$
\langle X \rangle = \sum_{G}P(G)X(G)
$$
denoted the **randomized value** of property $X$.

This is an analytical model, and is thus much faster than computational graph-generation models.

## Results

- Take Kristian Gleditsch (2002) database on international trade flows from 1950 to 2000
    - The size of the WTN changes over time due to geopolitical changes
    - Directed network, but relatively reciprocal
- Focus on following topological properties:
    - Total NS and ND
    - ANND and ANNS
    - Clustering coefficients
- Calculate correlations between properties; normalize properties via normalizing trade flows by yearly total trade
- Fit maximum-entropy random graph model for:
    - In-degree and out-degree constraints (binary WTN)
    - In-strength and out-strength constraints (weighted WTN)
- Standard deviations for each measure is calculated, allowing for 95% confidence interval calculations via $t$- and $\chi^2$-tests with $N-1$ d.f. 
- If the correlation between two measures $X$ and $Y$ is reproduced on the random graph, then $X$ "explains" $Y$
    - Interested in following correlations:
        - ANND and ND
        - CC and ND

### Binary WTN
- ANND patterns replicated; node-by-node ANNDs between null and actual model correlated
- Disassortativity replicated by null model, suggesting it is economically insignificant
- Null model matches negative CC-ND correlation and also predicts average CC

### Weighted WTN

- Weighted WTN differs in many properties with binary WTN: only weakly disassortative, positive CC-ND instead of negative CC-ND correlation
- Null model predicts decreasing trend of ANNS but fails to predict its average value
    - Correlation between predicted and expected ANNS fluctuates between 0 and 0.5; bad predictions
    - Disassortativity can also not be predicted well
- Null model cannot replicate clustering trends
    - WCC-NS correlation not observed

### conclusions
- Binary WTN: degree of each node is already maximally informative (can be used to accurately predict ANND and CC)
- Weighted WTN: need higher-order measures like CC and ANND