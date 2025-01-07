---
id: onyehjy0lt63qw4c231gnyt
title: Group Ownership
desc: ''
updated: 1734962441114
created: 1734711518155
nav_order: 1
---
## Group ownership and integrated ownership model
- <span style="background-color: #12ffd7; color: black;">(Model).</span> Group ownership.
- <span style="background-color: #03cafc; color: black;">Definition</span> (Business group). Define entities in a *business group* as a group of firms which have cross-shareholdings with one another, i.e. they own each other: e.g. $A$ owns 10% of $B$, $B$ owns 10% of $C$, $C$ owns 20% of $A$.

    - <span style="background-color: #03cafc; color: black;">Definition.</span> (External shareholder) There will also be an *external shareholder*: a firm which has direct ownership over all the firms in the group, but is not owned by the group.
    - <span style="background-color: #03cafc; color: black;">Definition</span> (Intrinsic value). Let $\mathbf{v}$ be the column vector denoting the *intrinsic value* (market cap, revenue, or some other metric) of each firm in the group
    - Let $\mathbf{d}$ be the row vector denoting the percentage of shares the external shareholder owns for each firm in the group, with portfolio value $p_{ext}=\mathbf{dv}$
    - <span style="background-color: #03cafc; color: black;">Definition</span> (Group value). The *group value* vector is defined recursively as $\mathbf{v^G} =\mathbf{W^G v^G +v}$
        - <span style="background-color: #ffb812; color: black;">Interpretation:</span> the group value of a firm is its intrinsic value ($\mathbf{v}$) plus the weighted sum of its ownership in other firms ($\mathbf{W^G v^G}$)
        - <span style="background-color: #12ffd7; color: black;">(Theorem.)</span> Reorganizing gives the solution $v^G=(I-W^G)^{-1}v$. (1)
        - We also have the group value of the external shareholder, $v^G_{ext}=v_{ext}+dv^G$ where $v_{ext}$ is the intrinsic value of the shareholder
        - We write $v^G_{tot}$ to be the vector that comprises the group value of the shareholder and the group's firms: 
        $$v^G_{tot}=\begin{pmatrix}v^G_{ext} \\ v^G\end{pmatrix}$$
        - <span style="background-color: #03cafc; color: black;">Definition</span> (Integrated ownership). **Integrated ownership** refers to the sum of the direct and indirect ownership of a shareholder in a firm. 
        - For the external shareholder in this group, let the integrated ownership be $\hat{d}$. Then we have $\hat{d}=d+\hat{d}W^G$, defined similarly as the group value vector
            - <span style="background-color: #ffb812; color: black;">Interpretation</span>: $d$ is the external ownership, and $\hat{d} W^G$ is the internal ownership (the matrix $W^G$ representing the ownership of firms within the group, weighted by the internal ownership of the shareholder over the firms $\hat{d}$)
            - <span style="background-color: #12ffd7; color: black;">(Theorem.)</span> Thus we also have $\hat{d}=d(I-W^G)^{-1}$. (2)
        - <span style="background-color: #12ffd7; color: black;">(Theorem.)</span> $\hat{d}v = dv^G$.
            - <span style="background-color: #1eff12; color: black;">(Proof).</span> $\hat{d}v=d(1-W^G)^{-1}v=dv^G$ by (1) and (2).
            - <span style="background-color: #ffb812; color: black;">Interpretation</span>: Direct ownership portfolio of shareholder over group values = integrated ownership portfolio over underlying values
        - A picture of the network this is describing:
        ```mermaid
        flowchart TB
        node_1(("Firm A"))
        node_3(("Firm C"))
        node_4(("Firm B"))
        node_2["Shareholder"]
        node_1 --> node_3
        node_1 --> node_4
        node_3 --> node_4
        node_2 -.- node_1
        node_2 -.- node_3
        node_2 -.- node_4

        ```
        
        - The issue is: this is not widely applicable - the shareholder could also be part of the group, e.g. Firm A might also own shares of the shareholder, etc.
        - How do we generalize this model?
