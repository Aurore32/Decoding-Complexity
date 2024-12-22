## Network value and integrated value
- (<span style="background-color: #03cafc; color: black;">Definition</span>.) **Integrated value**. Define the *integrated value* analogously to the *portfolio* value of a firm; recall that the portfolio value of firm $i$, $p_i$, is defined $p_i = \sum_{j=1}^{n}W_{ij}v_j$, the sum of value of each other firm $j$ in the group multiplied by the percentage ownership of firm $i$ in that firm $j$.
- **Integrated value** is simply the integrated ownership analogue to portfolio value: $\nu_i$, the integrated value of firm $i$, is defined $\nu_i = \sum_{j=1}^{n}\hat{W}_{ij}v_j$, based on the integrated ownership matrix rather than the direct ownership matrix
- In matrix form, we have $\nu_{int}=\hat{W}v=(I-W)^{-1}Wv$.
    - The integrated value is a Level 3 network measure: it fully considers both the connections between nodes (firm ownership) and the nodes themselves (the value of the firms)
    - (<span style="background-color: #12ffd7; color: black;">Theorem</span>.) $\nu_{int}$ satisfies $\nu_{int} = W\nu_{int} + Wv$. 
    - (<span style="background-color: #1eff12; color: black;">Proof</span>.) From the above equation, $(I-W)\nu_{int}=Wv$ and thus $\nu_{int}-W\nu_{int}=Wv$, $\nu_{int}=W\nu_{int}+Wv$.
    - This gives rise to the following scalar equation:
    $$
    \nu^{int}_k=\sum_{i=1}^n W_{ki}\nu^{int}_{i} + \sum_{i=1}^n W_{ki}v_{i}
    $$
    - The second term $\sum_{i=1}^n W_{ki}v_{i}$ is simply the portfolio value of firm $k$.
    - (<span style="background-color: #ffb812; color: black;">Interpretation 1</span>.) The integrated value of firm $k$ is equal to the sum of the integrated value of other firms multiplied by the ownership of firm $k$ in these firms, plus the portfolio value of firm $k$.
    - (<span style="background-color: #ffb812; color: black;">Interpretation 2</span>.) The importance of node $k$ in the graph depends on the importance of its surrounding nodes and the strength of the connections between $k$ and these nodes, as well as the value of these nodes themselves.

- (<span style="background-color: #03cafc; color: black;">Definition</span>.) **Network value**. Network value is analogous to group value defined previously: 
$$
v^{net} = Wv^{net} + v
$$
and hence
$$
v^{net}=(1-W)^{-1}v
$$
- (<span style="background-color: #ffb812; color: black;">Interpretation</span>.) We can treat a firm's network value as the portfolio of its neighbors' network values, plus its own intrinsic value. 
- Network value satisfies $Wv^{net}=\hat{W}v=\nu^{int}$ as shown in the previous sections; as such $v^{net}=Wv^{net}+v=\hat{W}v+v=\nu^{int}+v$.
- (<span style="background-color: #12ffd7; color: black;">Theorem</span>.) The network value and integrated values are related to one another by
$$
v^{net} = \nu^{int}+v
$$
- (<span style="background-color: #ffb812; color: black;">Interpretation</span>.) The network value of a firm is its underlying value $v$ plus the value gained from its integrated value $\nu^{int}$, which in turn is equal to the value gained from the underlying value of all firms reachable through indirect ownership.