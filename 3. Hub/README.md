# Chapter 3. Hubs
This document is a note summarizing the core features of hubs and network centrality based on chapter 3 of ***A First Course in Network Science***, utilizing Python's `NetworkX`.

## 1. Centrality Measures
Different ways to measure the importance or centrality of a node in a network.

* **Degree Centrality:** The number of neighbors a node has. High-degree nodes are called hubs.

* **Closeness Centrality:** The inverse of the sum of distances from a node to all other nodes. It measures how close a node is to the rest of the network:

$$g_{i}=\frac{1}{\sum_{j\ne i}l_{ij}}$$

  * Normalized closeness centrality:

$$\tilde{g}_i = (N-1) g_i = \frac{N-1}{\sum_{j \ne i} l_{ij}}$$

* **Betweenness Centrality:** Measures how often a node is traversed by the shortest paths between all pairs of nodes. It highlights nodes that act as bridges:

$$b_{i}=\sum_{h\ne j\ne i}\frac{\sigma_{hj}(i)}{\sigma_{hj}}$$


<br/>

## 2. Centrality Distributions
Statistical approaches to analyze the distribution of centrality measures in large heterogeneous networks.

* **Heavy-Tailed Distributions:** Many real-world networks have broad degree distributions spanning multiple orders of magnitude, often plotted on a log-log scale.

* **Heterogeneity Parameter ($\kappa$):** Compares the variability of the degree across nodes to the average degree:

$$\kappa=\frac{\langle k^{2}\rangle}{\langle k\rangle^{2}}$$


<br/>

## 3. The Friendship Paradox
The phenomenon where your friends have more friends than you do, on average.

* **Origin:** When sampling by nodes, each node has an equal probability. But when sampling by links (asking a person for a friend), hubs have a proportionally higher chance of being reached.
* **Impact:** The broader the degree distribution, the stronger the effect of the paradox due to super-connected hubs.

<br/>

## 4. Ultra-Small Worlds
The effect of hubs on the distances between nodes in a network.

* **Property:** Hubs drastically shrink the average distance between nodes because short paths naturally run through them.
* **Distributions:** The distribution of distances is strongly peaked at very low values, making these networks "ultra-small worlds."

<br/>

## 5. Robustness
How the removal of nodes and links affects the connectedness of the system.

* **Random Failures:** Real networks with hubs are highly robust against random node removal, as the vast majority of nodes have low degrees and their removal doesn't break the giant component.
* **Targeted Attacks:** These networks are extremely vulnerable to targeted attacks. Removing the highest-degree nodes (hubs) quickly fragments the network into disconnected components.

<br/>

## 6. Core Decomposition
A method to reveal the core-periphery structure of a network.

* **k-Core:** A maximal subnetwork where all nodes have at least degree $k$.
* **Algorithm:** Iteratively peel away (remove) low-degree nodes (shells) starting from degree 1, then degree 2, and so on, to uncover the denser inner core of the network.
