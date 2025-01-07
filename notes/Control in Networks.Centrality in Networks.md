---
id: 4t77cc9gvku1rbfkjprdaqy
title: 'Centrality in Networks'
desc: ''
updated: 1735225870174
created: 1735063965233
nav_order: 1
---
## Interpreting group ownership model as centrality
- <span style="background-color: #03cafc; color: black;">Definition</span>. *Centrality* is a notion in network analysis that refers to the importance of a node, which can be defined in several ways:
1. *Recursive centrality*. We expect the centrality (importance) of a node to depend on the importance of the nodes it is connected to; as such, we have
$$
c_i = \sum_{j}A_{ij}c_j
$$
where $A$ is some adjacency matrix for the network. Alternatively, we can write this in matrix form as 
$$
c = Ac
$$
<span style="background-color: #ffb812; color: black;">Interpretation</span>. $c$ is an eigenvector of $A$ with corresponding eigenvalue $\lambda = 1$: $\lambda c = Ac$.

2. *Bonacich eigenvector centrality*. Using the eigenvector equation $\lambda c = Ac$, we have
$$
c_i = \frac{1}{\lambda}\sum_{j}A_{ij} c_j
$$
with solution
$$
c=(\lambda  I - A)^{-1}e
$$
where $e$ is a column vector of ones.

3. *Hubbell index*. In addition to the above definition $c = Ac$, we also assume that each node has an intrinsic importance denoted by the vector $c^0$, yielding
$$
c^H = Ac^H + c^0
$$
where $c^H$ is the Hubbell index. We can also generalize the above two indices to yield the *$c(\alpha, \beta)$*-centrality measure:
$$
c(\alpha, \beta)=\sum_{j} (\alpha + \beta c_{ij})A_{ij}
$$
<span style="background-color: #bc42f5; color: black;">Observation</span>. The definition of the Hubbell index is identical to the definition of network value $v^{net}$ in a group ownership network:
$$
v^{net} = Wv^{net} + v
$$
replacing $c^H$ with $v^{net}$ and the intrinsic importance $c^0$ with the intrinsic value of firms $v$. 

- <span style="background-color: #ffb812; color: black;">Interpretation</span>. The indices $\nu^{int}$ and $v^{net}$ - integrated value and network value, respectively - are measures of centrality for a group ownership network; $\nu^{int}$ takes into consideration the importance of a firm's connected firms, while $v^{net} = \nu^{int} + v$ takes into account the intrinsic value in addition.
- <span style="background-color: #12ffd7; color: black;">Model</span>. For a group ownership network, we have $\bar{v}^{net}$ and $\bar{\nu}^{int}$ as metrics of centrality that correct for the excessive importance bestowed upon firms due to self-loops and the accumulation of importance towards root nodes.


