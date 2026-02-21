# Chapter 6. Communities

This document is a note summarizing the core concepts and algorithms for community detection in networks based on chapter 6 of ***A First Course in Network Science***, utilizing Python's `NetworkX`.

## 1. Basic Definitions

Fundamental variables and concepts used to describe communities within a network.

* **Community:** A connected subnetwork whose nodes are more densely linked to each other than to the rest of the network.
* **Internal Degree ($k_i^{int}$):** The number of a node's neighbors that are *inside* the same community.
* **External Degree ($k_i^{ext}$):** The number of a node's neighbors that are *outside* the community.
* **Internal Links ($l_c$):** The total number of links within a community $c$.
* **Cut Size:** The total number of links connecting a community to the rest of the network.

<br/>

## 2. Modularity

A quality function to evaluate the goodness of a partition of a network into communities.

* **Core Idea:** Modularity $Q$ compares the actual density of links within a community against what would be expected in an equivalent random network (null model).
* **Definition:** For a partition of a network into communities:

$$Q = \frac{1}{2L}\sum_{ij}\left[A_{ij} - \frac{k_i k_j}{2L}\right]\delta(g_i, g_j)$$

  * Note: $A_{ij}$ is the adjacency matrix, $k_i$ and $k_j$ are the degrees of nodes $i$ and $j$, $L$ is the total number of links, and $\delta(g_i, g_j) = 1$ if nodes $i$ and $j$ are in the same community, 0 otherwise. *

* **Interpretation:** $Q$ ranges from $-1$ to $1$.
  * $Q > 0.3$: Significant community structure is present.
  * $Q \approx 0$: The partition is no better than a random assignment.
  * A negative value means communities have fewer internal links than expected by chance.
* **Resolution Limit:** Modularity optimization tends to merge small communities into larger ones, failing to detect communities smaller than a scale determined by the network size.

<br/>

## 3. Community Detection Algorithms

Practical algorithms to find community structure in large networks.

### 3.1 Girvan-Newman Algorithm (Edge Betweenness)

* **Mechanism:** Iteratively removes the link with the highest betweenness centrality (the link most often traversed by shortest paths between all node pairs). Links between communities act as bridges and naturally have high betweenness.
* **Output:** A dendrogram (hierarchical tree) showing the order of link removals. The partition with the highest modularity $Q$ is selected as the best.
* **Drawback:** Computationally expensive — $O(L^2 N)$ — making it impractical for large networks.

### 3.2 Louvain Algorithm (Modularity Optimization)

A fast, greedy two-phase algorithm widely used for large-scale community detection.

* **Phase 1 — Modularity Optimization:** Each node starts in its own community. Iteratively, each node is moved to the neighboring community that yields the largest positive gain in modularity $\Delta Q$:

$$\Delta Q = \left[\frac{\Sigma_{in} + 2k_{i,in}}{2L} - \left(\frac{\Sigma_{tot} + k_i}{2L}\right)^2\right] - \left[\frac{\Sigma_{in}}{2L} - \left(\frac{\Sigma_{tot}}{2L}\right)^2 - \left(\frac{k_i}{2L}\right)^2\right]$$

  This step repeats until no move can improve $Q$.

* **Phase 2 — Community Aggregation:** Each community found in Phase 1 is collapsed into a single supernode. Links between communities become weighted links between supernodes, and links within a community become self-loops.
* The two phases repeat on the new, smaller network until modularity can no longer be improved.
* **Strength:** Scales to networks with millions of nodes and links.

### 3.3 Label Propagation Algorithm

* **Mechanism:** Each node is initialized with a unique label. Iteratively, every node adopts the label shared by the majority of its neighbors. Communities emerge as groups of nodes that converge to the same label.
* **Strength:** Extremely fast — nearly $O(N)$ — and easy to implement. Known community labels can be used as seeds for semi-supervised detection.
* **Weakness:** Results can vary across runs due to random tie-breaking.

```python
partition = nx.community.asyn_lpa_communities(G)
```

<br/>

## 4. Stochastic Block Model (SBM)

A generative model approach to community detection, framing it as a model-fitting problem.

* **Core Idea:** Nodes are divided into $q$ groups. The probability that two nodes are connected depends *only* on their group memberships:

$$P(i \leftrightarrow j) = p_{g_i g_j}$$

* **Stochastic Block Matrix:** The connection probabilities form a $q \times q$ matrix. For an assortative community structure, diagonal entries (within-group probabilities) are high, and off-diagonal entries (between-group) are low.
* **Community Detection:** Given a real network, the best-fitting SBM parameters are inferred. The group assignments that produce the model most resembling the observed network reveal its community structure.
* **Advantage over Modularity:** SBM is not subject to a resolution limit and can detect both assortative (dense internal links) and disassortative (sparse internal links) community structures.

<br/>

## 5. Benchmarking Community Detection

Standard methods to test and compare the performance of community detection algorithms.

* **Planted Partition Model:** A synthetic network with a known ground-truth community structure is generated, and algorithms are evaluated on how well they recover it.
* **LFR Benchmark:** A more realistic benchmark that generates networks with heterogeneous degree distributions and community sizes (following power laws), closely mimicking real-world networks.
* **Normalized Mutual Information (NMI):** A metric to compare the similarity between the detected partition and the ground-truth partition:
  * $NMI = 1$: Perfect recovery of the true communities.
  * $NMI = 0$: The detected partition is completely unrelated to the ground truth.
