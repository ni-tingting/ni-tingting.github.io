---
title: "Robotics Projects"
permalink: /robotics-projects/
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
Selected Robotics Projects (Supervision & Technical Guidance)

---

## Sim-to-Real Transfer for JetBot on Maze Escaping using Safe Reinforcement Learning 

- **Students:** Rocca Federico, Florian Tanguy
- **Supervision:** Tingting Ni, Kai Ren
- **Goal:** Develop a **Lagrangian-PPO framework** on a wheeled mobile-robot testbed to navigate a maze and reach the nearest exit, ensuring safety (obstacle avoidance) using feedback of robot position and relative position to obstacles/goals.
- **Work:**
  - Formulated the navigation challenge as a **Constrained Markov Decision Process (CMDP)** and implemented a **Lagrangian-PPO** approach to enforce safety constraints.
  - **Approach 1 (IsaacLab):** Leveraged **NVIDIA IsaacLab** to train policies across multiple **parallel environments** on GPU to accelerate learning.
  - **Approach 2 (Custom JAX):** Performed **system identification** to build a high-fidelity simulation model of the JetBot platform, utilizing **JAX** for accelerated learning.
  - Developed a **Sim-to-Real pipeline** exporting policies to a **ROS2** node for inference on a physical JetBot using OptiTrack for state estimation.
- **Outcome:**
  - **Simulation Performance:** Both approaches achieved **~100% collision-free trajectories** within their respective simulation environments.
  - **Sim-to-Real Gap (IsaacLab):** Policies trained in NVIDIA IsaacLab struggled to transfer, identifying critical gaps in the physics/actuation modeling that affected real-world safety.
  - **Real-World Success (Custom JAX):** Policies trained on the **self-built simulation model** bridged the reality gap, maintaining **~100% collision-free trajectories** when deployed on the physical robot.
 
<br>

<table>
  <tr>
    <th align="center">Custom Simulation </th>
    <th align="center">Real World (JetBot)</th>
  </tr>
  <tr>
    <td align="center"><img src="/assets/sim.gif" height="250"></td>
    <td align="center"><img src="/assets/real.gif" height="250"></td>
  </tr>
</table>

## Navigation of JetBot in Slippery Terrain via Domain Randomization 

- **Student:** Florian Tanguy
- **Supervision:** Tingting Ni, Kai Ren
- **Goal:** Enable a wheeled mobile robot to navigate **low-friction, slippery terrain** by overcoming the "Sim-to-Real" gap caused by unknown actuator deadzones and wheel slip.
- **Work:**
  - Migrated simulation to **JAX** for massive parallelization (4,096 environments) and differentiable physics, incorporating **System Identification** data to model multi-modal friction dynamics (distinct "slippery" vs. "grippy" regimes) and non-linear actuator deadzones.
  - Implemented **Data-Driven Domain Randomization** using **Gaussian Mixture Models (GMM)** to sample physics parameters, ensuring the training distribution covered real-world failure modes.
  - Addressed "perceptual aliasing" (where sliding mimics stopping) by implementing **Recurrent Neural Networks (LSTMs)** for policy structure, which outperformed memoryless Feedforward networks and Frame Stacking with MLPs.
- **Outcome:**
  - Achieved robust navigation across heterogeneous real-world environments, demonstrating **emergent recovery behaviors** (such as "wiggling") to escape low-friction terrain.
 
<br>

<div align="center">
  <video width="80%" controls autoplay loop muted>
    <source src="/assets/wet.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <p><b>Video:</b> Navigation performance on slippery terrain using different policies: 1. Memoryless Feedforward 2. MLP 3. LSTM.</p>
</div>

