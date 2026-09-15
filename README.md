# Flappy Bird Reinforcement Learning Agent 🐦🤖

> A deep reinforcement learning agent trained to master Flappy Bird using Deep Q-Learning (DQN), achieving optimal obstacle-avoidance strategies directly from game state vectors.

---

## 🏗️ System Architecture & Workflow

The reinforcement learning feedback loop handles continuous state observation, action execution, and reward optimization:

```text
       ┌────────────────────────────────────────────────────────┐
       │                        Action                          │
       ▼                                                        │
┌─────────────┐    State (Bird Pos, Gaps)    ┌───────────────────┐    │
│   Flappy    │ ──────────────────────────> │   Neural Network  │    │
│    Bird     │                             │    / RL Agent     │    │
│ Environment │ <────────────────────────── └───────────────────┘    │
└─────────────┘          Reward (+1 / -100)                     <┘
Complete Step-by-Step Breakdown:
State Observation: The environment feeds current game metrics (bird altitude, velocity, and distance to upcoming pipe gaps) into the agent.

Action Decision: The Neural Network evaluates the state and chooses whether to FLAP or stay IDLE.

Environment Execution: The game physics engine applies the action and advances the frame.

Reward & Optimization: The agent receives performance feedback—+1 for surviving/scoring and -100 for crashing—allowing the model to optimize its policy weights over time.

✨ Key Technical Highlights
Custom Environment Integration: Built using Pygame and Gym wrappers to extract precise game states and frame rates for efficient agent training.

Reward Shaping: Engineered a custom reward function that incentivizes survival time and successful pipe clearance while penalizing collisions.

Experience Replay & Exploration: Implemented epsilon-greedy exploration strategy with decaying epsilon and experience replay memory to stabilize Q-value convergence.

Model Checkpointing: Automatically saves model weights at high score milestones for seamless resumption and evaluation.

🧰 Tech Stack
Language: Python 3.x

Deep Learning: PyTorch, NumPy

Environment: Pygame, Gymnasium / Custom RL Wrapper

Visualization: Matplotlib, TensorBoard (for reward and loss curves)

🚀 Getting Started & Quick Start
Follow these steps to set up the repository and train or watch the agent locally.

Prerequisites
Make sure you have Python installed. It is recommended to use a virtual environment:

Bash
# Clone the repository
git clone [https://github.com/sujeetgupta19s2gt-dev/flappy-bird-rl.git](https://github.com/sujeetgupta19s2gt-dev/flappy-bird-rl.git)
cd flappy-bird-rl

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
Running Training
To train the RL agent from scratch:

Bash
python train.py --episodes 1000 --render_interval 100
Running Evaluation / Play Mode
To watch your pre-trained agent play Flappy Bird in real-time:

Bash
python play.py --checkpoint checkpoints/best_model.pth
📈 Results & Visualizations
Below is a sample progression of the agent's performance during training:

Training Phase	Average Score	Max Score Achieved
Initial (Random Actions)	0 - 2	3
Mid-Training (Policy Refinement)	25 - 50	85
Converged Agent (Optimal)	500+	1,250+
📂 Repository Structure
Plaintext
flappy-bird-rl/
│
├── assets/             # Game sprites, GIFs, and performance plots
├── configs/            # Hyperlearning & architecture configuration files
├── environment/        # Flappy Bird game logic and gym wrapper
├── models/             # Deep Q-Network / Policy network definitions
├── checkpoints/        # Saved model weights (.pth or .h5)
├── train.py            # Main training loop script
├── play.py             # Inference and rendering script
├── requirements.txt    # Project dependencies
└── README.md           # Project documentation
🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.
