# Chapter 5. Network Models

This document is a note summarizing the core models used to explain the origins of real-world network properties based on chapter 5 of ***A First Course in Network Science***, utilizing Python's `NetworkX`.

## 1. Random Networks (Erdős-Rényi / Gilbert Model)

A baseline model where links are placed between nodes completely at random.

* **Density and Degree:** The model connects any pair of $N$ nodes with a uniform link probability $p$. The expected number of links $\langle L \rangle$ and average degree $\langle k \rangle$ are:

$$\langle L\rangle=\frac{pN(N-1)}{2}$$

$$\langle k\rangle=p(N-1)$$

* **Degree Distribution:** The degrees of nodes follow a binomial distribution (a bell-shaped curve) strongly concentrated around the average degree $\langle k \rangle$. Because large deviations are extremely unlikely, this model **fails to generate hubs**.

* **Short Paths:** Random networks successfully reproduce the small-world property. The maximum distance (diameter) $l_{max}$ grows very slowly (logarithmically) with the network size $N$:

$$l_{max}=\frac{\log N}{\log k}$$

* **Clustering:** The expected clustering coefficient is roughly equal to $p$. Since real networks are sparse, $p$ is tiny, meaning random networks generate almost no triangles, failing to replicate the high clustering seen in real social networks.

<br/>

## 2. Small Worlds (Watts-Strogatz Model)

A model designed to simultaneously explain both the short paths and high clustering observed in real networks.

* **Mechanism:** Start with a regular ring lattice where each node is connected to its $k$ nearest neighbors (guaranteeing high clustering but long paths). Then iterate through every link and rewire one of its endpoints to a randomly chosen node with probability $p$.
* **Shortcuts and the "Sweet Spot":** Even a tiny fraction of rewired links ($0.01 < p < 0.1$) act as "shortcuts" that bridge distant parts of the network. This drastically shrinks the average path length to resemble a random network, while leaving enough of the original lattice intact to maintain a high clustering coefficient.
* **Limitation:** Like the random network model, the degree distribution remains highly concentrated. It cannot explain the extreme degree heterogeneity (hubs) of real networks.

<br/>

## 3. Configuration Model & Exponential Random Graphs

Models that generate networks subject to specific structural constraints.

* **Configuration Model:** Generates a random network that perfectly matches a pre-defined sequence of node degrees. Each node is assigned a number of "stubs" (half-links) equal to its desired degree, which are then randomly paired to form links.
* **Degree-Preserving Randomization:** This model is widely used as a "null model." By shuffling a real network's links while keeping its degree sequence intact, researchers can test if properties like high clustering are simply a byproduct of the degree distribution or driven by other hidden mechanisms.
* **Exponential Random Graphs (ERGs):** A broader class of models that generate networks satisfying specific constraints (e.g., forcing a certain average number of triangles) while maximizing randomness in all other aspects.

<br/>

## 4. Preferential Attachment (Barabási-Albert Model)

A model that explains the emergence of hubs and heavy-tailed (power-law) degree distributions.

* **Two Key Ingredients:**
  * **Growth:** Unlike static models, the network grows over time as new nodes are added one by one.
  * **Preferential Attachment:** New nodes prefer to connect to existing nodes that already have many links ("the rich get richer," or the Matthew effect).
* **Link Probability:** The probability $\Pi$ that a newly added node $i$ connects to an existing node $j$ is strictly proportional to $j$'s degree:

$$\Pi(i\leftrightarrow j)=\frac{k_{j}}{\sum_{l}k_{l}}$$

* **Limitations:** While successful at generating hubs, the BA model has drawbacks: the oldest nodes are always the biggest hubs, the clustering coefficient is too low, and it unrealistically assumes that new nodes possess global knowledge of every other node's exact degree.

<br/>

## 5. Advanced Preferential Models

Extensions created to overcome the limitations of the classic Barabási-Albert model.

* **Attractiveness Model (Price's Model):** Solves the "zero-degree pitfall" by adding a constant attractiveness $A$ to the degree, allowing nodes to receive their first link and enabling tuning of the distribution's slope:

$$\Pi(i\leftrightarrow j)=\frac{A+k_{j}}{\sum_{l}(A+k_{l})}$$

* **Fitness Model (Bianconi-Barabási):** Assigns an intrinsic fitness value $\eta$ to each node, representing its inherent appeal. High fitness allows latecomers (e.g., Google) to accrue links faster and overtake older nodes to become hubs:

$$\Pi(i\leftrightarrow j)=\frac{\eta_{j}k_{j}}{\sum_{l}\eta_{l}k_{l}}$$

* **Random Walk Model (Triadic Closure):** A new node attaches to a randomly chosen old node, and then with probability $p$, attaches to that node's neighbors. This implicitly mimics preferential attachment (yielding hubs) while heavily boosting triangle formation (yielding high clustering and communities).

* **Copy Model:** New nodes copy the connections of existing nodes (e.g., a new webpage copying links from a hub directory, or a researcher citing a paper's bibliography).

* **Rank Model:** Instead of requiring exact degree values, the probability of receiving a link is based on a node's relative ranking $R$:

$$\Pi(i\leftrightarrow j)=\frac{R_{j}^{-\alpha}}{\sum_{l}R_{l}^{-\alpha}}$$

  *(Note: This reflects realistic scenarios, such as users clicking top search engine results, where only relative popularity is known.)*
