---
id: 0rd28f46hgm9exbxx6bipil
title: Models of Control
desc: ''
updated: 1735227978247
created: 1735225879966
nav_order: 2
---
## Control in ownership networks
- How do we interpret control in ownership networks?
- <span style="background-color: #03cafc; color: black;">Definition</span>. While *ownership* is an objective quantity referring to the percentage of shares in another firm a firm owns, *control* is a subjective measure of the influence a firm has over another firm.
    - This is typically understood in terms of *voting rights*: a firm owning shares to another firm represents ownership of *cash-flow rights*, which translates into the right to vote at shareholder meetings
    - The relationship between cash-flow rights and voting rights is key to understanding control in ownership networks
- <span style="background-color: #12ffd7; color: black;">Model</span>. The *flow of control* model.
    - Existing literature refers primarily to *direct control*: control derived from a firm directly owning shares in another firm
    - This model will provide an analogy to integrated ownership and introduce the notions of *integrated control*, which not only take indirect ownership into account but also represent the *flow of control* (see "Flow in Ownership Networks")
    - All the following proposed models seek to transform the ownership matrix $W$ via some equation into the control matrix $C$:
    $$
    W \to C
    $$
- <span style="background-color: #12ffd7; color: black;">Model 1</span>. "One-Share-One-Vote" Rule. According to this model, share ownership is directly proportional to voting rights; we simply have
$$
W_{ij} = C_{ij}
$$
- <span style="background-color: #12ffd7; color: black;">Model 2</span>. Threshold model. 
    - If a firm is the majority shareholder of another firm, one would expect it to hold a monopoly on voting decisions; it holds all the control, while other shareholders hold none
    - Define a *threshold* $\theta$ such that if $W_{ij} > \theta$, $i$ is deemed to hold all the control over $j$: $C_{ij} = 1$.
    - This threshold has been varyingly set to 50% (more conservatively), or 10%, or 20% (more loosely)
    - However, if no firm exceeds this threshold, then no shareholder holds absolute control
    - Thus we have:
    $$
    \begin{cases}
    C_{ij} = 1,\ W_{ij} > \theta \\
    C_{ij} = 0,\ W_{ij} < \theta \text{ and } W_{kj} > \theta \text{ for some other firm $k$} \\
    C_{ij} = W_{ij} \text{ otherwise}
    \end{cases}
    $$
    - Essentially:
        - If a firm's ownership exceeds a threshold, it has complete control (1)
        - If it does not exceed the threshold and another firm exceeds the threshold, it has no control at all (0)
        - Otherwise, if no firms exceed the threshold, all firms have some control proportional to their ownership (as in Model 1).
- <span style="background-color: #03cafc; color: black;">Definition</span>. Define the *control value* of a firm $i$ in the ownership value, $c_{i}$, as
$$
c_i = \sum_{j} c_{ij}v_j
$$
the weighted sum of the value of the firms $i$ owns shares in, weighted by the control of $i$ over them. This provides a measure of the amount of economic value controlled by $i$.

