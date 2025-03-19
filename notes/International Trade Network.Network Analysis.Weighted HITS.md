---
id: 79iv6ou5f8mf9b70yl3nx6t
title: Weighted HITS
desc: ''
updated: 1739274813730
created: 1738937510080
nav_order: 3
---
### Deguchi et al.

This paper presents an investigation of economic hubs and authorities of the WTN through the hyperlink-induced topic search (HITS) algorithm.

****

## Weighted HITS algorithm

> <span style="background-color: #bc42f5; color: black;">Method</span>. The **weighted HITS** (and unweighted HITS) algorithm, modeled after Google's PageRank, for assessing **hubs and authorities** in the WTN.

> <span style="background-color: #03cafc; color: black;">Definition</span>. A **hub** conventionally denotes a country which is a center of outgoing trade (lots of exports); an **authority** is a country which is a center of incoming trade (lots of imports).

- Questions:
    - What to make of the increasing trade between advanced economies (the EU, the US) and emerging economies (China)?
    - Is the US losing its position as central hub of the WTN to China?
-  Existing literature:
    - Serrano and Boguna (Topology of WTN; *see above*) - WTN a complex network
    - WTN characterized by mostly weak trade links, but a few very strongly interconnected nations
- The basic idea of weighted HITS:
    - Originally introduced by Wei and Liu in the WTN
    - Countries have higher hub scores if they export to countries with high authority scores; countries have higher authority scores if they import from countries with high hub scores - ***note the similarity to economic complexity.***
    - Wei and Liu conclude that the authority scores of the US are decreasing, and that of China and Japan are increasing up to 2000.

> <span style="background-color: #ffb812; color: black;">Interpretation</span>. A country is a strong exporter if it exports to strong importers and vice versa.


- The algorithm used is based on Google's PageRank:

> <span style="background-color: #12ffd7; color: black;">Algorithm</span>. **PageRank**.

- Basic assumption: importance of a webpage based on importance of webpages linked to it (similar to eigenvector centrality)
- The **Random Surfer** model:
    - Suppose that, in a World Wide Web with an astonishing 4 pages ($A, B, C$ and $D$) page $A$ is linked to two other pages: $B$ and $C$.
    - If a "random surfer" begins on page $A$, they will next visit page $B$ or $C$ with equal probabilities; after arriving on that page, they will visit the pages linked to $B$ or $C$ again at random, with equal probability.
    - Suppose that this information is modeled with a graph with adjacency matrix $A$, and suppose that the probability of the random surfer being on $A$, $B$, $C$ or $D$ at any time is denoted by a veector $x$.
    - At any given time-unit, the surfer's next state is given by $x_{new} = Ax_{old}$ (this is a **Markov chain**).
    - This will eventually converge to

> <span style="background-color: #12ffd7; color: black;">Theorem</span>. **PageRank eigenvector**: the solution to the equation $x = Ax$, i.e. the eigenvector corresponding to the eigenvalue $1$ of $A$, is the steady state of the PageRank vector.

Notice the similarities to eigenvector centrality!

By the Perron-Frobenius system, this is not guaranteed to converge, so we introduce a **damping factor** $d = 0.85$:
$$
A' = dA + (1-d)S
$$
where $S$ is a matrix made up of entirely $\frac{1}{n}$s (with $n$ being the total number of webpages).

Now back in the context of the WTN: suppose that $A$ is now the **binary trade matrix** ($a_{ij}=1$ if trade exists between $i$ and $j$, $0$ if not). Then the PageRank algorithm can be simply applied as
$$
A'_{ij} = d\frac{a_{ij}}{\sum_{j} a_{ij}} + (1-d)S
$$
where $S$ is as above (matrix of $\frac{1}{n}$s) and $\sum_{j} a_{ij}$ is the out-degree of $i$. This naturally converges to the eigenvector of $A'$.

> <span style="background-color: #12ffd7; color: black;">Algorithm</span>. In the context of the WTN, define the **weighted PageRank** as the above PageRank matrix with $a_{ij}$ replaced with the weight $w_{ij}$.

Now we can propose

> <span style="background-color: #12ffd7; color: black;">Algorithm</span>. The **weighted HITS** algorithm: denote the **authority** vector for the $N$ countries in the WTN at as
$$
x=[x_1\ x_2\ ...\ x_N]^T
$$
> and likewise the **hub** vector as
$$
y=[y_1\ y_2\ ...\ y_N]^T
$$

> Then, by iterating across timesteps, we define $x(t+1)$, the authority vector at the $t+1$th timestep, as
$$
x(t+1) = c(t)A^Ty(t)
$$
> where $y(t)$ is the hub vector for the $t$th timestep, and $c(t)$ a normalizing constant ensuring that the elements of $x$ sum to one. Analogously, define
$$
y(t+1) = d(t)Ax(t)
$$
> where $d(t)$ is also a normalizing constant.

We thus claim that 

> <span style="background-color: #12ffd7; color: black;">Theorem</span>. The authority vector $x$ converges to the eigenvector of $A^T A$; the hub vector $y$ converges to the eigenvector of $AA^T$.

Replacing $A$ with $W$ defines the values for the **weighted** HITS algorithm. 

## Results

- Weighted HITS is more appropriate than unweighted HITS for the WTN
    - Korea and US have similar **unweighted** HITS values; however, the magnitude of trade exports for the US is 2.87 times greater than for Korea
    - Top 20 exporters in the WTN form an almost complete network; as such, not considering weights makes their HITS values nearly the same
    - Weighted HITS represents the difference between top exporters better

- 1992-2012: center of world trade shifts to Asia, China becomes top global exporter by 2012
- Hubs and authorities during that period:
    - China rises as a hub because of its exports to the US, which is the largest weighted HITS authority
    - Korea rose from 12th to 7th as a hub by strengthening international competitiveness and replacing Japanese exports
    - Japan's currency appreciated and its exports to authorities in the WTN decreased, becoming lower-ranked as a hub ("Lost Decade")
- Weighted HITS hub value and share of country in world exports not strictly proportional; some countries have larger hub values than their share (e.g. China)

- "New Economy" in 1990s led US to become largest authority in WTN, overwhelming dominance by 2001; hegemony weakened since then
- Weighted HITS authority value also not strictly proportional to import shares

- **Hub-authority correlation** is demonstrated
    - Important hubs are usually big exporters to important authorities
    - E.g. Canada, Mexico are large exporters to the US (~80% exports are to the US); HK large exporter to China
- The rise of China as a global market
    - China + HK + Macau (Greater China) has similar values with China because internal trade is large