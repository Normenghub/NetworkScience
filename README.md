# 🕸️ Network Science Study & Recap

이 저장소는 **Network Science(네트워크 과학)** 의 핵심 이론과 알고리즘을 학습하고 정리한 공간입니다.
그래프 이론의 기초부터 복잡계 네트워크(Complex Networks)의 동역학까지, 주요 교재를 기반으로 개념을 요약하고 코드로 구현합니다.

## 📚 References (참고 문헌)

이 학습 프로젝트는 다음 두 권의 핵심 교재를 기반으로 진행됩니다.

| **The Theory (이론 심화)** | **The Practice (구현 및 실습)** |
| :---: | :---: |
| <img src="http://networksciencebook.com/images/cover.jpg" width="150"> | <img src="https://m.media-amazon.com/images/I/71XmTcGvvFL._AC_UF1000,1000_QL80_.jpg" width="150"> |
| **Network Science** | **A First Course in Network Science** |
| *by Albert-László Barabási* | *by Filippo Menczer, Santo Fortunato, Clayton A. Davis* |
| 이론적 배경, 척도 없는 네트워크, 복잡계 물리학적 접근 | Python(NetworkX)을 활용한 알고리즘 구현 및 데이터 분석 |

<br/>

## 🎯 Objectives

* **Theory:** 네트워크의 구조적 속성과 생성 모델(Random, Small-world, Scale-free)의 수학적 이해
* **Implementation:** `NetworkX` (Python) 및 `C++`을 활용한 주요 그래프 알고리즘 구현
* **Analysis:** 실제 데이터셋(Social, Biological, Technological networks) 분석 및 시각화

## 🗂️ Curriculum & Recap Status

### Part 1: Graph Theory Basics
- [ ] **Introduction to Networks** (Graph elements, Adjacency matrix)
- [ ] **Graph Theory 101** (Paths, Cycles, Connectivity, Components)
- [ ] **Network Measures** (Degree, Average Path Length, Clustering Coefficient)

### Part 2: Network Models
- [ ] **Random Networks** (Erdős-Rényi Model, Phase Transitions)
- [ ] **Small Worlds** (Watts-Strogatz Model, Six Degrees of Separation)
- [ ] **Scale-Free Networks** (Barabási-Albert Model, Power Laws, Hubs)
- [ ] **Configuration Model** (Generating networks with arbitrary degree sequences)

### Part 3: Structure & Dynamics
- [ ] **Centrality Measures** (Degree, Betweenness, Closeness, PageRank)
- [ ] **Community Detection** (Modularity, Hierarchical Clustering)
- [ ] **Spreading Phenomena** (SI/SIR Models, Epidemics on Networks)
- [ ] **Percolation Theory** (Robustness, Attack Tolerance)

<br/>

## 🛠️ Tech Stack & Tools

* **Language:** Python 3.x (Primary), C++ (For performance-critical simulations)
* **Libraries:**
    * `NetworkX`: 네트워크 생성 및 분석
    * `NumPy` / `SciPy`: 행렬 연산 및 과학 계산
    * `Matplotlib` / `Seaborn`: 데이터 시각화
    * `Gephi`: (Optional) 대규모 네트워크 시각화 툴

## 📂 Repository Structure

```bash
├── 01_Graph_Theory/          # 기초 그래프 이론 정리 및 예제
├── 02_Network_Models/        # ER, WS, BA 모델 시뮬레이션 코드
├── 03_Centrality_Community/  # 중심성 지표 및 커뮤니티 탐지 알고리즘
├── 04_Dynamics/              # 전파 모델 및 동역학 시뮬레이션
├── assets/                   # 다이어그램 및 시각화 결과물 이미지
└── README.md
