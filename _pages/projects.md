---
title: "Robotics Projects"
permalink: /robotics-projects/
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

## Selected Robotics Projects (Supervision & Technical Guidance)
1. [**Sim-to-Real Transfer for JetBot on Maze Escaping using Safe Reinforcement Learning**](#project-1)
2. [**Navigation of JetBot in Slippery Terrain via Domain Randomization**](#project-2)
3. [**Safe Reinforcement Learning for Multi-Robot Systems in Hazardous Environments**](#project-3)

---

### <a id="project-1"></a>Sim-to-Real Transfer for JetBot on Maze Escaping using Safe Reinforcement Learning

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
    <th align="center">Simulation</th>
    <th align="center">Real World (JetBot)</th>
  </tr>
  <tr>
    <td align="center"><img src="/assets/sim.gif" height="250"></td>
    <td align="center"><img src="/assets/real.gif" height="250"></td>
  </tr>
</table>

<div align="right"><a href="#project-directory">(Back to Top)</a></div>

---

### <a id="project-2"></a>Navigation of JetBot in Slippery Terrain via Domain Randomization

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
  <video width="60%" controls autoplay loop muted>
    <source src="/assets/wet.MP4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <p><b>Video:</b> Navigation performance on slippery terrain using different policies: 1. Memoryless Feedforward 2. MLP 3. LSTM.</p>
</div>

<div align="right"><a href="#project-directory">(Back to Top)</a></div>
---

### <a id="project-3"></a> Safe Reinforcement Learning for Multi-Robot Systems in Hazardous Environments

- **Student:** Xiao Zhou
- **Supervision:** Tingting Ni, Kai Ren
- **Goal:** Utilize **Constrained Multi-Agent Reinforcement Learning (CMARL)** to enable robots to collaborate on survivor rescue missions while ensuring their own survival in hazardous environments featuring spreading fires and obstacle avoidance.
- **Work:**
  - Formulated the rescue mission as a **Constrained Decentralized Partially Observable Markov Decision Process (Dec-POMDP)**.
  - Implemented **constrained MAPPO**, **constrained IPPO**, and **Decentralized CRPO** to learn cooperative policies that strictly enforce safety, ensuring robots avoid fires and collisions while performing rescues.
- **Outcome:**
  - Achieved robust **collaborative behaviors** where robots successfully coordinate to locate and save survivors.

<br>

<div align="center">
  <video width="60%" controls autoplay loop muted>
    <source src="/assets/multi_rob.mov" type="video/quicktime">
    <source src="/assets/multi_rob.mov" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <p><b>Video:</b> Multi-robot coordination in hazardous fire environments.</p>
</div>

<div align="right"><a href="#project-directory">(Back to Top)</a></div>
