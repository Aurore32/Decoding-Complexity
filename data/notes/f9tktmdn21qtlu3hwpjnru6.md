## Propagation of control in networks
- Several models have been proposed to address how control propagates along a network, from one firm to another:
    - <span style="background-color: #12ffd7; color: black;">Model 1.</span> The *weakest link* model: if $A$ controls $x\%$ of $B$, and $B$ controls $y\%$ of $C$, then the control of $A$ over $C$ is given as $\min(x,y)$. The intuition behind this is that if $x$ is the minimum, then another firm $D$ can gain more control of $C$ than $A$ by increasing its control of $B$ to more than $x\%$; if $y$ is the minimum, then another firm can gain more control of $C$ by directly increasing its control of $C$ to more than $y\%$.
        - This model becomes problematic in larger ownership structures: if an ownership chain of 10 firms exists in the network, then simply taking the weakest link would severely overestimate the extent of control
        - Furthermore, it is difficult to apply to recursive networks
    - <span style="background-color: #12ffd7; color: black;">Model 2.</span> The *integrated control* model: apply directly the formula for integrated control to ownership, with the integrated control matrix $\tilde{C}$ being defined recursively as 
    $$
    \tilde{C} = C + C\tilde{C}
    $$
    with solution
    $$
    \tilde{C}=(I-C)^{-1}C
    $$
    <span style="background-color: #ffb812; color: black;">Interpretation</span>. The formula above can be rewritten in scalar form as $\tilde{C}_{ij}=C_{ij}+\sum_{k}C_{ik}\tilde{C}_{kj}$: the sum of direct control and the control of $i$ over firm $k$, multiplied by the indirect control of firm $k$ over $j$. This indicates that control is multiplicative: $i$ indirectly controls $j$ through the control of $i$ over an intermediate firm $k$ and the control of $k$ over $j$, or $C_{ij}=C_{ik}C_{kj}$.

## The relative majority model

- <span style="background-color: #12ffd7; color: black;">Model</span>. The *relative majority* model of control.
    - General problem plaguing above 2 models: ignores the possibility of *voting blocs*, or shareholders collaborating to form coalitions and gain more control
    - Four ways to address this:
        - *Fixed rule*: uses thresholds to analyze control over a firm. Classifies leading shareholder's control into categories.
        - *H-index*: uses the index $\sum_{i} W_{ij}^2$ to quantify how concentrated ownership over firm $j$ is.
        - *Power indices*: game-theoretic indices that take into account optimal outcomes for each shareholdler to calculate whether they will form coalitions. Can be ambiguous, hard to calculate, and inextensible to integrated control.
        - *Degree of control*: denoted by $\alpha$. Basic idea is that the control of firm $i$ over $j$ depends not only on $W_{ij}$, but also on how dispersed the other $W_{kj}$ are (the H-index). Difficult to calculate for large shareholdings and also has a minimum value of $0.5$, which is incompatible with integrated ownership.
    - Any new model of control should fulfill the following properties:
        - Define a function $F(W_{ij})$ that maps ownership $W_{ij} \in (0,1]$ to control $C_{ij} =F(W_{ij}) \in (0,1]$. Both should be continuous variables.
        - Extensible to integrated control and also fulfill $\sum_{i} C_{ij} = \sum_{i}F(W_{ij})=1$.
        - Take into account coalitions/voting blocs and intuitively describe the notion of power.
        - Be computable for large networks.
    - <span style="background-color: #03cafc; color: black;">Definition</span>. In-Degree and Out-Degree.
        - **In-Degree**. A measure of the importance of incoming links to a node in a network. Traditionally, we define in-degree as simply the number of incoming links to a node, $k^{in}_j$; in weighted networks, however, we define
        $$
        s_j = \frac{(\sum_{i=1}^{k^{in}_j}W_{ij})^2}{\sum_{i=1}^{k_{j}^{in}}W_{ij}^2}
        $$
        where the denominator corresponds to the H-index defined above. Thus, the *weighted in-degree* as defined above takes into account not only the number of connections, but how concentrated they are.
        
        - <span style="background-color: #bc42f5; color: black;">Observation</span>. In an ownership network, the sum of the weights of the incoming connections $\sum_{i=1}^{k_j^{in}} W_{ij}$ is equal to $1$ by definition. Thus the in-degree is simply the reciprocal of the H-index: $s_j=\frac{1}{H_j}$. It measures how concentrated the control of firm $j$ is among shareholders.
        - **Out-Degree**. For a given node $i$ and a destination node $j$, define the measure $H_{ij}$ as
        $$
        H_{ij} = \frac{W_{ij}^2}{\sum_{l=1}^{k_{j}^{in}}W_{;j}^2}
        $$
        where the denominator again corresponds to the H-index. Intuitively, $H_{ij}$ expresses the relative importance of the link $W_{ij}$ among all of the incoming links to $j$. If $H_{ij}$ is large, then $W_{ij}$ is an important (or relatively important) incoming link of $j$.
        - <span style="background-color: #ffb812; color: black;">Interpretation</span>. In an ownership network, $H_{ij}$ represents the *fraction of control* firm $i$ has over firm $j$.
        - <span style="background-color: #03cafc; color: black;">Definition</span>. Define the **control index** of firm $i$ as 
        $$
        h_i = \sum_{j=1}^{h^{out}_i} H_{ij}
        $$
        the sum of the fractions of control of all firms $i$ owns shares in.

## Re-interpreting as a new model of control

- <span style="background-color: #12ffd7; color: black;">Model</span>. The *relative majority* model of control simply equates control to the fraction of control above:
$$
C_{ij}=H_{ij}
$$
- Upon examination, this model satisfies several of the above outlined qualities:
    - $\sum_{i} H_{ij} = 1$, allowing us to use an integrated model. 
        - Corollary: If a shareholder gains control over a firm, other shareholders will lose control.
        - $\tilde{H}$ can be calculated without problems.
    - Like $\alpha$, the degree of control model, $H_{ij}$ takes into account the concentration of shareholder ownership by including the H-index in the denominator.
        - The smaller the H-index is, the more dispersed the ownership of $j$; and the more dispersed the ownership of $j$, the more the probability that any one shareholder can attain control
    - Power has a very intuitive definition under $H_{ij}$: the importance of a shareholder relative to all other shareholders.
        - $s_j$ (the in-degree, defined above) is the extent to which a firm is controlled by other firms, while $h_j$ is the extent to which a firm controls other firms.
    - Note that this is a Level 2 measure in graph-theoretic terms: it considers the connections between nodes but not the intrinsic value of nodes themselves

> This could potentially be relevant in the context of row-stochastic matrices in economic complexity!

- <span style="background-color: #03cafc; color: black;">Definition</span>. Define *integrated control*, $\xi^{int}$, in the context of this model analogously to integrated value: 
$$
\tilde{\xi}^{int} = \tilde{C}v
$$
representing the vector that holds the economic value controlled by each firm. Define $\bar{\xi}^{int}$, $\tilde{\xi^{int}}$ and $\dot{\xi^{int}}$ analogously to $\bar{\nu}^{int}$, $\tilde{\nu}^{int}$ and $\dot{\nu}^{int}$: in other words, as the control matrix proposed by the above model $C = H$ is row-stochastic, it can be subjected to every corrective models proposed in the Ownership Networks section.

- Note that integrated control is a Level 3 measure; it combines relative majority control, a Level 2 measure determined by the weights of the links, with intrinsic value, a Level 3 measure determined by the weights of the nodes

- <span style="background-color: #03cafc; color: black;">Definition</span>. Define analogously the notion of *network control*, $c^{net} = \xi^{int} + v$:  the total economic value a firm controls in the network, resulting from a combination of its own value ($v$) and its integrated control ($\xi^{int}$). $\bar{c}^{net}$, $\dot{c}^{net}$ and $\tilde{c}^{net}$ can be substituted accordingly.

    - We want to answer two questions: (1) which firms are the most important actors in the network in terms of control, and (2) how is control distributed in the network?



