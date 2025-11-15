# Complex Network Motif Analysis: Topological Fingerprints of Real-World Graphs

[![GitHub Stars](https://img.shields.io/github/stars/wajason/Complex-Network-Motif-Analysis?style=for-the-badge&logo=github&color=4C8EDA)](https://github.com/wajason/Complex-Network-Motif-Analysis/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/wajason/Complex-Network-Motif-Analysis?style=for-the-badge&logo=github&color=4C8EDA)](https://github.com/wajason/Complex-Network-Motif-Analysis/network/members)
[![Issues](https://img.shields.io/github/issues/wajason/Complex-Network-Motif-Analysis?style=for-the-badge&color=4C8EDA)](https://github.com/wajason/Complex-Network-Motif-Analysis/issues)
[![License](https://img.shields.io/badge/License-MIT-4C8EDA?style=for-the-badge)](./LICENSE)
[![Run in Colab](https://img.shields.io/badge/Open%20in-Colab-4C8EDA?style=for-the-badge&logo=googlecolab)](https://colab.research.google.com/github/wajason/Complex-Network-Motif-Analysis/blob/main/Complex_Network.ipynb)

---

## 💡 Project Overview

This project conducts a **High-Order Network Structure Analysis** by comparing the frequency distribution of four key network **Motifs** across three distinct types of complex networks: Biological, Chemical, and Social. The goal is to demonstrate that network function dictates its local topology, yielding unique **"Structural Fingerprints"** for each domain.

The analysis utilizes `NetworkX` for graph computation and `Matplotlib` for visualization.

### Datasets Used

| Dataset | Type | Description | Selected Graph Size (Example) |
| :--- | :--- | :--- | :--- |
| **PROTEINS** | Biological | Protein-Protein Interaction (PPI) Network | 25 nodes, 51 edges |
| **MUTAG** | Chemical | Chemical Molecule Structures | 20 nodes, 22 edges |
| **IMDB-BINARY** | Social | Movie Actor Collaboration Network | 25 nodes, 91 edges |

### Motifs Calculated

We focus on quantifying the density of the following small subgraphs:

1.  **Triangle ($\text{K}_3$):** Basic clustering structure.
2.  **Wedge (2-Path):** Simple chain, representing potential connections.
3.  **4-Clique ($\text{K}_4$):** Highly dense, fully connected sub-community of 4 nodes.
4.  **4-Star:** Centralized structure, indicating a primary hub connected to 3 leaves.

---

## 📊 Experimental Results and Topological Analysis

### Normalized Motif Frequency Heatmap

The Heatmap (Motif count per node) shows the **absolute density** of each motif in the normalized graph space.

| Network | Triangle | Wedge | 4-Clique | 4-Star |
| :---: | :---: | :---: | :---: | :---: |
| **PROTEINS** | 0.88 | 4.16 | 0.12 | 1.44 |
| **MUTAG** | 0.00 | 1.60 | 0.00 | 0.40 |
| **IMDB** | **6.92** | 9.00 | **8.68** | **31.12** |

### Motif Composition by Network Type (Stacked Bar Chart)

The stacked bar chart highlights the **relative proportion** of each motif within the network's overall structure.

| Network | Triangle (%) | Wedge (%) | 4-Clique (%) | 4-Star (%) |
| :---: | :---: | :---: | :---: | :---: |
| **PROTEINS** | 13.3% | **63.0%** | 2.0% | 21.8% |
| **MUTAG** | 0.0% | **80.0%** | 0.0% | 20.0% |
| **IMDB** | 12.4% | 16.2% | 15.6% | **55.9%** |

---

## 🔬 Academic Discussion: Functionality vs. Structure

The results demonstrate a clear relationship where **network functionality dictates its topological fingerprint**.

### 1. Social Networks (IMDB): High Density and Centralization

* **Observation:** IMDB exhibits the **highest absolute density** across all motifs, with 4-Star and 4-Clique frequencies reaching **31.12** and **8.68** (Motifs per node), respectively.
* **Interpretation:** The **4-Star (55.9% proportion)** dominance validates the existence of highly centralized **Hub Nodes** (e.g., highly collaborative actors) that connect multiple others. The high frequency of Triangles and 4-Cliques confirms strong **Community Structure** (social groups/film casts) inherent to social systems.

### 2. Chemical Networks (MUTAG): Extreme Sparsity and Simplicity

* **Observation:** MUTAG is the **most sparse**, showing **zero frequency** for Triangle and 4-Clique, and a dominant **80.0% proportion** of the Wedge motif.
* **Interpretation:** This confirms the structural limitations of chemical bonds. The network primarily consists of simple **chain-like formations (Wedge)** and single rings, lacking the complex, redundant, high-order connections found in social or biological networks.

### 3. Biological Networks (PROTEINS): Modularity and Path-Dominance

* **Observation:** PROTEINS exhibits moderate density, dominated by the **Wedge (63.0%)** motif, with a substantial Triangle presence (13.3%).
* **Interpretation:** This composition suggests a structure that favors **pathways and modularity**. The high Wedge count (relative to high-order clusters) indicates that the network is organized efficiently to pass information (interactions) through specific sequences, rather than relying heavily on highly redundant, fully connected components.

---

## 🚀 Outlook: AI for Complex Networks

This Motif analysis serves as a crucial prerequisite for moving into **High-Order Interaction** studies. The observed structural differences motivate the development of specialized GNNs that can model complex networks beyond simple pairwise links, including:

* **Hypergraphs and Simplicial Complexes (SC):** To explicitly model multi-way interactions (e.g., three proteins interacting simultaneously, or three actors co-starring).
* **Foundation Models:** To leverage these diverse topological fingerprints to pre-train models that generalize across different network types (Biological vs. Social).
