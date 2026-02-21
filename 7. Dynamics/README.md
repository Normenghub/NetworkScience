# Chapter 7. Dynamics

This document is a note summarizing the core models of network dynamics based on chapter 7 of ***A First Course in Network Science***, utilizing Python's `NetworkX`.

## 1. Social Contagion and Influence Spreading

How ideas, behaviors, and information spread through a network, analogous to disease transmission.

* **Influencers:** A set of initially activated nodes that seed the spreading process.
* **Influence Cascade:** The chain reaction of node activations triggered by influencers. Cascades can range from local (a handful of nodes) to global (a substantial fraction of the network).
* **Two Main Classes:**
  * **Threshold Models:** A node activates if the cumulative influence from its active neighbors exceeds a threshold.
  * **Independent Cascade Models:** Each active neighbor independently tries to activate a node with some fixed probability.

### 1.1 Linear Threshold Model

A node $i$ becomes active when the total influence from its active neighbors surpasses its personal threshold $\theta_i$.

* **Influence:** The influence on node $i$ is the sum of weights from its active neighbors:

$$I(i) = \sum_{j:\text{active}} w_{ji}$$

* **Activation Condition:** Node $i$ activates if:

$$I(i) \geq \theta_i$$

<br/>

## 2. Epidemic Spreading

Mathematical models that describe how diseases spread through contact networks.

### 2.1 SIS Model (Susceptible–Infected–Susceptible)

Applies to diseases that do not confer lasting immunity (e.g., the common cold). Infected individuals recover and become susceptible again.

* **Parameters:**
  * **Infection rate ($\beta$):** Probability that a susceptible node contracts the disease from an infected neighbor at each time step.
  * **Recovery rate ($\mu$):** Probability that an infected node recovers and returns to susceptible at each time step.
* **Dynamics:** At each iteration, for each node $i$:
  1. If $i$ is susceptible: become infected with probability $\beta$ for each infected neighbor.
  2. If $i$ is infected: recover (become susceptible again) with probability $\mu$.
* **Outcome:** The infected fraction either dies out or stabilizes at an endemic equilibrium.

### 2.2 SIR Model (Susceptible–Infected–Recovered)

Applies to diseases that confer long-lasting immunity (e.g., measles, mumps). Recovered individuals cannot be reinfected.

* **Parameters:** Same infection rate $\beta$ and recovery rate $\mu$ as the SIS model.
* **Dynamics:** Infected individuals move permanently to a recovered (R) compartment upon recovery.
* **Outcome:** The infected fraction always decays to zero as individuals recover and gain immunity.

### 2.3 Epidemic Threshold

A critical condition that determines whether a disease will spread or die out. For a homogeneous network with average degree $\langle k \rangle$, the epidemic threshold is:

$$\frac{\beta}{\mu} > \frac{1}{\langle k \rangle}$$

* If the ratio $\beta/\mu$ exceeds this threshold, the epidemic spreads to a finite fraction of the population.
* If it falls below, the disease dies out quickly.
* **Effect of Hubs:** In heterogeneous (scale-free) networks, the epidemic threshold effectively vanishes as $N \to \infty$, meaning even a very weakly infectious disease can spread. Hubs act as super-spreaders.

<br/>

## 3. Opinion Dynamics and Coevolution

Models describing how opinions form and evolve, and how network structure and opinions influence each other.

* **Voter Model:** At each step, a node randomly adopts the opinion of one of its neighbors. The system eventually reaches consensus (all nodes share the same opinion).
* **Coevolution Model:** Combines *social influence* (nodes adopt neighbors' opinions) with *homophily* (nodes preferentially rewire links toward nodes sharing their opinion). At each step, for a randomly chosen edge between nodes $i$ and $j$ holding different opinions:
  1. With probability $p$ (*selection*): the link is rewired from $i$ to a randomly chosen non-neighbor with the same opinion as $i$.
  2. With probability $1-p$ (*influence*): node $i$ adopts the opinion of $j$.
* **Outcome:** The system always segregates into disconnected components of nodes sharing the same opinion. When $p \approx 0$, influence dominates and the whole network homogenizes. When $p \approx 1$, selection dominates and the initial opinion groups fragment into isolated clusters.

<br/>

## 4. Network Search and Navigation

How nodes can efficiently find targets or route information through a network without global knowledge.

* **Peer-to-Peer (P2P) Networks:** Decentralized networks where computers share files directly without a central server.
  * **Gnutella:** Used BFS-based flooding, which was inefficient and consumed excessive bandwidth.
  * **BitTorrent:** Uses a *distributed hash table* (DHT) and an *overlay network* for efficient search.
* **Distributed Hash Table (DHT):** Maps each file to a unique key via a hash function. Each node stores and routes queries for keys in its assigned range. Any node joining or leaving only requires updating its immediate neighbors.
* **Greedy Routing:** A simple local algorithm where each node forwards a query to whichever neighbor is closest to the target key. The DHT structure guarantees this always reaches the correct destination efficiently.
* **Milgram's Small-World Experiment:** Demonstrated that people can navigate social networks to reach distant targets using only local information (forwarding letters to acquaintances), confirming that short paths not only exist but are also *findable* without a map.
