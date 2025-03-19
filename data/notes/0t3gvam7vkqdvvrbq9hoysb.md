### Kali and Reyes

The authors find that a country's position and degree of integration in the WTN can explain the magnitude to which financial crises beginning in that country affect other countries; in short, a network approach based on the WTN offers a good explanation for financial contagion.

## Literature review

- Does integration into the WTN make a country more vulnerable to economic crises?
    - Having more trading partners increases both the channels through which a crisis can reach the country, and the chance for the country to find alternative trade partners to minimize the crisis
- Globalization has led to country-specific events having international consequences; even in small countries, crises can have global impacts that leave some other countries extremely affected and others not affected at all
- Focus needs to turn from bilateral trade to the entire network of trade, enabled by complex network advances by Albert and Barabasi (2002) and Newman (2003); take the WTN as the backbone for representing not only flow of goods, but financial flows as well, e.g. credit, bank loans, speculation
- Trade linkages vs. financial flows?
    - Kaminsky and Reinhart, 2000, 2003; Bae, Karolyi and Stulz, 2003 emphasize financial flows in crisis propagation
    - Forbes, 2001; Forbes and Rigobon, 2001; Claessens and Forbes, 2001; Abeysinghe and Forbes, 2002 stress trade linkages
    - Empirical evidence: little direct trade between Russia and Brazil, yet Brazil impacted by Russian crisis in 1998; Argentina affected by Brazil devaluation in 1999 due to Argentina being a major trade partner
    - Difficult to separate the two; however, trade can be itself separated into different channels that affect crisis propagation differently - 
        - *Competitive effect* - changes in relative prices due to a crisis affects domestic firms' competitiveness abroad
        - *Income effect* - crisis affects incomes which affect purchasing power
        - *Cheap-import effect* - crisis reduces import prices for partners importing from country where crisis started, leading to a positive supply shock
    - Forbes and Chinn 2003 find that trade is the strongest determinant for cross-country linkages in stock and bond markets
    - Forbes and Abeysinghe 2002 find that even small trade links can have profound effects on crisis propagation due to multiplier eeffects
- Not yet considered is the presence of intermediary partners, i.e. indirect trade flows: if $A$, $B$ and $C$ form a trade triangle, then any crisis in $A$ will loop through the entire triangle through interdependent "second-order" effects
    - $A$ defaults -> $A$ can no longer supply needed goods to $B$ and $C$ -> $B$ defaults -> $B$ and $C$ are trading partners so $C$ is also affected -> $A$ is trading partners with $C$ so $A$ is affected more
- However, these second-order effects can also dampen shocks: if $A$ is connected to both $B$ and $C$, then the effect of the crisis is spread between $B$ and $C$

    
## Methods

- Consider a binary network (threshold-based): $A_{ij} = 1$ if exports from $i$ to $j$ is above a certain share of $i$'s total exports; use different thresholds to test for robustness
    - An alternative link construction is considered: exports of $i$ to $j$ divided by GDP of $i$
- Consider country-level "integration" into the WTN:
    - Degree centrality
        - Top countries (South Korea, Russia, Brazil etc.) are also epicenters of recent crises
    - Node importance (eigenvector centrality)
        - Exactly the same as network value presented in [[International Trade Network.Decoding Complexity - Glattfelder]]!
        $$
        v^{net} = Dv^{net} + v
        $$
        where $D$ is a matrix of dependencies (can be weights or alternatively defined; adjusted for robustness) and $v$ is intrinsic value of the country
        - Again, top-ranked countries are epicenters of major crises
    - Maximum flow (number of paths, direct and indirect, from a country to another country)
        - Successfully indicates countries most affected by Thai currency crisis (Brazil, Indonesia, Korea, Russia)
        - Drawback: not distance-weighted (a direct path is as important as a path of length $n$)

### Stock market analysis
- Data: NBER-UN world trade database, 1992-2000.
- Thresholds used for binary matrix are 0, 1, and 2%; 92% of trade links in 2000 are between 0 and 2%
- Non-overlapping windows considered (i.e. the next crisis is not affected by the first), as in Rigobon 2003 and Glick and Rose 1998: Mexican crisis 1994-95, Asian crisis 1997-98, Russian crisis 1998-99
- Empirical evidence for windows based on tranquility before window -> volatility after window
    - Use "exchange-market pressure index" (Forbes, 2003) based on variations of exchange rate, interest rates, and international currency reserves
    - A timeframe is identified as a crisis if the index is five, three, or 1.5 times the st. dev. away from the mean
- Rigobon (2003) traces each crisis window to an epicenter country: first $\mu + 5\sigma$ country after a tranquil window
- Econometric model used is
    $$
    SMR_{i,w} = \beta_1 NIC_{i,w} + \beta_2 NIEC_w + \sum_{k=1}^K \gamma_k Z_{k,i,w} + \epsilon_{i,w}
    $$
    where $SMR$ is the stock market performance indicator for country $i$ during crisis window $w$, $\beta_1, \beta_2, \gamma$ are parameters to be found by OLS, $NIC_{i,w}$ is a **network indicator** for country $i$ (e.g. centrality) in this window, $NIEC_{w}$ is the **network indicator** for the **epicenter country** during window $w$, and $Z_{k,i,w}$ are $k$ control variables (standard macroeconomic variables of currency, banking, and financial crises).
    - Control variables: bank reserves to assets ratio, inflation rate in CPI, GDP growth rate, current account balance, govt. expenditures, govt. budget balance, private capital flows, trade as percentage of GDP

- $\epsilon$ is a control variable for trade between country $i$ and epicenter country -> isolates network effects from direct effect of trade with epicenter

- $SMR$ (stock market indicator) calculated by considering deviation of weekly stock market return during crisis window $w$ from non-crisis average returns from Jan 1992 to Dec 1994 (last month before Mexican crisis)
    - This timeframe is characterized by stable macroeconomic conditions around the world
    - Robustness test involves different window of returns
- Dependency matrix defined either as exports from $i$ to $j$ as a share of total exports of $i$ (cash-flow dependency) or exports from $i$ to $j$ as a share of the GDP of $i$ (how much the total output of $i$ depends on $j$).

## Results

- Node importance (vector centrality) -> intrinsic value taken as world trade share of country $i$ (case 1) and degree centrality of country $i$ (case 2)
- Epicenter network indicators statistically significant; all negative (epicenter strongly integrated -> crisis has more significant effect)
    - 1 st.dev. increase in epicenter importance leads to 0.19 increase in abnormal stock returns
- Country network indicators positively affect crisis mitigation; well-integrated countries can avert crises better
- Crisis windows exceed 10 weeks on average; the cumulative effects of these indicators are substantial
- Maximum flow metrics lead to the following model:
$$
 SMR_{i,w} = \beta_1 Maxflow(\text{epicenter to $i$}) + \sum_{k=1}^K \gamma_k Z_{k,i,w} + \epsilon_{i,w}
$$
where a one st. dev. increase in maximum flow leads to a 0.075% reduction in stock market returns (signs coincide with other network indicators, but with lower magnitude).

