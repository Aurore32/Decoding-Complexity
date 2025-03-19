
### Schiavo et al.

The WTN and WFN (world financial network) are analyzed together and compared in regard to their properties, finding that the WTN is more densely connected than the WFN, that both networks exhibit core-periphery structures, and that the WFN is more hierarchical.

***

## Literature review

- Network formed from flow of **financial assets** not well-studied; can provide interesting insights into globalization
- Important to understand similarities and differences in real vs. financial integration; can advance our understanding of WTN dynamics

## Methodology
- Analyze the following network measures:
    - ND, ANND and CC for unweighted
    - NS, ANNS, and weighted CC for weighted
    - Random walk betweenness centrality

- Data:
    - Financial network formed from CPIS (Coordinated Portfolio Investment Survey) via IMF
    - Trade taken from UN Comtrade
    - Sample size only 61-65 countries but accounts for 80% of world trade
    - Treat network as undirected

## Results

- Reciprocity of networks: 96% for world trade, 75% for financial flows
- Density of networks:
    - WTN more integrated; 98% density for WTN, 62% to 69% for different types of financial flows in WFN
    - Density increased from 2001 to 2004
    - Real markets more integrated than financial ones
    - Long-term debt denser than short-term debt and equities (25-30% density only)
- Degree distribution:
    - IFN bimodality; "elite" of countries with many connections
    - Node strength paints a different picture; both peak at low strengths with very few strong connections
    - *Node disparity* low and stable for WTN, larger for WFN (lower = more homogeneous links)
    - Node disparity lower than a random graph
    - May imply that the benefits of trading with more countries (e.g. economies of scale, comparative advantage) lead to more diverse trade
- ANNS-degree correlation
    - Goyal and Van der Leij (2006): networks characterized by skewed degree distribution (a few nodes which are well-connected) and positive strength-degree distribution (nodes which are well-connected have strong connections) are core-periphery networks
    - IFN positive ANNS-degree correlation; well-connected countries are connected to well-connected countries; well-connected countries have strong connections
- Assortativity
    - Negative ANND-ND and ANNS-NS correlation in both cases
- Clustering
    - Binary clustering almost 1; weighted clustering low
        - Not surprising given high heterogeneity among link strengths; for high weighted CC, all three links have to be strong
    - High correlation between weighted CC and NS: major financial hubs more clustered
    - Statistically significant, i.e. higher compared to null model
    - Rich club coefficient shows that small group of countries command most international flows:
        - Top 10 countries account for 40% of trade in goods and 60% of flow in financial assets
- Centrality
    - RWBC distributed by power law, top 10% of RWBC countries are part of rich core
    - Same central core for ITN and IFN except Luxembourg (core financially but not in trade)