# Maze Solver with Q-Learning

This project implements a Q-Learning-based approach to train an agent to navigate a maze. The agent learns to move through a 2D maze grid from a start point to a designated goal region while optimizing its path using reinforcement learning principles.

## Features

- **Customizable Maze**: Preprocesses maze images to convert them into binary grids.
- **Q-Learning Agent**: Trains the agent using a reward-based approach with adjustable parameters.
- **Dynamic Visualization**: Displays the agent's progress in real-time during training.
- **Path Optimization**: Stores and emphasizes the best path found during training.
- **Flexible Parameters**: Supports configurable learning rate, exploration rate, discount factor, and episode count.

## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
3. [Requirements](#requirements)
4. [Structure](#structure)
5. [Examples](#examples)
6. [License](#license)

## Installation

Clone the repository and install the required dependencies:

```bash
# Clone the repository
git clone https://github.com/your_username/maze-solver-qlearning.git
cd maze-solver-qlearning

# Install dependencies
pip install -r requirements.txt
```

## Usage

1. **Preprocess the Maze**:
   Load a maze image and preprocess it into a binary grid where `1` represents paths and `0` represents walls.

   ```python
   from maze_solver import preprocess_image

   maze = preprocess_image("maze.png")
   ```

2. **Train the Agent**:
   Define start and goal points, and train the agent to solve the maze.

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

3. **Visualize Results**:
   Plot the agent's path and the best path found during training.

   ```python
   from maze_solver import plot_best_path

   plot_best_path(maze, best_path, step=10, end_rect=end_rect, reward=best_reward)
   ```

## Requirements

- Python 3.8+
- Libraries:
  - OpenCV (>=4.7.0)
  - NumPy (>=1.21.2)
  - Matplotlib (>=3.8.0)

Install all dependencies using:

```bash
pip install -r requirements.txt
```

## Structure

```
maze-solver-qlearning/
|│-- maze_solver.py       # Core implementation (functions for training and preprocessing)
|│-- requirements.txt    # Dependency list
|│-- README.md           # Project documentation
|│-- examples/           # Example scripts and data
|│-- tests/              # Unit tests
```

## Examples

### Example Maze Image
Ensure that the input maze is a grayscale image where walls and paths are distinguishable.

```bash
maze.png
```

### Training Output
- **Training Progress**: Shows agent progress at regular intervals.
- **Best Path Visualization**: Highlights the optimal path found during training.

```python
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

### Visualizing Paths

After training, visualize the best path:

```python
plot_best_path(maze, best_path, step=10, end_rect=end_rect, reward=best_reward)
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.