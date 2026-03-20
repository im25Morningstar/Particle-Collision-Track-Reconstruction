# Graph Neural Networks for Jet Classification (ML4SCI GSoC Task)

This project explores graph-based representations of particle physics jet events using Graph Neural Networks (GNNs).

# Overview

Input: Multi-channel jet images (ECAL, HCAL, Tracks)

Transformation: Image → Point Cloud → Graph

Task: Binary classification (quark vs gluon jets)

🧠 Methodology
🔹 Feature Engineering

Each particle is represented by:

Transverse momentum (pt)

log(pt)

Spatial coordinates (η, φ)

Relative coordinates (Δη, Δφ)

Radial distance (ΔR)

🔹 Graph Construction

Nodes: Particles (non-zero pixels)

Edges: k-Nearest Neighbors (k=8)

Graph built in η–φ space

🔹 Models
1. Graph Attention Network (GAT)

Learns attention weights between particles

2. EdgeConv (Dynamic Graph CNN)

Captures local geometric structure explicitly

⚙️ Training Setup

Loss: CrossEntropyLoss

Optimizer: Adam

Learning rate: 0.001

Epochs: 30

Batch size: 32


## Future Work

- Train on combined dataset (all runs)
- Explore dynamic graph construction
- Experiment with hybrid GNN architectures
- Incorporate physics-informed constraints

## Experiments

We evaluate models across three independent dataset splits:

| Dataset | GAT Acc | Edge Acc | GAT AUC | Edge AUC |
|--------|--------|---------|--------|---------|
| Run0   | 0.684 | 0.685 | 0.749    | 0.738     |
| Run1   | 0.696  | 0.695  | 0.753  | 0.750   |
| Run2   | 0.6946 | 0.6943 | 0.7498 | 0.7432  |


## Key Insights

- No single model consistently outperforms across all dataset splits
- EdgeConv performs better when local geometric structure dominates
- GAT performs better when adaptive interaction weighting is beneficial

This suggests that both models capture complementary aspects of jet structure.

The variability across runs highlights the importance of robust evaluation in scientific machine learning.

## Conclusion

This work demonstrates the effectiveness of graph-based approaches for particle physics and highlights the importance of model evaluation across multiple data distributions.
