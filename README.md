# Generalizable Deep Reinforcement Learning-Based Intelligent Handover in Indoor WiGig Networks

![WiGig](https://img.shields.io/badge/WiGig-60GHz-blue?style=for-the-badge)
![DRL](https://img.shields.io/badge/Deep%20RL-DQN%20%7C%20PPO%20%7C%20A2C-purple?style=for-the-badge)
<img src="https://img.shields.io/badge/-Python-3776AB?&style=for-the-badge&logo=Python&logoColor=white" alt="Python Badge" />
![Handover](https://img.shields.io/badge/Intelligent%20Handover-red?style=for-the-badge)

---

##  Project Highlights

- Proposed a **generalizable DRL-based framework** for intelligent handover in indoor WiGig networks  
- Designed a **gain-sensitive reward function** to handle small channel gain differences  
- Compared **DQN, PPO, and A2C** with multiple hyperparameter tuning techniques  
- Demonstrated that **DQN + Grid Search** achieves the best performance  
- Validated **generalization across 1–8 user-density scenarios**  

---

## 📄 Abstract

Indoor WiGig networks operating in the 60 GHz band offer ultra-fast connectivity but suffer from severe blockage and dynamic channel variations. Traditional handover techniques struggle to adapt in such environments.

This project presents a **deep reinforcement learning-based intelligent handover framework** that evaluates DQN, PPO, and A2C combined with hyperparameter tuning techniques such as Grid Search, Random Search, Optuna, and HyperOpt.

A **novel reward function** is introduced to amplify channel gain differences and improve learning stability. Results show that:

- **DQN + Grid Search** achieves the best performance  
- **48% higher reward than A2C**  
- **32% faster convergence than PPO**  
- A **merged agent trained on multiple user densities generalizes effectively**, while a high-density-only model degrades by up to **13%**

---

## 🚀 Key Contributions

- First study on **multi-user indoor WiGig handover using DRL**
- Introduced a **channel-gain-aware reward mechanism**
- Comprehensive evaluation of **hyperparameter tuning strategies**
- Demonstrated **generalization vs expert vs high-density models**
- Showed practicality of **single unified agent vs multiple expert agents**

---

## 🧠 Problem Motivation

WiGig networks provide ultra-high-speed communication but are highly sensitive to:

- Blockage (walls, humans, furniture)
- Mobility
- Rapid signal fluctuations

Traditional threshold-based handover methods fail in such dynamic environments.

👉 This work solves this using **adaptive DRL-based decision-making**.

---

## 🏗️ System Model

- Indoor environment: **5m × 5m × 3m office**
- **4 WiGig Base Stations (BS)**
- Up to **8 mobile users**
- Realistic **human mobility model**
- Dynamic **LoS / NLoS channel modeling**

<p align="center">
  <img src="room.PNG" width="500">
  <br>
  <b>Figure 1:</b> Indoor WiGig environment.
</p>

<p align="center">
  <img src="channel_model.png" width="750">
  <br>
  <b>Figure 2:</b> Mobility and channel modeling framework.
</p>

---

## 📊 Data Generation

- Generated datasets for **1–8 users**
- Simulated:
  - entering
  - moving
  - exiting scenarios

### Preprocessing

- Applied **Min-Max normalization**
- Scaled channel gains to **[0,1]**
- Ensured stable and fair RL learning

---

## 🤖 RL Framework

### Agents

- **DQN (Value-based)**
- **PPO (Policy-based)**
- **A2C (Actor-Critic)**

### State
- Channel gains from **4 BSs**

### Action
- Select BS / trigger handover

### Objective
- Maximize QoS  
- Minimize unnecessary handovers  

<p align="center">
  <img src="assets/rl_framework.png" width="650">
  <br>
  <b>Figure 3:</b> RL-based handover framework.
</p>

---

## 🎯 Reward Function

Custom gain-sensitive reward:

- Reward switching only if gain improvement > threshold (5%)
- Penalize unnecessary handovers
- Reward staying when connection is strong

👉 Improves:
- Convergence speed  
- Decision accuracy  
- Stability  

---

## ⚙️ Hyperparameter Tuning

Evaluated:

- Grid Search
- Random Search
- Optuna
- HyperOpt

### Best Results

| Agent | Best Method |
|------|------------|
| PPO  | Grid Search |
| A2C  | HyperOpt |
| DQN  | Grid Search |

---

## 📈 Results

### Key Findings

- **DQN + Grid Search = Best Overall**
- +48% reward vs A2C
- 32% faster convergence vs PPO

<p align="center">
  <img src="assets/rolling_reward_comparison.png" width="850">
  <br>
  <b>Figure 4:</b> Rolling reward comparison.
</p>

---

## 🌍 Generalization Study

Compared:

- ✅ Merged Agent (trained on 1–8 users)
- ❌ High-density agent (trained only on 8 users)
- ⚠️ Expert agents (one per density)

### Results

- Merged agent → **Best generalization**
- High-density agent → **Up to 13% performance drop**
- Expert agents → Accurate but impractical

<p align="center">
  <img src="assets/generalization_comparison.png" width="850">
  <br>
  <b>Figure 5:</b> Generalization comparison.
</p>

---

## 💡 Why This Matters

This work shows that:

👉 A **single generalized RL model** can outperform specialized models  
👉 Reduces:
- Deployment complexity  
- Memory usage  
- System overhead  

👉 Enables:
- Scalable intelligent wireless systems  
- Real-time adaptive handover  
- Future 6G-ready AI networking  

---

## 📁 Repository Structure
