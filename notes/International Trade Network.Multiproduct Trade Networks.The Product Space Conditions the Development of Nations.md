---
id: jt4pa4l737rr7eafxhvybla
title: The Product Space Conditions the Development of Nations
desc: ''
updated: 1740391097627
created: 1740380150667
---
### Hidalgo et al.

A network of products produced around the world is constructed based on the degree of interrelatedness between these products. The authors find that such a network exhibits a core-periphery structure, and that poor countries have empirical difficulties in moving towards more sophisticated regions of this network.

****

## Literature review

- Does the type of product a country produces matter?
    - *Industrial products* are suggested to be more economically beneficial than agriculture due to spillover effects (i.e. production of industrial products leads to industrialization, which leads to growth)
- However, this notion has not been formalized; instead, the **level of development** of a country's specialization in products has been studied through
    - **Factor proportions**: ratios between a country's capital, labor, land, etc. Poor countries are unskilled-labor and land heavy; rich countries are capital heavy.
    - **Technological differences**: products are differentiated by the level of technology required to produce them. A country becomes more developed when it moves to a more technologically advanced product.
- **Traditional growth theory** posits that countries develop by moving to more advanced products, and that such a redeployment of resources (land, labor, capital) is always possible
    - However, if the **distance** between certain products are too large, then such a redeployment would be very difficult
    
## Methods

- **Relatedness of products** can be measured in several ways:
    - Proportion of land, labor, and capital needed to produce them
    - Level of technological sophistication
    - Inputs/outputs involved in the product's value chain
    - Requisite institutions for producing the product
- Instead, they can also be measured by looking at how much they are produced together
    - E.g. countries who produce apples probably produce pears, and it can be concluded that they are similar products
- Based on this, we have

> <span style="background-color: #12ffd7; color: black;">Model</span>. **Product proximity** between products $i$ and $j$.

First define the metric

> <span style="background-color: #03cafc; color: black;">Definition</span> RCA (**revealed comparative advantage**) of a country $c$ in the production of product $i$ is given by 
$$
RCA_{c,i} = \frac{\text{proportion of $i$ in country $c$'s exports}}{\text{proportion of exports of $i$ in total world exports}}
$$
> or, mathematically,
$$
RCA_{c,i} = \frac{(\frac{x(c,i)}{\sum_{i}x(c,i)})}{(\frac{\sum_{c}x(c_i)}{x_{total}})}
$$

A country will have an RCA above 1 for product $i$ if it exports more of product $i$ than is expected (i.e. than the world average proportion of exports of $i$ vs. all exports). We expect two products to be **closely related** if they are produced at the same time, or if they are not produced by the same time, in a single country; thus, define product proximity $\phi_{ij}$ between $i$ and $j$ as either
$$
P(RCA_{x,i} \geq 1 | RCA_{x,j} \geq 1)
$$
or
$$
P(RCA_{x,j} \geq 1 | RCA_{x,i} \geq 1)
$$
whichever value is smaller, i.e. for all countries, what is the probability that $i$ is a widely produced product given that $j$ is widely produced? 

## Results

- The product proximity of 775 product classes were studied and formed into a network, referred to as the **product space**
- **The product space is clustered**. Hierarchical clustering shows that products form several groups, with products within each group being close in proximity and products beetween groups being far away.
- **The product space has a core-periphery structure**, with industrial productsa nd chemicals being at the core, agriculture and textiles at the left periphery, and electronics and mining at the right
- Leamer (1984) performs a similar clustering with relative factor intensities in product production, and obtains similar results
- **Different continents have different specialization patterns**. For instance, the Americas occupy the core (industrialized products); East Asia occupies the peripheries, e.g. garments and textiles; Africa occupies the far peripheries

### Diffusion of products

- **Countries export new products close in proximity to already-exported products**. Studies of Malaysia and Colombia's product spaces between 1980 and 2000 reveal a **diffusion process** in which the countries tend to produce new products that are closer to existing goods.
- To test product diffusion, define

> <span style="background-color: #12ffd7; color: black;">Model</span>. **Density model of product diffusion**. Suppose that a country $c$ wants to produce a new potential product $j$ which they are not already producing. Define the **density** of the country's current production structure to $j$ as
$$
\omega^c_j = \frac{\sum_{i} x_i\phi_{ij}}{\sum_{i} \phi_{ij}}
$$
> where $\phi_{ij}$ is product proximity between $i$ and $j$, and $x_i$ is 1 if $RCA(c,i) > 1$ and 0 otherwise. Density is thus the number of products that are important to $c$ ($RCA(c,i) > 1$), weighted by their proximity to $j$. High density means that country $c$ has many products which have high proximities to $j$.

- To illustrate that a high proximity makes the production of a new good more likely, consider **transition products** from 1990 to 1995: for a country $c$, if product $i$ was **undeveloped** ($RCA(c,i)<0.5$) in 1990 but **developed** ($RCA(c,i)>1$) in 1995, then it is part of the set of transition products.

- Let $T$ be the set of countries for which a product $i$ was a transition product. Define the **discovery factor** for product $i$
 
$$
H_i = \frac{\text{average density to $i$ in transition countries}}{\text{average density to $i$ in non-transition countries}}
$$

or
$$
H_i = \frac{\frac{\sum_{j=1}^T \omega^j_i}{T}}{\frac{\sum_{j=T+1}{N}}{N-T}}
$$

- This ratio is bigger than 1 for 79% of products, showing that average density influences transitioning.

- Alternatively, upon calculating the probability of transitioning to a new product conditioned upon $\phi$, the probability is 15% if $\phi = 0.8$ but nearly zero if $\phi = 0.1$.

### Connectivity of the product space

- **The product space is sufficiently connected**. Links with proximity $\phi < 0.3$ fully connect the product space.

- A dynamical model where countries diffuse into products with $\phi > k$ for $k = 0.65$ or $0.6$ or $0.5$ finds that countries like Korea, which is positioned near the core of the product space (industrial products), diffusion is easy; while for countries like Chile, which are not in the core, diffusion is difficult and slow.
