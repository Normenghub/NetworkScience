# Chapter 4. Directions and Weights

This document is a note summarizing the core features of directed and weighted networks based on chapter 4 of ***A First Course in Network Science***, utilizing Python's `NetworkX`.

## 1. Directed Networks

Networks where links have a specific direction, from a source node to a target node.

* **Examples:**
  * **Citation Networks:** Links point from a citing paper to a cited paper, always backward in time.
  * **The Web:** A hyperlink leads from page A to page B, but page B may not link back to page A.
* **Bow-Tie Structure (Web Graph):** The giant component of the Web has three main parts:
  * **Core:** The giant strongly connected component (SCC), where any page can reach any other.
  * **In-component:** Pages that can reach the core but cannot be reached from it.
  * **Out-component:** Pages reachable from the core but that cannot reach it back.

<br/>

## 2. PageRank

A algorithm to rank the importance of nodes in a directed network, famously used by Google.

* **Core Idea:** A page is important if it is linked to by other important pages. Importance propagates through links.
* **Key Distinction from In-Degree:** Among two pages with the same in-degree, the one linked by pages with higher PageRank wins. A link from a high-PageRank page provides a greater boost.
* **Distribution:** The distribution of PageRank is heavy-tailed, similar to the in-degree distribution of the Web.
* **Random Surfer Model:** PageRank can be interpreted as the fraction of time a random surfer — who follows links at random but occasionally teleports to a random page — spends on each page:

$$r_i = \frac{1-d}{N} + d \sum_{j \to i} \frac{r_j}{k_j^{out}}$$

  *(Note: $d$ is the damping factor, typically set to 0.85, representing the probability of following a link rather than teleporting.)*

<br/>

## 3. Weighted Networks

Networks where each link carries a numerical weight representing the strength of the connection.

* **Strength ($s_i$):** The sum of the weights of all links adjacent to a node:

$$s_i = \sum_j w_{ij}$$

* **Directed Weighted Networks:** Nodes have both in-strength and out-strength:

$$s_i^{in} = \sum_j w_{ji} \quad \text{and} \quad s_i^{out} = \sum_j w_{ij}$$

* **Application — Information Diffusion:** In a retweet network, out-strength measures a user's propensity to *produce* information (influence), while in-strength measures their propensity to *consume* it. The ratio $s^{out}/s^{in}$ classifies users as producers or consumers.

<br/>

## 4. Cosine Similarity

A measure to compare the similarity between two nodes (e.g., documents) based on their weight vectors.

$$\cos(\vec{d_1}, \vec{d_2}) = \frac{\vec{d_1}}{||\vec{d_1}||} \cdot \frac{\vec{d_2}}{||\vec{d_2}||} = \frac{\sum_t w_{d_1,t} w_{d_2,t}}{\sqrt{\sum_t w_{d_1,t}^2}\sqrt{\sum_t w_{d_2,t}^2}}$$

* A cosine of **1** means the two documents share all the same terms; **0** means they share none.
* The vector is normalized by its norm $||\vec{d}|| = \sqrt{\sum_t w_{d,t}^2}$, so longer documents are not unfairly penalized.
* **Web Topical Locality:** Pages close to each other (short path length) have high cosine similarity. As crawl distance increases, similarity decays toward the noise level — illustrating *topic drift*.

<br/>

## 5. Information and Misinformation

How directed and weighted networks shape the spread of content on social media.

* **Influence vs. Popularity:** Out-strength (retweets received) captures *influence*, whereas in-degree in a follower network captures *popularity*. A user can be popular but not influential.
* **Social Bots:** Fake automated accounts that amplify misinformation by generating fake tweets, retweets, and mentions, effectively hijacking public attention and manipulating ranking algorithms.
* **Astroturfing:** Bots create the illusion of grassroots campaigns to make fringe views appear mainstream.

<br/>

## 6. Co-citation and Co-reference Networks

Undirected, weighted networks derived from directed citation networks.

* **Co-citation:** Two papers are linked if they are both cited by the same paper. Link weight reflects how many papers cite both.
* **Co-reference:** Two papers are linked if they both cite the same paper. Link weight reflects how many papers they both reference.
* Both are used to find related sets of publications and reveal thematic clusters in academic literature.

<br/>

## 7. Weight Heterogeneity and Network Backbone

Handling the broad distribution of link weights in real-world networks.

* **Heavy-Tailed Weight Distributions:** Like degree distributions, link weights in real networks often span many orders of magnitude.
* **Network Backbone:** A method to extract the most significant links by filtering out weak or statistically insignificant ones.
  * A global weight threshold is inappropriate for heterogeneous networks.
  * Instead, each link is evaluated against a null model local to its node. The probability that link $ij$ has weight $w_{ij}$ or larger under the null model is:

$$p_{ij} = \left(1 - \frac{w_{ij}}{s_i}\right)^{k_i - 1}$$

  * If $p_{ij} < \alpha$ (a chosen significance level), the link is preserved; otherwise it is removed. Lower $\alpha$ produces a sparser backbone.
