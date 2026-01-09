# Transition Path Sampling Using Gradient Matching

This repository presents **Transition Path Sampling Using Gradient Matching**, a method for efficiently sampling rare molecular transition events using a neural network–parameterized potential trained via **path-space Kullback–Leibler (KL) divergence minimization**.

The approach accelerates the observation of rare transitions (e.g., protein conformational changes and chemical reactions) **without requiring expensive transition-path simulation data**, while remaining fully **physics-informed**.

---

## Overview

In molecular dynamics (MD), transitions between metastable states often occur on millisecond timescales, making direct simulation computationally infeasible. Most computational effort is spent resolving thermal fluctuations within metastable basins rather than the rare transition events themselves.

This work introduces a **neural network potential** explicitly designed to sample transition paths between specified initial and final metastable states. Instead of learning the full potential energy surface, the model focuses on the **transition region**, where rare events occur.

The neural network potential is trained by minimizing the **Kullback–Leibler (KL) divergence between path probability measures** induced by:
- Langevin dynamics under the true molecular force field, and
- Langevin dynamics under the learned neural network potential,

with **fixed endpoint constraints**.

---

## Key Contributions

- **Path-space KL divergence with fixed endpoints**  
  We derive a simplified and computable expression for the KL divergence between path probability measures induced by two stochastic differential equations under fixed endpoint constraints.

- **Endpoint-conditioned neural network potential**  
  We design a neural network architecture based on interpolants that enforces prescribed initial and final metastable states while allowing flexible modeling of transition dynamics.

- **Physics-informed learning**  
  The model learns directly from molecular force-field gradients, ensuring physically consistent transition paths.

- **No rare-event training data required**  
  The method does not rely on pre-simulated rare transition trajectories, preserving the purpose of accelerated sampling.

---

## Advantages

- **No rare-event MD data required**  
  Training does not rely on precomputed transition trajectories.

- **Physics-informed by construction**  
  The neural network learns directly from molecular force-field gradients.

- **Efficient rare-event sampling**  
  Rare transitions are observed frequently without changing the MD integration timestep.

- **Focused modeling capacity**  
  The method avoids approximating irrelevant regions of the potential energy surface.

## Results for Muller-Brown Potential

The model trained on the Muller-Brown potential quickly converges allowing for sampling transition paths.

<img src="https://github.com/user-attachments/assets/5dab060b-2fd8-400d-9199-27c7d2ce65da" width="518" height="403" />

<img src="https://github.com/user-attachments/assets/f135a74d-9a8d-48e7-9902-ace5154e1969" width="518" height="403" />

## Citation

## Citation

If you use this work, please cite:

```bibtex
@article{nagaraj2024tps,
  title={Transition Path Sampling Using Gradient Matching},
  author={Nagaraj, Balakrishnan},
  year={2024}
}
```



