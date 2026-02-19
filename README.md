# 🕸️ Network Science with Python

This repository is a space to log my journey of learning the core theories of network science, based on the textbook ***[A First Course in Network Science]***, and implementing them directly in **Python**.

## 📘 About The Project

* **Textbook:** *A First Course in Network Science* by Filippo Menczer, Santo Fortunato, and Clayton A. Davis
* **Goal:** Summarize the core theories of each chapter and implement examples and exercises using Python libraries such as `NetworkX`.
* **Focus:** Bridging the gap between theoretical understanding (Theory) and practical code implementation (Implementation).

## 🛠️ Tech Stack

* **Language:** Python 3.x
* **Core Libraries:**
  * `NetworkX`: Graph creation, manipulation, structural analysis, and drawing
  * `NumPy` / `Pandas`: Data processing and matrix operations
  * `Matplotlib` / `Seaborn`: Network visualization and statistical plotting
  * `Jupyter Notebook`: Hands-on practice and result reporting

## 🗂️ Curriculum & Progress

Tracking progress according to the textbook's table of contents:

### **0. Introduction**
- [ ] 0.1 Social Networks
- [ ] 0.2 Communication & Transportation Networks
- [ ] 0.3 The Web, Wikipedia, and The Internet

### **1. Network Elements**
- [ ] 1.1~1.2 Basic Definitions & Handling Networks in Code
- [ ] 1.3 Density and Sparsity
- [ ] 1.5 Degree & Degree Distribution
- [ ] 1.6~1.7 Directed & Weighted Networks
- [ ] 1.10 Drawing Networks (Visualization techniques)

### **2. Small Worlds**
- [ ] 2.1 Birds of a Feather (Clustering)
- [ ] 2.2 Paths and Distances
- [ ] 2.3 Connectedness and Components
- [ ] 2.5 Finding Shortest Paths (BFS/DFS)
- [ ] 2.7 Six Degrees of Separation

### **3. Hubs**
- [ ] 3.1 Centrality Measures (Degree, Closeness, Betweenness)
- [ ] 3.2 Centrality Distributions (Power Laws)
- [ ] 3.3 The Friendship Paradox
- [ ] 3.5 Robustness (Resilience to attacks/failures)
- [ ] 3.6 Core Decomposition

### **4. Directions and Weights**
- [ ] 4.1 Directed Networks & The Web (Bow-tie structure)
- [ ] 4.3 PageRank Algorithm
- [ ] 4.4 Weighted Networks
- [ ] 4.6 Co-occurrence Networks

### **5. Network Models**
- [ ] 5.1 Random Networks (Erdős-Rényi)
- [ ] 5.2 Small Worlds (Watts-Strogatz)
- [ ] 5.3 Configuration Model
- [ ] 5.4 Preferential Attachment (Barabási-Albert)

### **6. Communities**
- [ ] 6.1 Basic Definitions (Cliques, Clusters)
- [ ] 6.3 Community Detection Algorithms (Modularity, Louvain)
- [ ] 6.4 Method Evaluation

### **7. Dynamics**
- [ ] 7.1 Ideas, Information, Influence (Threshold models)
- [ ] 7.2 Epidemic Spreading (SI, SIR, SIS models)
- [ ] 7.3 Opinion Dynamics
- [ ] 7.4 Search in Networks

<br/>

## 📂 Repository Structure

The practice codes for each chapter are organized into the following directory structure:

```bash
├── 00_Introduction/       # Loading network datasets and basic exploration
├── 01_Network_Elements/   # NetworkX basics, calculating graph properties
├── 02_Small_Worlds/       # Pathfinding, clustering coefficients, small-world simulations
├── 03_Hubs/               # Centrality measures, power-law distribution, robustness tests
├── 04_Directions_Weights/ # PageRank implementation, weighted network analysis
├── 05_Network_Models/     # Generating and comparing ER, WS, and BA models
├── 06_Communities/        # Applying and visualizing community detection algorithms
├── 07_Dynamics/           # Simulating spreading models (e.g., SIR)
└── data/                  # Network datasets used for practice (GML, Edge list, etc.)
