🚀 Jet Classification using Graph Neural Networks

This project explores graph-based representations for particle physics jet classification. We convert calorimeter images into particle-level point clouds and construct graphs to classify jets as quark or gluon using Graph Neural Networks.

📌 Overview

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

📊 Results
Model	Graph	Accuracy
GAT	kNN	0.6839
EdgeConv	kNN	0.6849
📈 Observations

Both models converge within 15–20 epochs

EdgeConv slightly outperforms GAT

Graph-based representations effectively capture jet structure

🚧 Future Work

Explore dynamic graph construction

Experiment with different k values

Incorporate additional physics-inspired features

Try deeper architectures

🧠 Conclusion

Graph Neural Networks provide an effective framework for jet classification by leveraging particle-level relationships. EdgeConv shows a slight advantage due to its ability to model local geometric interactions.