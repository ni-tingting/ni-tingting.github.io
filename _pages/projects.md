
---
layout: archive
title: "Robotics Projects"
permalink: /robotics-projects/
redirect_from:
  - /home
---

{% include base_path %}

Selected Robotics Projects (Supervision & Technical Guidance)
======


#### **Sim-to-Real Transfer for JetBot via Domain Randomization and Recurrent Policies (Semester Project, 2026)**

- **Student:** Florian Tanguy
- **Supervision:** Tingting Ni, Kai Ren
- **Goal:** Address the "Sim-to-Real" gap in low-cost robotics, specifically targeting the "stuck robot" phenomenon on low-friction surfaces by integrating high-fidelity physics modeling and memory-based control.
- **Work:**
  - Performed **System Identification** on the physical robot to capture multi-modal friction dynamics (e.g., "slippery" vs. "grippy" regimes).
  - Implemnet **JAX**, enabling massive parallelization (4,096 environments) and differentiable physics to model non-linear actuator deadzones.
  - Implemented **Data-Driven Domain Randomization** using Gaussian Mixture Models (GMM) to sample realistic physics parameters for domain randomization.
  - Addressed **perceptual aliasing** (where wheel slip creates false stationary observations) by transitioning from memoryless Feedforward networks to **Recurrent Neural Networks (LSTMs)**.
- **Outcome:**
  - The **LSTM + Data-Driven** approach successfully bridged the reality gap, enabling **emergent recovery behaviors** (such as "wiggling") to escape low-friction patches where standard policies remained immobilized[cite: 619, 1174].
  - Achieved robust navigation across heterogeneous real-world environments, significantly outperforming Frame Stacking and MLP baselines.


#### **Sim-to-Real Transfer for JetBot on Maze Escaping using Safe Reinforcement Learning (MSc Projects, 2024/2025)**

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

