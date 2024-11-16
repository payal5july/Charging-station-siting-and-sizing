# Charging-station-siting-and-sizing

This work was conducted as part of my Ph.D. thesis and was published in the IEEE Transactions on Intelligent Transportation Systems, 2024.

Here is a short abstract of the problem:

In the past decade, the rising demand for electric vehicle (EV) charging has caused fluctuating inflows at charging stations (CSs), necessitating efficient infrastructure planning to determine optimal locations and capacities. This challenge, known as the Charging Station Siting and Sizing Problem (CSSSP), is complicated by uncertain EV inflow, limited charging ports, and unpredictable queueing times, resulting in unsatisfied charging demand. To address this, we model time-varying EV demand using statistical distributions and propose a queueing mechanism that limits waiting times to a threshold. An iterative heuristic algorithm is developed, starting with an initial port allocation and followed by a statistical approximation to estimate unmet demand. Charging ports are then intelligently reallocated to minimize dissatisfaction. The process is repeated until unmet demand is minimized. The method is validated through Monte Carlo simulations and comparative analysis.

## Problem Description

This section formalizes the problem of allocating chargers to potential charging stations (PCSs) in a city network under various constraints. Each PCS `i` has a capacity `𝒞ᵢ` and receives EV demands `𝐷ₕⁱ` at each time slot `h`, which are modeled as random variables. Chargers are allocated according to a budget `𝐵`, satisfying:

- `xᵢ ≤ 𝒞ᵢ` for all `i ∈ 𝒞` (capacity constraint),
- `Σᵢ xᵢ ≤ 𝐵` and `xᵢ ≥ 0` for all `i ∈ 𝒞` (budget constraint).

EVs are served on a first-come-first-serve (FCFS) basis and can stay in a PCS for a fixed time window `τ`. The total time includes waiting and service time, after which uncharged EVs are counted as unsatisfied demands. Queue dynamics are modeled to track the state of EVs with remaining time `k`, where `k ∈ {τ-1, ..., 0}`.

The objective is to minimize total unsatisfied EV demands (`𝓛ₜₒₜⁱ`) across all PCSs over a time horizon `𝐻`. The queueing mechanism and time-dependent arrivals are used to derive unsatisfied demands dynamically while accounting for charger allocation and PCS-specific capacities.

This work addresses the challenge of allocating charging ports to potential charging stations (PCSs) under capacity constraints and uncertain, time-dependent EV demands. Key contributions include:

1. **EV Queueing Model**: A time-dependent queueing model for PCSs that accounts for dynamic EV inflow, where waiting times depend on demand accumulation across time slots. Unsatisfied EVs are those uncharged within a specified waiting window, $\tau$.
2. **Statistical Approximation**: A novel approximation method estimates total unsatisfied demands using time-dependent EV inflow distributions and is validated against Monte Carlo (MC) simulations.
3. **Port Allocation Algorithm**: A heuristic algorithm minimizes total unsatisfied demands through iterative optimization, achieving near-optimal charging port distribution across PCSs.
4. **Comparison with MC Simulations**: Proposed methods are benchmarked against MC simulations for accuracy and computation time, showing comparable solutions with significantly reduced computational effort.

The paper describes a heuristic approach for allocating charging ports across potential charging stations (PCSs) in a network, based on EV demand distribution. Here's a concise summary:

1. **Objective**: Determine the optimal distribution of charging ports to minimize unsatisfied EV demand.
2. **Initial Allocation**: Ports are initially allocated using policies based on factors like average or maximum demand.
3. **Statistical Approximation**: Unsatisfied demand is estimated for a given allocation using a statistical method.
4. **Iterative Optimization**: If unsatisfied demand can be reduced, chargers are reshuffled intelligently among PCSs. The process repeats until no further reduction is possible.
5. **Output**: The final allocation identifies PCSs with non-zero assigned ports, which are selected for charging station construction. 

The methodology balances demand satisfaction with efficient resource allocation.

