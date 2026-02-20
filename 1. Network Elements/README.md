# Chapter 1. Network Elements
This document is a note summarizing the most basic elements and concepts of network science based on chapter 1 of ***A First Course in Network Science***, utilizing Python's `NetworkX`.

## 1. Basic Definitions
The most fundamental elements constituting a network and classifications based on direction and weight.

* **Nodes & Links:** A network (or graph) is a set of elements called nodes, along with a set of connections between pairs of nodes called links.
* **Direction:**
  * **Undirected Network:** All links are bi-directional.
  * **Directed Network (Digraph):** The link goes from a source node to a target node.
* **Weight:** A network can also be unweighted or weighted.
* **Bipartite Network:** There are two groups of nodes where links only connect nodes from different groups.

<br/>

## 2. Density and Sparsity
Metrics indicating how densely a network is connected.

* **Maximum Links ($L_{max}$):** Bounded by the possible number of distinct connections among the nodes.
  * For an undirected network with $N$ nodes:

$$L_{max}=\binom{N}{2}=\frac{N(N-1)}{2}$$

* **Density ($d$):** The fraction of possible links that actually exist.
  * For an undirected network:

$$d=\frac{L}{L_{max}}=\frac{2L}{N(N-1)}$$

  * For a directed network:

$$d=\frac{L}{L_{max}}=\frac{L}{N(N-1)}$$

* **Sparsity:** Real-world networks are typically sparse, meaning the actual number of links is much smaller than the maximum possible number.

<br/>

## 3. Subnetworks
Sub-structures within the entire network that satisfy specific conditions.

* **Subnetwork:** Obtained by selecting a subset of the nodes and all of the links among these nodes.
* **Clique:** A complete subnetwork where a subset of nodes are all linked to each other.
* **Ego Network:** Consists of a chosen central node (the ego) and its neighbors.

<br/>

## 4. Degree and Strength
Measures of how many connections an individual node has within the network.

* **Degree ($k_{i}$):** The number of links, or neighbors, of a node.
* **Average Degree ($\langle k\rangle$):** Defined as:

$$\langle k\rangle=\frac{\sum_{i}k_{i}}{N}$$

  * Relationship with density in undirected networks:

$$\langle k\rangle=\frac{2L}{N}=\frac{dN(N-1)}{N}=d(N-1)$$

* **Directed Networks:** Nodes have an in-degree (number of incoming links) and an out-degree (number of outgoing links).
* **Strength ($s_{i}$):** In a weighted network, the sum of the weights of a node's links:

$$s_{i}=\sum_{j}w_{ij}$$

  * For directed weighted networks:

$$S_{i}^{in}=\sum_{j}w_{ji} \quad \text{and} \quad S_{i}^{out}=\sum_{j}w_{ij}$$

<br/>

## 5. Multilayer and Temporal Networks
Extended network structures to model complex, real-world interactions.

* **Multilayer Network:** Each layer can represent a specific type of network or relationship.
* **Multiplex:** A multilayer network built upon the exact same set of nodes across all layers.
* **Temporal Network:** A dynamic network where links and interactions occur at different times.

<br/>

## 6. Network Representations
Methods for storing and representing network data computationally.

* **Adjacency Matrix:** An $N \times N$ matrix where each element represents the link between the nodes indexed by the row and column.
* **Adjacency List:** A more compact representation for sparse networks that stores the list of neighbors for each node.
* **Edge List:** A data structure which lists each link as a pair of connected nodes.
