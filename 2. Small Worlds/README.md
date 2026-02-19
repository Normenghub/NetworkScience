# Chapter 2. Small Worlds

This document is a note summarizing the core features of real-world networks based on chapter 2 of ***A First Course in Network Science***, utilizing Python's `NetworkX`.

## 1. Birds of a Feather

Nodes in a network often connect to other nodes that share similar properties.

* **Assortativity:** The property where nodes tend to connect to similar nodes.
* **Homophily:** The tendency of similar people to select each other and become connected.
* **Social Influence:** The converse mechanism where people who are connected become more similar over time.
* **Degree Assortativity:** Networks where high-degree nodes tend to connect to other high-degree nodes, and low-degree to low-degree.
  * **Assortative Networks:** High-degree nodes (hubs) form a densely connected core.
  * **Disassortative Networks:** Hubs tend to be connected to low-degree nodes.

<br/>

## 2. Paths and Distances

Concepts and metrics used to define and measure distances among nodes in a network.

* **Path & Shortest Path:** A path is a sequence of traversed links. The shortest path minimizes the number of links traversed.
* **Average Path Length ($\langle l \rangle$):** Obtained by averaging the shortest-path lengths across all pairs of nodes.
  * For an undirected, unweighted network:
    $$\langle l\rangle=\frac{\sum_{ij}l_{ij}}{\binom{N}{2}}=\frac{2\sum_{ij}l_{ij}}{N(N-1)}$$
  * For a directed network:
    $$\langle l\rangle=\frac{\sum_{ij}l_{ij}}{N(N-1)}$$
* **Diameter ($l_{max}$):** The maximum shortest-path length across all pairs of nodes:
  $$l_{max}=max_{i,j}l_{ij}$$

<br/>

## 3. Connectedness and Components

Analyzing the physical connectivity structure of the network.

* **Components:** A subnetwork where there is a path connecting any pair of its nodes, but no path connecting them to other components.
* **Giant Component:** The largest connected component that includes a substantial portion of the network.
* **Directed Network Components:**
  * **Weakly Connected:** Components defined by ignoring the direction of the links.
  * **Strongly Connected:** Components where there is at least one directed path between every pair of nodes in both directions.

<br/>

## 4. Trees

A special class of undirected, connected networks.

* **Definition:** A connected network such that the deletion of any one link will disconnect the network into two components.
* **Properties:** Trees have no cycles, and the number of links is exactly:
  $$L=N-1$$
* **Hierarchy:** Trees are hierarchical, featuring a root, parent nodes, children nodes, and leaves.

<br/>

## 5. Finding Shortest Paths

Algorithms used to navigate and find short distances in a network.

* **Breadth-First Search (BFS):** An algorithm that navigates a network from a source node, visiting the entire "breadth" before moving to a greater "depth".
* **Shortest-Path Tree:** Built by the BFS algorithm to map the shortest paths between its root (the source) and all other reachable nodes.

<br/>

## 6. Social Distance

The phenomenon where average path lengths in real-world networks are surprisingly short.

* **Small World Property:** The popular notion that social distances are short, meaning the path length scales logarithmically with network size:
  $$\langle l\rangle \sim \log N$$
* **Six Degrees of Separation:** The idea that any two people in the world are connected by a short chain of acquaintances, popularized by Milgram's experiment.

<br/>

## 7. Friend of a Friend

The local structure capturing how tightly knit, or clustered, the network's nodes are.

* **Triangles & Triadic Closure:** A triangle is a triad where each pair of nodes is connected. Meeting people through shared contacts and closing these triangles is triadic closure.
* **Node Clustering Coefficient ($C(i)$):** The fraction of pairs of a node's neighbors that are connected to each other:
  $$C(i)=\frac{\tau(i)}{\tau_{max}(i)}=\frac{\tau(i)}{\binom{k_{i}}{2}}=\frac{2\tau(i)}{k_{i}(k_{i}-1)}$$
* **Network Clustering Coefficient ($C$):** The average of the clustering coefficients across all valid nodes:
  $$C=\frac{\sum_{i:k_{i}>1}C(i)}{N_{k>1}}$$
