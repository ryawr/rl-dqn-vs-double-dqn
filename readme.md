# Implementation and Comparitive analysis of DQN and Double-DQN to solve OpenAI Gym CartPole and MountainCar environments

This repository contains a comprehensive analysis and implementation of **Deep Q-Network (DQN)** and **Double DQN (DDQN)** algorithms applied to various environments: Gridworld, Cartpole, and Mountain Car[cite: 1]. The project evaluates the effectiveness of these algorithms in both discrete and continuous state spaces[cite: 1].

---

## Project Overview

The primary goal of this analysis was to compare the performance and convergence stability of vanilla DQN against the improved Double DQN algorithm[cite: 1]. 

### Key Architecture Benefits
*   **Experience Replay**: Used to break correlation between consecutive steps by sampling random past experiences, ensuring well-rounded training without overfitting[cite: 1].
*   **Target Network**: Implemented to solve the "moving target" problem by fixing target Q-values for a specific number of training steps[cite: 1].
*   **Q-Function Approximation**: Utilized neural networks to solve continuous state environments that are untreatable with tabular methods[cite: 1].

---

## Environments & Neural Networks

| Environment | Observation Space | Action Space | Network Architecture[cite: 1] |
| :--- | :--- | :--- | :--- |
| **Gridworld** | Discrete (Vector size 5) | 6 Actions | 2 Hidden Layers (64 units each) |
| **Cartpole-v1** | Continuous (Vector size 4) | 2 Actions | 2 Hidden Layers (24 units each) |
| **MountainCar**| Continuous (Vector size 2) | 3 Actions | 2 Hidden Layers (128 units each) |

### Custom Modifications
*   **Mountain Car Reward**: The default sparse reward was modified to a custom energy-based reward (change in car energy - 0.01) to encourage faster completion and more constructive learning[cite: 1].

---

## Analysis Results

### Comparative Performance
*   **Gridworld**: Double DQN converged significantly faster (approx. episode 4000) compared to vanilla DQN (approx. episode 8000)[cite: 1].
*   **Cartpole**: Vanilla DQN showed unstable learning with larger networks due to overfitting; DDQN converged earlier at episode 1700 compared to 3000 for DQN[cite: 1].
*   **Mountain Car**: DQN converged earlier (episode 6000) than DDQN (episode 9000), likely due to network sync instability in the DDQN implementation for this specific environment[cite: 1].

### Key Findings
*   **Discrete vs. Continuous**: Discrete state environments (Gridworld) exhibited more stable learning than continuous state environments[cite: 1].
*   **Overestimation**: Double DQN effectively addressed the overestimation problem common in vanilla DQN, generally leading to more stable learning trends[cite: 1].

---

## File Structure

The repository is organized as follows[cite: 1]:
*   `dqn.ipynb`: The primary Jupyter notebook containing all code for training and evaluation[cite: 1].
*   `analysis.pdf`: The detailed final report[cite: 1].
*   `dqn_*.h5`: Saved model weights for the vanilla DQN algorithm[cite: 1].
*   `ddqn_*.h5`: Saved model weights for the Double DQN algorithm[cite: 1].

---

## How to Use

### Prerequisites
Ensure you have the following libraries installed:
*   PyTorch
*   Gymnasium
*   NumPy
*   Matplotlib

### Running the Analysis
1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/ryawr/rl-dqn-vs-double-dqn.git
    ```
2.  **Open the Notebook**:
    Navigate to the directory and open `dqn.ipynb` in your preferred Jupyter environment[cite: 1].
3.  **Execute Cells**: 
    The notebook is structured to define the environment, initialize the DQN/DDQN agents, and run the training loops.
4.  **Loading Models**:
    You can use the provided `.h5` files to skip training and jump directly to evaluation to see the agents in action[cite: 1].

---
**Author**: Rahul Yadav
```
