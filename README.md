# 🕸️ Network Science with Python

이 저장소는 ***[A First Course in Network Science]*** 교재를 기반으로 네트워크 과학의 핵심 이론을 학습하고, **Python**으로 직접 구현한 기록을 남기는 공간입니다.

## 📘 About The Project

* **Textbook:** *A First Course in Network Science* by Filippo Menczer, Santo Fortunato, and Clayton A. Davis
* **Goal:** 교재의 챕터별 이론을 요약하고, `NetworkX` 등 파이썬 라이브러리를 활용하여 예제 및 연습문제를 구현합니다.
* **Focus:** 이론적 개념(Theory)의 이해와 코드 구현(Implementation)의 병행

## 🛠️ Tech Stack

* **Language:** Python 3.x
* **Core Libraries:**
  * `NetworkX`: 그래프 생성, 조작, 구조 분석, 그림 그리기
  * `NumPy` / `Pandas`: 데이터 처리 및 행렬 연산
  * `Matplotlib` / `Seaborn`: 네트워크 시각화 및 통계 플로팅
  * `Jupyter Notebook`: 실습 및 결과 리포트

## 🗂️ Curriculum & Progress

교재의 목차에 따라 진행 상황을 체크합니다.

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

각 챕터별 실습 코드는 아래 폴더 구조로 관리됩니다.

```bash
├── 00_Introduction/       # 네트워크 데이터셋 로딩 및 기초 탐색
├── 01_Network_Elements/   # NetworkX 기초, 그래프 속성 계산
├── 02_Small_Worlds/       # 경로 탐색, 군집 계수, 좁은 세상 효과 시뮬레이션
├── 03_Hubs/               # 중심성 측정, 멱함수 분포 분석, 로버스트니스 테스트
├── 04_Directions_Weights/ # 페이지랭크 구현, 가중치 네트워크 분석
├── 05_Network_Models/     # ER, WS, BA 모델 생성 및 비교
├── 06_Communities/        # 커뮤니티 탐지 알고리즘 적용 및 시각화
├── 07_Dynamics/           # 전파 모델(SIR) 시뮬레이션
└── data/                  # 실습에 사용되는 네트워크 데이터셋 (GML, Edge list 등)
