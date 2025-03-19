---
id: roj8za85govp2tda1mkle04
title: Trade Structure and Economic Growth
desc: ''
updated: 1739766190387
created: 1739613142787
---
### Kali et al.

The "structure of trade" - a country's number of trade partners, the concentration of their trade partners, etc. - can be used to predict its rate of economic growth, and is just as informative of a variable as the actual trade volume.

****

## Literature review

- How does trade affect economic growth?
    - Econometric analysis has involved export/import volumes, tariffs, measures of "trade openness" etc.
    - However, little attention has been given to **trade strategies**: the selection of trade partners, the trade agreements established (130 reported to WTO in last decade)
    - The structure of trade has changed in more pronounced ways than the volume of trade:
        - Proportion of trade to GDP increased from 58.3% to 88.5%, 1970-2003
        - Avg. number of trading partners **more than doubled** (46.4 to 93.9 in same period)
        - **Trade concentration **(Herfindahl index) decreased from 2201 to 1580 -> less reliant on any one trade partner, more diversified
    - Do changes in trade structures affect economic growth?
        - **Variables used**: number of trading partners of a country, **concetration of trade** -> GDP growth rate
        - **Dataset**: 1980-2000, 155 countries
        - **Results**:
            - No. of trading partners positively correlated with GDP growth
            - Trade concentration also positively correlated, but mostly for poorer countries
- Previous studies on trade and GDP growth
    - Trade openness: Dollar 1992, Sachs and Warner 1995, Wacziarg 1998
        - **Trade openness** is defined as the ratio of total trade volume to GDP for a country
    - Increases in trade productivity as a result of trade openness: Coe and Helpman 1995, Keller 1998, Edwards 1998

## Methods

### Theoretical background

- Trade increases productivity via technological diffusion:
    1. Trade generates knowledge spillovers that expand no. of goods, production processes, or ideas known to the local market -> increased productivity
    2. Trade generates competition and forces innovation & expands market of potential buyers
- How does the structure of trade affect such mechanisms?
    - Hypothesis: more trading partners -> more ideas exposed and more technological diffusion, ceteris paribus; also more potential buyers, greater innovation, more competition -> more productivity (Vickers and Yarrow 1991)
    - Additional trade partners:
        - Marginal benefit of additional trade partners may be different for poor rather than for rich countries
            - On one hand, poor countries have a small stock of knowledge and may not fully utilize new technologies
            - On the other hand, poor countries may benefit more from each new technology due to their limited existing knowledge
        - Benefit of having rich trading partners may be different from having poorer partners
            - Rich partners (technologically superior) may lead to more technological diffusion effects than poor ones
        - Model explores: rich vs poor partners, marginal effects on rich and poor countries
    - Concentration of trade:
        - Hypothesis: higher concentration of trade (less diverse trading partners) has a positive effect on growth
            - Some technologies from different countries are equally efficient but different in form and incompatible (e.g. American and European electric outlets)
            - May be cost-efficient to concentrate on a few trade partners; lowers transportation costs
            - Economies of scale in small economies
        - Rich countries may benefit less from trade concentration, e.g. because they have better transportation infrastructure

### Econometric specifications
- Hypothesis: there is a relationship between trade structure and economic growth not accounted for purely in the trade volume variable
    - An increase in no. of trade partners increases growth, though this effect differs for rich and poor countries
    - An increase in trade concentration increases growth, with a smaller effect for richer countries
- Earlier econometric literature on trade and growth:
    - Levine and Renelt (1992) provides the econometric specification used in this paper:
        - Growth rate of GDP per capita $\dot{y}/y$ regressed against vector $\vec{C}$ 
        - $\vec{C}$ composed of initial per-capita income $y_0$, rate of population growth $\dot{L}/L$, secondary-school enrollment ratio, and ratio of investment to GDP
        - Trade openness is also included and is measured by ratio of total trade (exports + imports) to GDP
        - Additionally, **trade structure** information is represented by a vector $\vec{TS}$ of explanatory variables
        - The model is
        $$
        \frac{\dot{y}}{y} = \alpha + \beta \vec{C} + \phi Trade + \psi \vec{TS} + \epsilon
        $$
        with constants $\alpha, \beta, \phi, \psi$ and a country error term $\epsilon
    - Use standard ordinary least-squares of average in entire timeframe (1980-2000) or fixed-effect regression over a five-year average
    - To test robustness, use Feder (1982) alternative specification:
    $$
    \frac{\dot y}{y} = \alpha(\frac{I}{Y}) + \beta(\frac{\dot L}{L}) + \gamma (\frac{\dot X}{X}\frac{X}{Y}) + \chi \vec{TS} + \epsilon
    $$
    where $X$ denotes exports, $Y$ real output, and $I$ investment.

- **Dataset description**. Large sample of countries from 1980-2000. Variables: annual population growth (POP), real income per capita (GDP), annual GDP growth (GDP), secondary school enrollment rates (SED), investment to GDP ratio, total trade to GDP ratio, government expenditure to GDP ratio
    - Additionally incorporate trade structure variables, i.e. total number of trade partners and concentration of trade volumes among partners (DOT database from IMF)
    - Monetary value of total imports and exports used to construct Herfindahl index of trade (HHI)
    $$
    HHI = \sum_{j=1}^N (\frac{T_{ij}}{\sum_{j=1}^N T_{ij}})^2
    $$
    i.e. sum of squares of trade share of every trading partner. No. of trading partners not necessarily correlated with trade concentration. (Multicolinearity bias avoided - $R^2$ correlation between two variables is 0.14)
    - Compute number of rich partners and poor partners separately to test the hypothesis that rich partners have different effects on trade than poor ones (threshold = median GDP in 1980)

## Results

- Trade openness:
    - Pos. and significant coefficient for poor countries; positive but statistically insignificant for total sample; negative and insignificant for rich sample
- No. of trading partners:
    - Positive for all three samples; considerable magnitude for GDP growth
    - Increasing no. of trading partners by 10 increases growth by 0.52% - significant for poor countries whose annual rate of growth is 1% or lower
    - Smaller effect for poor countries than rich countries, **confirming above hypothesis**
- Trade concentration:
    - Positive and statistically significant for most of the sample; mixed evidence for rich sample
    - Poor countries: 1 standard deviation rise in HHI leads to 1.42% increase in GDP growth rate (0.32 st. dev.) for poor countries, while for rich countries it is 0.97% (0.19 st. dev.)
- Robustness:
    - Using the specifiation by Feder (1982), similar conclusions are drawn