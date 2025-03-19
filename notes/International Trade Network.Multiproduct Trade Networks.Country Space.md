---
id: ftah6ge9ih25429p49ig2hh
title: Country Space
desc: ''
updated: 1742121027432
created: 1742035825281
---
### Nomaler and Verspagen 2022

The authors propose the idea of a Country Space to complement [[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]]. 

## Literature review
- Product space introduced by [[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]]
- This paper extends product space in four ways:
    - The introduction of a "country space"
    - Testing the loss of comparative advantage
    - New measures of relatedness
    - Non-parametric test based on bootstrapping
- Product space relevant because it links development and trade diversification, e.g. Coniglio et al. 2021, Hausmann and Rodrik 2003
- However, diversification and specialization are different and even contradictory concepts: a country cannot have RCA in all products by definition
    - If new specializations are added, old ones will vanish
    - 59 countries have more losses than gains in RCA out of 155 from 2012 to 2018
    - China gained 367 but loss 224
- Empirical evidence justifies product space
    - [[International Trade Network.Multiproduct Trade Networks.The Product Space Conditions the Development of Nations]] introduce the density measure and use a $t$-test to show that new specializations can be indicated by density; also conduct an OLS regress to justify the same point
    - This is followed by Boschma and Capone (2015, 2016); Bahar et al. (2017); Alsonso and Martin (2019) on Mexico; Guo and He (2015) on industrial employment; and Coniglio et al. 2021 using a non-parametric test showing that some countries fit the Product Space hypothesis while others less so

## Methods
- Product space measures: 
    - RCA: for country $i$ and product $j$, RCA is defined
    $$
    x_{ij} = \frac{\text{$i$'s share in exporting of $j$}}{\text{$j$'s share in world exports}}
    $$
    - Matrix $X$ has elements $X_{ij} = x_{ij}$ (RCA of country $i$ in product $j$)
    - **Product proximity**:
        - Defined based on conditional probability: the proximity of two products $i$ and $j$ is the probability that a country has RCA in $i$ given that it has RCA in $j$
        - This can be calculated in matrix form as follows:
            - $k_{pq}$ is the number of countries with comparative advantage in both $p$ and $q$
            - $s_p$ is the number of countries with comparative advantage in $p$
            - Proximity $\phi_{pq} = \frac{k_{pq}}{s_{p}}$
            - Matrix of proximities $\Phi = S^{-1}XX^T$ where $S$ is the matrix with row sums of $X$ on its diagonal and zeroes everywhere else
            - $XX^T$ has elements equal to the dot product between the RCAs of $p$ and the RCAs of $q$, i.e. the number of countries that share both RCAs
    - **Density**: the proximity of a country's current export basket to a product, calculated as 
    $$
    d_{ij} = \frac{\sum_{p\ \in \text{ exports of } i} x_{ip}\phi_{pj}}{\sum_{p\ \in \text{ exports of } i}\phi_{pj}}
    $$
    i.e. the average proximity to $j$ of the products that $i$ has proximity in. This can be rewritten in matrix form as 
    $$
    D = \frac{\Phi X}{\Phi O}
    $$
    where $O$ is a matrix of only ones.

- New measures:
    - Mutually exclusive proximity
        - Measures which products a country is **not** specialized in
        - A country loses specializations at the same time it gains specializations
        - As such, some specializations are mutually exclusive: e.g. manufacturing and agriculture
        - If two products are mutually exclusive in specialization, then they are **anti-competitive**
        - Define the mutually exclusive proximity between products $p$ and $q$ as 
        $$
        b_{pq} = \frac{z_{pq}}{u_p}
        $$
        where $z_{pq}$ is the number of countries which export $q$ but not $p$, and $u_p$ is the number of countries which do not export $p$; this is equivalent to the matrix equation
        $$
        B = U^{-1}ZX^T
        $$
        i.e. $ZX^T$ is the dot product between a row of $Z$ (which is $O - X$, whose elements are $1$ if a country **does not** have RCA in a product and $0$ otherwise), and a column of $X^T$, which is the RCA matrix, and $U^{-1}$ is as above.
    
    - Combining the mutually exclusive proximity and the regular proximity gives the new RCA indicator $e_{ij}$, between country $i$ and product $j$
        $$
        e_{ij} = \frac{1}{m}(\sum_{p\ \in\ \text{exports of } i} \phi_{jp} + \sum_{q\ \in \text{ non-exports of }i} b_{jq})
        $$
        where $m$ is the total number of products. This essentially says "average of product $j$'s proximity with exports of $i$, and product $j$'s anti-proximity with non-exports of $i$".
        - This can naturally be rewritten in matrix form as 
        $$
        E = \frac{1}{m}(\Phi^T X + B^T Z)
        $$
        - The columns of $E$ sum to the original product ubiquity.
    - Define $K = \Phi - B$ as the **marginal** proximities: the proximity between two products minus their antiproximities.
    - Thus we can also rewrite
    $$
    E = \frac{1}{m}(B^T O + K^T X)
    $$
    i.e. the antiproximities of all products plus the marginal proximities to the exported products. The second term reflects the country's own specialization profile, while the first reflects an **autonomous** proximity true for all countries.
- **Country space**
    - Products move through the "country space" simultaneously as countries move through the product space
    - Country space indicators can be obtained by transposing the ubiquity matrix $S$ (ie. creating the diversity matrix)
    - A **combined space** can be produced and normalized by
    $$
    E^{Tot} =\frac{1}{r(m+n)}(B^T O + K^T X +OB^* + XK^*)
    $$
    where $B^*$ and $K^*$ are the corresponding country space indicators for $B$ and $K$, $m+n$ is the number of products plus the number of countries, and $r$ is the sum of the elements of $X$.

### Non-parametric testing

- Applied to data from 2012-2018, COMTRADE, 155 countries (> 1 million inhabitants)
- 5197 product categories
- For an indicator (proximity, antiproximity, $E$, country space, etc.) the *bootstrap test* is as follows:
    - Null hypothesis: the indicator being tested, on average, is the same for products that experienced a change in its RCA for countries from 2012 to 2018.
    1. Consider the matrix $X - X_0$, where $X$ is the RCA matrix in 2018 and $X_0$ the matrix in 2012. An entry in this matrix is 1 if the corresponding product gained RCA bby a country.
    2. Call the set of all products in $X_0$, the original RCA, the "potential gainers" - a total of $N$ products. Divide into two parts: the products which actually gained RCA, and the products which didn't. Let the number of potential gainers which actually gained RCA be $N_1$, and thus the non-gainers be $N - N_1$.
    - Split the set of potential gainers into a set of size $N_1$ and a set of size $N - N_1$ 5000 times. Each time, find the average of the indicator for the set of size $N_1$ and compare it to the average of the indicator of the actual gainers set. 
    - Define 
    $$
    p = \frac{\text{no. of times actual average $\geq$ random average}}{\text{5000}}
    $$
    as the observed confidence value.
    - This can be run for both observed gains and losses in RCA, and for a specific product, a specific country, or all products and countries. 
    - Big RCA changes are weighted the same as small RCA changes because small RCA changes are infrequent.


## Results

- Indicators have $p$-value $< 0.0001$ tested on all countries and products. 
- Indicators are far less effective on products (60% achieve $p \leq 0.1$)
- Loss of RCA harder to predict than gain.
