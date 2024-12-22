---
id: 1es5gk1mwnnbslmao0uhg3z
title: Self-Loop Problem and Refinements
desc: ''
updated: 1734840071844
created: 1734714983334
nav_order: 3
---
## Self-loop problem and refinements for group ownership

- <span style="background-color: #bc42f5; color: black;">(Problem 1).</span> Self-loops.
    - If firm $i$ owns shares in firm $j$ and firm $j$ also owns shares in firm $i$, a self-ownership loop is created: $i$ owns $j$ owns $i$ owns $j$ owns $i$...
    - This creates a magnifying effect on the final group value because group value is defined recursively: $v^G=v+Wv^G$, and if a firm owns a large part of itself indirectly then its own group value will be added onto itself
    - $v^G$ will often be much larger than $\sum v_i$, the total inherent (market) value of the firms
        - <span style="background-color: #ffb812; color: black;">Interpretation</span>: self-loops overestimate the group values of strongly connected components (SCCs).
    - This can be refined by looking at the scalar equation for the integrated ownership matrix:
    $$
    \hat{W_{ij}}=W_{ij}+\sum_{k}\hat{W}_{ik}{W}_{kj}
    $$
    which leads to self-loops due to the term $\hat{W}_{ii}W_{ij}$, where $\hat{W}_{ii}$ indicates a firm's indirect ownership of itself. We simply remove this term from the equation:
    
    - <span style="background-color: #12ffd7; color: black;">(Refinement 1.)</span> Simply write 
    $$
    \tilde{W_{ij}}=W_{ij}+\sum_{k}\hat{W}_{ik}{W}_{kj} -\hat{W}_{ii}W_{ij}
    $$
    removing the self-looped term. 
    - (<span style="background-color: #12ffd7; color: black;">Theorem</span>). In matrix notation, we write 
    $$\hat{W}=W+\hat{W}W-\text{diag}(\hat{W})W=(I-\text{diag}(\hat{W}))W+\hat{W}W$$
    where $\text{diag}(\hat{W})$ is the diagonal matrix
    $$
    \begin{bmatrix}
    \hat{W_{11}} & 0 & ... & 0 \\
    0 & \hat{W_{22}} & ... & 0 \\
    \vdots & \ddots & ... & \vdots \\
    0 & 0 & ... & \hat{W_{nn}}
    \end{bmatrix}
    $$
    - (<span style="background-color: #1eff12; color: black;">Proof</span>). This can be easily verified to be equivalent to the above refinement. 
    - Thus we have:
    $$
    (I-W)\hat{W}=(I-\text{diag}(\hat{W}))W
    $$
    or, equivalently,
    $$
    (I-\text{diag}(\hat{W}))^{-1}\hat{W}=W(I-W)^{-1}
    $$
    - (<span style="background-color: #12ffd7; color: black;">Theorem</span>.) By Baldone et al. (1998), $\hat{W}$ has solution
    $$
    \hat{W} = \text{diag}(V)^{-1}(V-I)
    $$
    where $V = (I-W)^{-1}$.

    Continuing on the above, multiplying by $v$ on both sides to the right yields:
    $$
    \begin{aligned}
        (I-\text{diag}(\hat{W}))^{-1}\hat{W}v
        &=W(I-W)^{-1}v \\
        &=Wv^G \\
        &= v^G - v

    \end{aligned}
    $$
    arriving at
    - (<span style="background-color: #12ffd7; color: black;">Theorem</span>.) The group value $v^G$, under this refinement, can be found as $(I-\text{diag}(\hat{W}))^{-1}\hat{W}v + v$. Equivalently, we can also write
    $$
    v^G=(I-\text{diag}(\hat{W}))^{-1}(\hat{W}v+(I-\text{diag}(\hat{W}))v)
    $$
    which enables the equation for $v_k^G$, the group value of firm $k = 1, 2, ..., n$:
    $$
    v^G_k = \frac{1}{1-\hat{W_{kk}}}[(\sum_{i=1}^n \hat{W}_{ki}v_i) - \hat{W}_{kk}v_k+v_k]
    $$
    $$ = \frac{1}{1-\hat{W_{kk}}}[(\sum_{i=1, i\neq k}^n \hat{W}_{ki}v_i)+v_k]
    $$
    as the matrix $(I-\text{diag}(\hat{W}))$ is purely diagonal and has an inverse equal to the inverse of its entries. 

    - If $\hat{W}_{kk}=0$, i.e. a firm does not own any shares in itself (some economists <span style="background-color: #ffb812; color: black;">interpret</span> this as owning *treasury shares*), $v_k^G$ is simply $v_k$, the value of the firm, plus the value of other firms in the group weighted by their integrated ownership by firm $k$.
    - If $\hat{W}_{kk}> 0$, the group value is larger than simply the integrated ownership-weighted sum. 
    - This refinement is due to Baldone et al. (1998)
- (<span style="background-color: #bc42f5; color: black;">Drawbacks</span>.)
    - The issue of self-loops are indeed correctly isolated by Baldone et al., but their modifications to the equation are mysterious ($\text{diag}(\hat{W})$ in particular).
    - The above equation does not actually result in smaller group values if self-loops are present, as if $\hat{W}_{kk}>0$ then $v_k^G$ still gets very large.
    - The next section will propose a simpler modification to the model that bypasses the self-loop problem.