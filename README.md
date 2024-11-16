# Charging-station-siting-and-sizing

This work was conducted as part of my Ph.D. thesis and was published in the IEEE Transactions on Intelligent Transportation Systems, 2024.

Here is a short abstract of the problem:

In the past decade, the rising demand for electric vehicle (EV) charging has caused fluctuating inflows at charging stations (CSs), necessitating efficient infrastructure planning to determine optimal locations and capacities. This challenge, known as the Charging Station Siting and Sizing Problem (CSSSP), is complicated by uncertain EV inflow, limited charging ports, and unpredictable queueing times, resulting in unsatisfied charging demand. To address this, we model time-varying EV demand using statistical distributions and propose a queueing mechanism that limits waiting times to a threshold. An iterative heuristic algorithm is developed, starting with an initial port allocation and followed by a statistical approximation to estimate unmet demand. Charging ports are then intelligently reallocated to minimize dissatisfaction. The process is repeated until unmet demand is minimized. The method is validated through Monte Carlo simulations and comparative analysis.

This paper formalizes the problem of allocating chargers to potential charging stations (PCSs) in a city network under various constraints. Each PCS $i$ has a capacity $\mathcal{C}_i$ and receives EV demands $D_h^i$ at each time slot $h$, which are modeled as random variables. Chargers are allocated according to a budget of $B$, satisfying:
\begin{equation}
\begin{align}
    x_i &\leq \mathcal{C}_i, \quad \forall i \in C, \label{eq:cap_constraint}\\
    \sum_{i} x_i &\leq B, \quad x_i \geq 0, \quad \forall i \in C. \label{eq:budget_constraint}
\end{align}
\end{equation}

EVs are served on a first-come-first-serve (FCFS) basis and can stay in a PCS for a fixed time window $\tau$. The total time includes waiting and service time, after which uncharged EVs are counted as unsatisfied demands. Queue dynamics are modeled to track the state of EVs with remaining time $k$, where $k \in \{\tau-1, \ldots, 0\}$.

The objective is to minimize total unsatisfied EV demands, $\mathcal{L}_{tot}^i$, across all PCSs over a time horizon $H$. The queueing mechanism and time-dependent arrivals are used to derive unsatisfied demands dynamically while accounting for charger allocation and PCS-specific capacities.
