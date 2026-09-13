# Flappy Bird Deep Q-Network (DQN) Reinforcement Learning

A Deep Q-Learning (DQN) project built from scratch using PyTorch and Gymnasium to train an intelligent agent to play **Flappy Bird**. This implementation incorporates foundational reinforcement learning concepts including experience replay memory, target network synchronization, and an epsilon-greedy exploration decay strategy.

---

## Project Architecture & Implementation Steps

Based on the core algorithmic design, the implementation follows these structural steps:

1. **Environment Integration**: Sets up the reinforcement learning loop using `gymnasium` and `flappy_bird_gymnasium` (`FlappyBird-v0`).
2. **DQN Neural Network Architecture (`dqn.py`)**: Implements a feed-forward multi-layer perceptron via PyTorch's `nn.Sequential` mapping state vectors to discrete action-value predictions.
3. **Experience Replay Memory (`experience_replay.py`)**: Utilizes a FIFO queue (`deque`) of fixed capacity to store agent transitions and sample random mini-batches, breaking temporal correlations during training.
4. **Target Network Syncing**: Maintains a secondary target network decoupled from the policy network, updated periodically to stabilize learning targets.
5. **Epsilon-Greedy Exploration Policy**: Balances exploration and exploitation dynamically, utilizing an exponential decay function down to a defined minimum threshold.
6. **Training Loop & Optimization**: Iterates across multiple episodes optimizing mean squared error (MSE) loss using the Adam optimizer.
7. **Model Checkpointing & Testing**: Automatically logs performance metrics and persists the best-performing model weights (`.pt`) for evaluation and rendering.

---

## Project Structure

```text
FLAPPY BIRD RL/
│
├── agent.py              # Main Agent class, training/evaluation loops, and CLI entry point
├── dqn.py                # Deep Q-Network architecture definition
├── experience_replay.py  # FIFO experience replay memory buffer
├── parameters.yaml       # Hyperparameter sets and environment configuration
├── requirements.txt      # Python package dependencies
└── .gitignore            # Git exclusion rules for cache and runtime files
