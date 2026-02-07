---
layout: page
title: "Robotics Projects"
permalink: /robotics-projects/
---
# Selected Robotics Projects (Supervision & Technical Guidance)

#### **Imitation Learning & IRL for Dexterous Manipulation (MSc Thesis, 2025)**

- **Student:** Gregorio Valenti
- **Supervision:** Andreas Schlaginhaufen, Cheng Pang (CREATE Lab, EPFL)
- **Goal:** Build an imitation-learning pipeline for controlling a custom dexterous robotic hand, using demonstrations collected via a VR teleoperation setup.
- **Work:**
    - Developed a VR teleoperation + data collection pipeline for the  [**ADAPT hand**](https://www.youtube.com/watch?v=gVNkmsFAQ3Q) in **NVIDIA Isaac Sim** to gather expert demonstrations.
    - Implemented and benchmarked **behavioral cloning (BC)**, **inverse RL (IRL)**, and **RL fine-tuning** on simulated pick-and-place tasks.
- **Outcome:**
    - Achieved successful **pick-and-place in simulation** with a **22-DoF** dexterous hand setup.
    - Demonstrated that **BC benefits from RL/IRL refinement**, indicating a promising hybrid approach for dexterous manipulation.

<div style="display:flex; gap:12px; justify-content:center; align-items:center; flex-wrap:wrap; margin-bottom:24px;">
  <img src="/assets/hand/pick_and_place.png"
       alt="Pick and place"
       style="height:350px; width:auto; max-width:48%; border-radius:10px;">
  <img src="/assets/hand/teleop.png"
       alt="Teleop"
       style="height:350px; width:auto; max-width:48%; border-radius:10px;">
</div>


<hr>
#### **Imitation Learning for Autonomous Car Racing (MSc Project, 2024)**
  - Performed system identification and built a simulation model of the JetBot platform.
- **Student:** Emre Gursoy 
- **Supervision:** Andreas Schlaginhaufen, Johannes Waibel (PREDICT Lab, EPFL)
- **Goal:** Learn stable control policies for an autonomous race car from expert demonstrations.  
- **Work:**
  - Augmented expert demonstrations with **stabilizing inputs** (using [replica noising](https://arxiv.org/pdf/2307.14619)) to improve closed-loop stability of the behavioral cloning policy.
  - Evaluated against **vanilla BC** in both **simulation** and **real-world racetrack** experiments.  
- **Outcome:**
  - Achieved a **stable BC policy** in simulation and on track, improving behavior from **immediate crashes** to **successful lap/track completion**.

<div style="display:flex; gap:12px; justify-content:center; align-items:center; flex-wrap:wrap; margin-bottom:24px;">
  <video controls style="height:350px; width:auto; max-width:40%; border-radius:10px;">
    <source src="/assets/car/simulation.webm" type="video/webm">
  </video>

  <video controls style="height:350px; width:auto; max-width:57%; border-radius:10px;">
    <source src="/assets/car/real_track.mp4" type="video/mp4">
  </video>
</div>


<hr>
#### **Safe Reinforcement Learning for Robot Maze Escaping (MSc Project, 2024)**

- **Student:** Rocca Federico
- **Supervision:** Tingting Ni, Kai Ren
- **Goal:** Develop a **Lagrangian-PPO framework** on a wheeled mobile-robot testbed to navigate a maze and reach the nearest exit, ensuring safety (obstacle avoidance) using feedback of robot position and relative position to obstacles/goals.
- **Work:**
  - Formulated the navigation challenge as a **Constrained Markov Decision Process (CMDP)** and implemented a **Lagrangian-PPO** approach to enforce safety constraints.
  - Leveraged **NVIDIA IsaacLab** to train policies across **4096 parallel environments** on GPU to accelerate learning.
  - Developed a **Sim-to-Real pipeline** exporting policies to a **ROS2** node for inference on a physical JetBot using OptiTrack for state estimation.
- **Outcome:**
  - Learned **safe navigation policies** in simulation using a hybrid cost/probability strategy, achieving **~99% collision-free trajectories**.
  - Deployed policies to the real robot to evaluate **Sim-to-Real transfer**, identifying critical gaps in action space mapping and control latency that affected real-world safety.

<div style="display:flex; gap:12px; justify-content:center; align-items:center; flex-wrap:wrap; margin-bottom:24px;">
  <video controls style="height:250px; width:auto; max-width:100%; border-radius:10px;">
    <source src="/assets/jetbot/demo.mp4" type="video/mp4">
  </video>
</div>
