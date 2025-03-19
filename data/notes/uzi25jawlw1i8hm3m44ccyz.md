### Liu et al.
 
The authors summarize every study conducted on the WTN from 2003 to 2023 and offer their thoughts on future areas to explore.

***

## Introductory literature review

- Globalization has led to a complex system of trade where bilateral trade relations are affected by the entire network
- The WTN has consequential effects on other spatiotemporal networks, like geopolitical relations (Mansfield and Pevehouse 2000), transportation (Hummels 2007), and population movements ([[International Trade Network.Misc.Human Migration and Trade]])
- WTN analysis offers superior insights to bilaterial trade analysis:
    - Illustrates higher-level dependencies
    - Variance and evolution across time and space
    - Allows countries to make trade decisions with fewer risks
- History of network analysis of world trade:
    - Hilgerdt 1943: impact of trade on monetary equilibrium
    - Snyder and Kick 1979: hierarchical structure of world trade
    - Serrano and Boguna 2003: complex-network structure of world trade
    - An
- WTN analysis mainly includes case studies (Reyes et al. 2010; Benedictis 2012, [[International Trade Network.Network Analysis.World Trade Network]])
- Paper studies 325 different papers studying the WTN from 2003 to 2023

## Research framework
### Model summaries
- **Structure prediction**
    - Spatial econometric models
        - Node fitness models
        - Cascading failure models
        - Configuration models
- **Correlation analysis**
    - Mathematical models and correlation coefficients
- **Topology analysis**
    - Node distance
    - Node centrality
    - Denseness
    - Heterogeneity
    - Community and backbone
    - Stability and implicit flow
### Data sources
- UN Comtrade (data since 1962)
- ResourceTrade and CITIES (trade data from specific areas)
- Explanatory variables (e.g. inflation, GDP, etc.): NBER, World Integrated Trade Solution (WITS), IMF, UNCTADstat
    - Trade, tariffs, investments, output value, population, etc.
- Input-output analysis: Eora, WIOD, EXIOBASE, OECD-ICIO (15909 sectors across 190 countries)
- Integrated data platforms: World Bank (6500 databases across many fields), CEPII (economic + trade data, cultural data), Kristian Skrede Gleditsch (K-G)
- Other databases (politics, immigration, etc.)
- Most cited for WTN studies:
    - UN Comtrade (100)
    - CEPII (45)
    - World Bank (37)
    - K-G (37)
    - IMF (32)
### Classifications of the WTN
- Directionality and weight
    - Undirected-unweighted ([[International Trade Network.Network Analysis.Trichotomous Measure of World-System Position in the WTN]])
    - Undirected-weighted ([[International Trade Network.Clustering (Trade Blocs).Rich-Club Phenomenon]])
    - Directed-weighted ([[International Trade Network.Misc.Triadic Analysis of Agricultural Trade Networks]])
    - Most of the literature studies weighted-directed WTNs; however, ([[International Trade Network.Modeling + Predicting the WTN.Fitness.Microscopic Study of Node Fitness]]) believe that weighted WTNs do not have greater explanatory power than unweighted WTNs
- Node definition
    - Countries = nodes (most common)
    - Products = nodes or sectors = nodes ([[International Trade Network.Multiproduct Trade Networks.Who Buys What Where]])
    - Bipartite WTN ([[International Trade Network.Modeling.Multiproduct Trade Network.Prediction in Complex Systems]])
    - Groups of countries = nodes ([[International Trade Network.Clustering.Network of Networks Perspective on Global Trade]])
- Edge definition
    - Import vs. export data
    - Different types of flow:
        - Monetary flow (most common)
        - Energy, emission, environmental impact, chemical flows 
        - **Topological flow**: 
            - Node similarity ([[International Trade Network.Clustering.Multi-Attribute Community Detection in WTN]])
            - Weight-adjusted topological flow (De Andrade and Rigo 2018)
            - Product-space proximity ([[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]])
            - Internode competition (An et al. 2014)
- Visualization tools
    - UCINET; Gephi; Cytoskape
    - ArcGIS; QGIS; Python and MATLAB
    - Web platforms such as RESOURCETRADE and FlowMapBlue
- Methodologies
    - Topology analysis
        - Temporal (global and local evolution of WTN)
        - Basic measures (distance, node centrality, denseness, heterogeneity)
        - Structural measures (backbone, community, stability, implicit flow, robustness)
    - Structural prediction
        - Dynamic simulation of WTN evolution over time
        - Spatial econometric models; cascading failure models
    - Correlation analysis
        - Relationship between WTN variables and other variables; relationship between WTN variables and WTN variables
        - Degree-degree correlation; centrality-degree correlation, etc.
        - WTN on economic growth

## Topology analysis

### Basic properties
- Distance
    - Topological proximity between nodes; distinct from weight
    - Several measures exist
        - Flow distance: min. number of steps between two nodes (unweighted), reciprocal of min. weight between two nodes (weighted) (De Andrade and Rego 2018)
        - Trade distance accounting for multilateral resistance effects ([[International Trade Network.Modeling + Predicting the WTN.Gravity.Topological Analysis of Trade Distance]])
        - Estrada communication distance ([[International Trade Network.Crisis Propagation.COVID-19 Diffusion]])
        - Minkowski distance considering various node properties ([[International Trade Network.Clustering.Multi-Attribute Community Detection in WTN]])
- Centrality
    - Degree centrality; closeness centrality; betweenness centrality; eigenvector centrality
    - Closeness and betweenness centrality measure global significance of the node as an in-between node (Zhong and An 2014, [[International Trade Network.Misc.Trade and Australia]])
    - Eigenvector centrality reflects the number of important nodes a node is connected to, and extends to several other concepts:
        - Katz centrality (Liu et al. 2019)
        - PageRank (Lamsal 2018)
        - HITS ([[International Trade Network.Network Analysis.Weighted HITS]])

- Denseness
    - Density
    - Clustering coefficients (Fagiolo 2007)
- Heterogeneity
    - Whether measures like centrality or node fitness are the same (homogeneous) or different (heterogeneous) for all nodes
    - Centrality distribution curves, average nearest neighbor centrality, heterogeneity coefficients
    - WAAND and ANND
    - Node heterogeneity index ([[International Trade Network.Misc.Plastic and China Plastic Ban]])
    - Disparity (Maeng et al., 2012)
    - Homophily ([[International Trade Network.Modeling + Predicting the WTN.Evolution of Commonwealth WTN]])

### Community properties
- Backbone
    - Threshold-based methods
        - Nodes exceeding certain degree/strength are part of the backbone
        - Inflexible; instead a top-X algorithm is used (Maeng et al. 2012)
    - Maximum-spanning tree methods
        - Subgraph with greatest sum of weights among all min. connected subgraphs
        - Employed by ([[International Trade Network.Network Analysis.Spanning Trees of the WTN]])
    - Null model based methods (Piccardi and Tajoli 2012)
- Community
    - Detection of strongly interconnected "trade islands"; helps understand trade regionalization
    - Modularity optimization (Piccardi and Tajoli 2012, [[International Trade Network.Clustering.Trade Networks of the BRI]], [[International Trade Network.Clustering.The Rise of China]])
        - Divisive algorithms (fragments entire WTN into smaller communities)
        - Agglomerative algorithms (starts from each individual node and builds up communities) ([[International Trade Network.Clustering.Identifying the Community Structure of the WTN]]; [[International Trade Network.Misc.Meat Trade Network]])
        - Community partition significance uses small perturbations (Hu et al. 2010) to determine whether global optimum solutions exist to community detection
- Stability
    - Extent of fluctuations in network topology over time
    - Set similarity: similarity of WTN between two years
        - Jaccard index; autocorrelation function; Hamming distance (An et al. 2014; Wang et al. 2022)
    - Matrix similarity ([[International Trade Network.Misc.Stability of Oil Network]])
    - Modified Hamming distance ([[International Trade Network.Clustering.Network of Networks Perspective on Global Trade]])
    - Community structure stability based on Normalized Mutual Information ([[International Trade Network.Modeling + Predicting the WTN.Kaolin International Trade]]; [[International Trade Network.Clustering.Identifying the Community Structure of the WTN]])
- Robustness
    - Stability of WTN when faced with disruptions
    - Penetration threshold ([[International Trade Network.Misc.Robustness of Oil Trade]])
    - Stability-based measures without disruptions
        - HHI ([[International Trade Network.Clustering.Identifying the Community Structure of the WTN]]; [[International Trade Network.Misc.Global Energy Flows]]; [[International Trade Network.Misc.Country Risks]])
        - Laplacian centrality
        - Fiedler eigenvalue
        - Spectral radius ([[International Trade Network.Clustering.Multi-Attribute Community Detection in WTN]])
- Implicit flow
    - Influence between non-connected nodes in WTN
    - Random walker model ([[International Trade Network.Network Analysis.Dominant Flows in the WTN]])
    - Input-output analysis ([[International Trade Network.Misc.Evolution of World Trade]])

## Structure prediction
### Gravity models
- Incapable of considering multilateral dependence of trade relationships
- Two types of improvements:
    - Introducing WTN parameters into GM
        - Degree centrality ([[International Trade Network.Network Analysis.World Trade Network]])
        - Human migration ([[International Trade Network.Misc.Human Migration and Trade]])
        - Centrality distribution power index ([[International Trade Network.Economic Growth.Heckscher-Ohlin]])
        - GNN combined with GM (Verstyuk and Douglas 2022)
    - Changing the mechanisms of the GM
        - Changing indices of distance ([[International Trade Network.Network Analysis.Spanning Trees of the WTN]])
        - Effective trade distance rather than geographical distance ([[International Trade Network.Modeling + Predicting the WTN.Gravity.Topological Analysis of Trade Distance]])
        - Using General Bilinear Mixed Effects model to simulate multilateral dependence (Ward et al. 2013)
### Spatial regression models
- Consider spatial autocorrelation between nodes (local nodes influenced by neighboring nodes)
    - [[International Trade Network.Economic Growth.A Multi-Network Perspective]]

### Node fitness models
- Derived from intrinsic variable models: nodes possess an intrinsic value that determines connection probability between any two nodes
- Virtual network generated based on this fitness can reproduce properties of the real network
- Node fitness defined as normalized GDP ([[International Trade Network.Modeling + Predicting the WTN.Fitness.Fitness-Dependent Topological Properties]])
- Standard fitness model with simple binary relationship used ([[International Trade Network.Modeling + Predicting the WTN.Fitness.Fitness-Dependent Topological Properties]]); adjusted fitness model ([[International Trade Network.Modeling + Predicting the WTN.Structure and Evolution of the WTN]]; [[International Trade Network.Modeling + Predicting the WTN.Topology and Dynamics]])
- Fitness model used to forecast trade volumes ([[International Trade Network.Economic Growth.GDP-Driven Structural Prediction]])
- Fitness difference term proposed ([[International Trade Network.Modeling + Predicting the WTN.Fitness.Microscopic Study of Node Fitness]])

### Configuration models
- Maximum-entropy null model generation:
    - Binary generation (Squartini et al. 2011)
    - Enhanced generation (Mastrandrea et al. 2014)
    - Directed generation (Ruzzenenti et al. 2012)
    - Bipartite generation ([[International Trade Network.Crisis Propagation.Warning Signals for Crises]])
    - Fitness generation (Cimini et al. 2015)
- Empirical evidence suggests that the binary WTN can be entirely reconstructed from weights
- Also conducted two-step analysis ([[International Trade Network.Economic Growth.GDP-Driven Structural Prediction]]; Cimini et al. 2015)
- Comparisons between real WTN and null models reveal geographic dependency (Ruzzenenti et al. 2012), nestedness ([[International Trade Network.Clustering.Nested Structure of the WTN]]), and recession warning signals ([[International Trade Network.Crisis Propagation.Warning Signals for Crises]])

### Cascading failure models
- Based on supply chain theory
- Bootstrap percolation ([[International Trade Network.Crisis Propagation.Bootstrap Percolation and Attack]])
- Two improvements to bootstrap:
    - Weight distribution ([[International Trade Network.Crisis Propagation.Topology and Crisis Propagation]]); stronger nations suffer less from crises (Grassia et al. 2022)
    - Absorption of crises ([[International Trade Network.Crisis Propagation.Spillover Effects]]; [[International Trade Network.Crisis Propagation.COVID-19 and Shocks]])
    - Weak links in crisis propagation cannot be overlooked ([[International Trade Network.Crisis Propagation.Topology and Crisis Propagation]]; Lee and Goh 2016)

### Other models
- Topological similarity models; preferential attachment (Zhou et al. 2022)
- Agent decision models (each producer maximizes their own profit/minimizes their own costs) - globalization ([[International Trade Network.Modeling + Predicting the WTN.Locally Optimal Individual Decisions]]), Brexit ([[International Trade Network.Modeling + Predicting the WTN.Brexit]])
- Predicting link formation/export baskets via bipartite model ([[International Trade Network.Modeling.Multiproduct Trade Network.Prediction in Complex Systems]])

## Correlation analysis
### Correlation between topological attributes

- Degree-ANND correlation ([[International Trade Network.Network Analysis.Topology of the World Trade Web]]) and strength-ANNS correlation ([[International Trade Network.Network Analysis.Topology of the World Trade Web.Economic Integration in East Asia and Latin America]]) both negative and more pronounced over time ([[International Trade Network.Modeling + Predicting the WTN.Analytic Process Framework]])
- Out-degree and in-degree correlation ([[International Trade Network.Network Analysis.Topology of the World Trade Web]]) and out-strength and in-strength correlation positive, fit power law
- Positive degree-strength correlation (Liu et al. 2007; [[International Trade Network.Modeling + Predicting the WTN.Analytic Process Framework]])
- Clustering coefficient-degree correlation negative but WCC-strength correlation positive ([[International Trade Network.Network Analysis.Topology of the World Trade Web.Fagiolo et al]])
- Core-periphery topology

### Correlation between network attributes and other indicators

- Economic/political/environmental indicators, e.g. GDP; central nations in the WTN have higher GDPs ([[International Trade Network.Misc.Human Migration and Trade]]; Schiavo et al. 2014)
- Edge weights correlated with geographical distance ([[International Trade Network.Misc.Investment Networks]])

### Correlation between cross-product attributes

- Similarities between WTNs formed by different products or times
- Clustering coefficients, in- and out-strengths, etc. similar for products that share HS codes ([[International Trade Network.Multiproduct Trade Networks.Multinetwork of International Trade]])
- Human migration and WTN correlated ([[International Trade Network.Misc.Human Migration and Trade]]); FDI and WTN correlated ([[International Trade Network.Economic Growth.A Multi-Network Perspective]])

### Overlap between WTN and similar networks
- Jaccard index used to measure overlap between WTN and migration network ([[International Trade Network.Economic Growth.A Multi-Network Perspective]])
- Commodity-specific weighted analysis reveals that similar commodities have similar trade patterns ([[International Trade Network.Multiproduct Trade Networks.Multinetwork of International Trade]]; [[International Trade Network.Crisis Propagation.Multiplex Cascading Failure]])
- Element difference and quadratic assignment procedure (QAP) reveal correlations with the FDI, inflation rate, exchange rate, and high-tech exports ([[International Trade Network.Modeling + Predicting the WTN.Analytic Process Framework]])
- Positive effect of geographic adjacency and negative effect of institutional disparities on trade ([[International Trade Network.Multiproduct Trade Networks.Recommendations of New Produ]])

### Exponential random graph models

- Temporal ERGMs (Xu, Yang and Razzaq 2021; [[International Trade Network.Modeling + Predicting the WTN.ERGM.Humanistic Factors Along the BRI]])
- Separable TERGM for WTN evolution dynamics ([[International Trade Network.Modeling + Predicting the WTN.ERGM.ERGM Analysis of the WTN]])
- Use AIC and BIC

### Econometric models
- Influence of WTN on economic fluctuations ([[International Trade Network.Economic Growth.Trade and Volatility]])
- GNNs to predict national income levels (Panford-Quainoo et al. 2020)

## Discussion

- WTN analysis reveals structure and evolution of trade ([[International Trade Network.Network Analysis.World Trade Network]])
- Bilateral trade not independent of influences of other countries, requiring WTN ([[International Trade Network.Economic Growth.Gravity Rainbow]])
- WTN links can reveal:
    - Status of countries in global value chains (Reyes et al. 2010)
    - Implicit impacts between non-adjacent countries (Abeysinghe and Forbes 2005)
    - Heterogeneity ([[International Trade Network.Modeling + Predicting the WTN.Evolution of Commonwealth WTN]])
    - Triadic structures ([[International Trade Network.Clustering.Structure and Formation of Top Networks]])
    - Economic integration ([[International Trade Network.Modeling + Predicting the WTN.Measuring Globalization]])
- The WTN can be used to construct scenarios on multiple levels:
    - Level 1: trade itself
        - Multiscale ITNs ([[International Trade Network.Multiproduct Trade Networks.Recommendations of New Produ]])
        - Multiple commodity ITNs (Gephart and Pace 2015)
        - Temporal ITNs (Luo and Yuan 2021)
    - Level 2: the structure of trade
        - Centrality ([[International Trade Network.Network Analysis.World Trade Network]])
        - Distance measures (Piccardi and Tajoli 2012)
        - Communities ([[International Trade Network.Misc.Robustness of Oil Trade]]), stability of communities ([[International Trade Network.Misc.Features of Oil Trade]])
        - Density ([[International Trade Network.Network Analysis.World Trade Network]]), connectivity ([[International Trade Network.Multiproduct Trade Networks.Multinetwork of International Trade]]), trade chains (Reyes et al. 2010)
    - Level 3: the dynamics and evolution of trade
        - Random walkers ([[International Trade Network.Network Analysis.Dominant Flows in the WTN]]); input-output analysis ([[International Trade Network.Misc.Evolution of World Trade]])
        - Reconstruction of trade flows via basic network features ([[International Trade Network.Multiproduct Trade Networks.Who Buys What Where]])
        - Interaction between trade and other systems
- The WTN is useful for observing dynamic changes of world trade over time
    - Evolution of trade status of countries ([[International Trade Network.Network Analysis.Weighted HITS]]); formation of network hierarchies ([[International Trade Network.Modeling + Predicting the WTN.Analytic Process Framework]]); market regulations (An et al. 2014); economic prosperity ([[International Trade Network.Modeling + Predicting the WTN.Kaolin International Trade]]); integration (Tzekina et al. 2008; Barigozzi et al. 2010)
        - Integration leads to convergent behavior among economies ([[International Trade Network.Network Analysis.Synchronization of the WTN]])
    - Impact of other trends on trade:
        - Finance ([[International Trade Network.Clustering.Network of Networks Perspective on Global Trade]]); wars (An et al. 2014); varying impacts of shocks (Liu et al. 2019)
    - Policy recommendations
        - Increasing node degree is beneficial for countries (Sun et al. 2022)
        - Increasing complexity of products is beneficial ([[International Trade Network.Modeling + Predicting the WTN.Kaolin International Trade]]; Liao et al. 2018)
        - Market innovation matrix ([[International Trade Network.Misc.Trade and Australia]])
        - QAP Analysis ([[International Trade Network.Misc.Petroleum Along the BRI]]; [[International Trade Network.Modeling + Predicting the WTN.Analytic Process Framework]])
        - Risk mitigation:
            - Diversify partners (Li et al. 2021)
            - Improve productivity (Liang et al. 2020)
            - Develop alternative products ([[International Trade Network.Misc.Cruel Oil Competition Networks]])
            - Stimulating domestic consumption ([[International Trade Network.Misc.Country Risks]])
            - Increasing trade agreements ([[International Trade Network.Modeling + Predicting the WTN.Kaolin International Trade]])

## Future agendas
- **Broader scenario reconstruction**   
    - Analyze on a commodity-to-commodity basis ([[International Trade Network.Clustering.Nested Structure of the WTN]])
    - Cascading failure models ([[International Trade Network.Crisis Propagation.Multiplex Cascading Failure]]; Liu et al. 2016)
    - Artificial intelligence, including GNNs

## Connected research
- [[International Trade Network.Modeling + Predicting the WTN.Gravity.Topological Analysis of Trade Distance]], Wu et al., 2020
- [[International Trade Network.Clustering.Network of Networks Perspective on Global Trade]], 
- [[International Trade Network.Modeling.Multiproduct Trade Network.Prediction in Complex Systems]], Vidmer et al., 2015
- [[International Trade Network.Multiproduct Trade Networks.Who Buys What Where]], Ikeda et al. 2016
- [[International Trade Network.Modeling + Predicting the WTN.Fitness.Microscopic Study of Node Fitness]], Hoppe and Rodgers 2015
- [[International Trade Network.Network Analysis.Trichotomous Measure of World-System Position in the WTN]], Clark and Beckfield 2012
- [[International Trade Network.Misc.Triadic Analysis of Agricultural Trade Networks]], Shutters and Muneepeerakul 2012
- [[International Trade Network.Network Analysis.Topology of the World Trade Web.Economic Integration in East Asia and Latin America]], Reyes et al. 2010
- [[International Trade Network.Modeling + Predicting the WTN.Analytic Process Framework]], Zhao and Dzever 2018
- [[International Trade Network.Crisis Propagation.Multiplex Cascading Failure]], Zhang et al. 2016
- [[International Trade Network.Misc.Human Migration and Trade]], Fagiolo and Mastrorillo 2014.
- **Trade Blocs, Trade Flows, and International Conflict**, Mansfield and Pevehouse 2000. Membership in the same trade bloc decreases chance of military conflict.
- **Structure and formation of top networks in international trade, 2001-2010**, Zhou et al.