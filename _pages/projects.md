---
layout: page
title: "Robotics Projects"
permalink: /robotics-projects/
---
# Selected Robotics Projects (Supervision & Technical Guidance)


<hr>

#### **Safe Reinforcement Learning for Robot Maze Escaping (MSc Projects, 2024/2025)**

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

