---
id: z5zud4p7rwge0azpdqgonwk
title: Thoughts on Economic Complexity
desc: ''
updated: 1735297561667
created: 1735288465505
nav_order: 1
---
## Summarizing complex networks

### <span style="background-color: #12ffd7; color: black;">1.</span> The basic model
- *Ownership networks*. Networks where each node is a firm that can own shares in other firms of the group. The adjacency network of the group, $W = [W_{ij}]$, denotes the share of ownership between any two firms. This leads to:
- *Direct ownership* and *indirect ownership*. Direct ownership denotes, e.g. firm $A$ directly being connected to firm $B$, while indirect ownership denotes firm $A$ reaching firm $B$ through a series of connections. 
    - Direct ownership is provided simply by the adjacency matrix  $W$
    - Indirect ownership (integrated ownership) $\tilde{W}$ is provided by the recursion $\tilde{W} = W + W\tilde{W}$
- Similarly define:
- *Direct value* (portfolio value) and *indirect value* (integrated value).
    - Portfolio value, $p$: value of shares a firm directly owns. We have $p=Wv$ 
    - Integrated value, $\nu^{int}$: value of shares a firm indirectly owns. We have $\nu^{int} = \tilde{W}v$, leading to...
    - Network value, $v^{net}$: a firm owns itself, so network value is integrated value plus a firm's own value. $v^{net} = \nu^{int} + v$.

### <span style="background-color: #12ffd7; color: black;">2.</span> Problem 1: Self-loops and improvements
- Self-loops (A owns B, B owns A) lead to overestimations in integrated (indirect) value due to its recursive definition
- Examine $\nu^{int}$ for a firm $i$: $\nu^{int}_i = \sum_{j} \tilde{W}_{ij}v_j$
    - The solution is to remove the portion which represents the ownership of $i$ in itself, $\tilde{W}_{ii}$.
- In matrix form, this was found to be equivalent to multiplying $\nu^{int}$ by a *correction operator* $D = (\text{diag}(I-W)^{-1})^{-1}$.
- Similarly correct $v^{net}$ by setting $Dv^{net}$, and $\tilde{W}$ by setting $D\tilde{W}$. Thus we have a series of corrections:
$$
\begin{cases}
\hat{v}^{net} = Dv^{net} \\
\hat{\nu}^{int} = D\nu^{int} \\
\hat{W} = D\tilde{W}
\end{cases}
$$

### <span style="background-color: #12ffd7; color: black;">3.</span> Problem 2: Root node accumulation and improvements
- **Interpretation in terms of flow**. Integrated value $\nu^{int}$ is a representation of flow in networks. This can be mathematically proven, but intuitively, it is because the integrated value represents how much economic value a firm owns because of its ownership of shares in other firms. Thus, it is how much value *flows* to a firm from other firms.
- The *bow-tie* problem. Ownership networks often assume a bow-tie shape with IN nodes, OUT nodes and a strongly-connected component (SCC). IN nodes own the SCC but are not owned, the SCC's firms own each other, and OUT nodes are owned by firms in the SCC but do not own any firms.
    - As IN nodes own shares but are not owned in return, value flows to them while no value flows from them. This will lead to an accumulation of value into IN nodes, and an excessive overestimation for $\nu^{int}$ and $v^{net}$.
- To solve this, note that **two** corrected values originate from the correction operator $D$: $\hat{W}=DW$, and due to the non-commutativity of matrix multiplication, $WD$.
    - From $WD$, we have $\bar{v}^{net} = WDv^{net} + Dv$ where $v^{net}$ is the uncorrected network value. (This is opposed to $DWv^{net} + Dv$, which is $\hat{v}^{net}$).
    - SImilarly, we have $\bar{\nu}^{int} = WDv^{net}$.
- This correction has the issue of **computation speed**: it runs in $O(n^3)$. Thus an algorithmic correction based on breadth-first search (BFS) is also proposed:
    - General algorithm $(*)$: run BFS on a node to find all nodes reachable from it. This will form a sub-network of the ownership network. Remove all links coming back to $i$ (this is mathematically proven to be equivalent to the self-loop correction). Find the network value of this sub-network.
    1. Run $(*)$ on OUT.
    2. Run $(*)$ on all nodes in the SCC connected to OUT. Add the network values of those nodes to their intrinsic values $v$.
    3. Run $(*)$ on the SCC.
    4. **Root node correction**. **Do not** run $(*)$ on all nodes of IN directly connected to the SCC, but instead have their network values directly equal the weighted sum $\sum_{j}W_{ij}v^{net}(j)$. Add the network values of those nodes to their intrinsic values $v$.
    5. Run $(*)$ on IN.

![alt text](image-3.png)

### <span style="background-color: #12ffd7; color: black;">4.</span> Centrality and control
- Integrated value and network value can be interpreted as measures of centrality, which is similarly defined recursively as 
$\tilde{C} = W\tilde{C} + C_0$. (Centrality of a node depends on centrality of nodes connected to it weighted by strength of connection, plus some intrinsic centrality $C_0$).

- This improves upon the existing literature through $\hat{v}$ and $\bar{v}$, which solve self-loops and root node accumulation.

- **Control** refers to a firm's voting rights over another firm in shareholder meetings. Let $C$ denote the control matrix $[C_{ij}]$, where $C_{ij}$ is the control of $i$ over $j$.  Several models of control were proposed:
    - Direct equivalence: $W = C$ where $W$ is the adjacency matrix of the network. Essentially, ownership = control.
    - Threshold model: if $W_{ij}$ exceeds a certain threshold (10%, 20%, 50$ etc.), $C_{ij} = 1$; otherwise it is 0.
    - Degree of control: control should depend on how concentrated a firm's shareholders are. If one big shareholder, then that shareholder has all the control and all other firms have none; if many small shareholders, then even if $W_{ij}$ is small then it is possible to have a large amount of control. Thus define the H-index
    $$
    H_{j} = \sum_{i} W_{ij}^2
    $$
    which measures the concentration of shareholders of firm $j$. 
- The paper proposes the new model $C_{ij}=\frac{W_{ij}^2}{H_j}$, or the proportion of the control of $i$ over $j$ over total control. This has the benefits of:
    - $C_{ij}$ sums to 1, allowing us to analyze it like an ownership matrix. 
    - Takes into account shareholder concentration.
    - Easy to calculate.
    - Can implement corrections $\bar{C}$ and $\hat{C}$ according to the above.
- **Overall**:
1. Analyze ownership network: adjacency matrix, find corrections -> gives information on flow of value.
2. Analyze matrix of control.
3. Analyze concentration of control using Lorenz curve.

## Analogies to economic complexity
- A striking analogy that can be made between the two models is their column-stochastic nature. The types of networks (and adjacency matrices) that the above models support are column-stochastic (rows sum to 1)
    - $\sum_j W_{ij} = 1$: proportions of shares that all firms own in $j$ sum to 1
    - Perhaps similarities with $\tilde{M}$ can be drawn