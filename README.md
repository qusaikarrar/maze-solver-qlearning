# Maze Solver with Q-Learning

This project implements a Q-Learning-based approach to train an agent to navigate a maze. The agent learns to move through a 2D maze grid from a starting point to a designated goal region, optimizing its path using reinforcement learning principles.

## Features

- **Customizable Maze**: Convert maze images into binary grids for analysis.
- **Q-Learning Agent**: Train the agent using a reward-based approach with adjustable hyperparameters.
- **Dynamic Visualization**: Real-time visualization of the agent's learning progress and paths.
- **Path Optimization**: Identifies and emphasizes the best path found during training.
- **Flexible Parameters**: Configure learning rate, exploration rate, discount factor, and episode count for fine-tuned training.

---

## Table of Contents

1. [Installation](#installation)  
2. [Usage](#usage)  
3. [Requirements](#requirements)  
4. [Structure](#structure)  
5. [Examples](#examples)  
6. [License](#license)  

---

## Installation

Clone the repository and install the required dependencies:

```bash
# Clone the repository
git clone https://github.com/qusaikarrar/maze-solver-qlearning.git
cd maze-solver-qlearning

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

### 1. Preprocess the Maze
Convert a maze image into a binary grid where `1` represents paths and `0` represents walls.

```python
from maze_solver import preprocess_image

maze = preprocess_image("maze.png")
```

### 2. Train the Agent
Define the start position and goal region, and train the agent to solve the maze.

```python
from maze_solver import train_agent

start = (10, 10)  # Starting point
end_rect = ((380, 200), (399, 220))  # Goal region

q_values = train_agent(
    maze, start, end_rect,
    episodes=5000,
    alpha=0.5,
    gamma=0.7,
    epsilon=0.3,
    step=10,
    visual_interval=100,
    max_steps=1000
)
```

### 3. Visualize Results
Plot the agent's path and the best path found during training.

```python
from maze_solver import plot_best_path

plot_best_path(maze, best_path, step=10, end_rect=end_rect, reward=best_reward)
```

---

## Requirements

- **Python**: 3.8+  
- **Libraries**:  
  - OpenCV (>=4.7.0)  
  - NumPy (>=1.21.2)  
  - Matplotlib (>=3.8.0)  

Install dependencies using:

```bash
pip install -r requirements.txt
```

---

## Structure

```
maze-solver-qlearning/
├── maze_solver.py       # Core implementation (training and preprocessing functions)
├── requirements.txt     # Dependency list
├── README.md            # Project documentation
├── examples/            # Example scripts and data
├── tests/               # Unit tests for validation
```

---

## Examples

### Example Maze Image
Ensure that the input maze is a grayscale image with distinguishable walls and paths.

Example:
```
maze.png
```

### Training Output
After training, observe detailed metrics and progress logs such as:

```bash
Training Summary:
Starting point: (10, 10)
Target region: ((380, 200), (399, 220))
Number of episodes: 5000
Learning rate (alpha): 0.5
Discount factor (gamma): 0.7
Initial exploration rate (epsilon): 0.3
Exploration rate when target first reached: 0.1487
Total times the agent reached the target: 120
Best reward achieved: 690.00
```

---

## Visualizing Paths

Visualize the agent’s best path after training:

```python
plot_best_path(maze, best_path, step=10, end_rect=end_rect, reward=best_reward)
```

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for more details.
