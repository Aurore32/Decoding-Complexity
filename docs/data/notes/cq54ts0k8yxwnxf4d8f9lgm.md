## Generalized group ownership model
- <span style="background-color: #12ffd7; color: black;">(Model).</span> Generalized group ownership model.
    - <span style="background-color: #bc42f5; color: black;">(Generalization 1.)</span> formalizing the shareholder into the matrix equation
        - If we include the shareholder in the adjacency matrix $W$, then $W$ can be expressed as
        $$\begin{bmatrix}0 & d_1 & d_2 & \cdots & d_n\\
        0 & W_{11} & W_{12} & \cdots & W_{1n} \\
        \vdots  & W_{21} & \ddots & \cdots & W_{2n} \\
        \vdots & \vdots & \vdots & \ddots & \vdots \\
        0 & W_{n1} & W_{n2} & \cdots & W_{nn} \end{bmatrix}$$
        - The first column is entirely zero because it represents the ownership of the group of firms over the shareholder, which they do not own at all. The first column is $d_1, d_2, ... = d$, the row vector representing the ownership of the shareholder over the group.
        - The remaining parts of the matrix remains the same as the original adjacency matrix $W^G$.
        - Now $v$ also contains the value of the shareholder.
        - This allows us to write directly: $v^G = (I-W)^{-1}v$ as before, except now the group value vector contains the group value of the shareholder.
        - Generalizing (2) from above, we also have $\hat{W}=W+\hat{W}W$ where $\hat{W}$ is the integrated ownership matrix of the shareholder plus every other firm.
            - <span style="background-color: #ffb812; color: black;">Interpretation:</span> in scalar form this can be written $\hat{W_{ij}}=W_{ij}+\sum_{k}W_{ik}\hat{W}_{kj}$ - the integrated ownership of a firm is the direct ownership $W_{ij}$ plus the integrated ownership of every firm towards firm $j$, weighted by the directed ownership of firm $i$ towards those firms. 
            - <span style="background-color: #12ffd7; color: black;">(Theorem.)</span> $\hat{W}=W(1-W)^{-1}$. Perron-Frobenius theorem ensures this matrix inverse exists 
            - <span style="background-color: #12ffd7; color: black;">(Theorem.)</span> $Wv^G=\hat{W}v$ and thus $v^G = Wv^G+v=\hat{W}v+v$.
                - (<span style="background-color: #1eff12; color: black;">Proof</span>.) $\hat{W}v=W(1-W)^{-1}v=Wv^G$.
                - <span style="background-color: #ffb812; color: black;">Interpretation</span>: the group value weighted by the direct ownership percentages, $Wv^G$, is equal to the intrinsic value weighted by the integrated ownership percentages, $\hat{W}v$.
    - <span style="background-color: #bc42f5; color: black;">(Generalization 2).</span> Integrating the shareholder into the business group.
        - The shareholder may also be owned by a firm in the group, i.e. the shareholder may also be part of the group.
        - Formally, this would mean that the first column of the adjacency matrix of the group is nonzero: in the following adjacency matrix of the group
        $$\begin{bmatrix}W_{11} & W_{12} & ... & W_{1n} \\
        W_{21} & W_{22} & ... & W_{2n} \\
        \vdots & \ddots & ... & \vdots \\
        W_{n1} & W_{n2} & ... & W_{nn} \end{bmatrix}$$
        The term $W_{ij}$ represents the direct ownership of firm $i$ in firm $j$, and if we take firm $1$ to be the shareholder, then all $W_{i1} \neq 0$.
    - This model faces a range of problems, as detailed in the following note.