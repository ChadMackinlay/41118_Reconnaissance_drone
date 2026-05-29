# AI in Robotics: PyBullet Drone RL Control

## Project Overview

This project implements reinforcement learning control for simulated quadrotor drones using PyBullet and Gymnasium. It provides a robust simulation environment with cascaded PID controllers for low-level drone dynamics and high-level reinforcement learning interfaces for training agents to navigate, avoid obstacles, and reach multi-goal targets.

**Key Features:**
- Gymnasium-style environment for RL training
- PyBullet physics simulation with accurate drone dynamics
- Cascaded PID controller for stable flight
- Support for multi-goal waypoint navigation
- Obstacle avoidance capabilities
- Pre-trained PPO models available

## Group Information

### About Us

[To be filled in by the team]

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd AI_In_Robotics-main
```

2. Create and activate a conda environment:
```bash
conda create -n drone-rl python=3.9
conda activate drone-rl
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Verify the installation:
```bash
python scripts/check_project.py
```

## Quick Start

### Run a Random Policy Demo
```bash
python scripts/random_agent_demo.py --gui
```

### Test a Trained Model
```bash
python scripts/test_model.py --gui --debug --model your_model_name.zip
```

### Train Your Own Model
```bash
python train_drone_multi_goal.py
```

## Main pipeline

```text
RL action or waypoint target
    -> CascadedPIDController
    -> QuadrotorMixer
    -> Quadrotor.apply_motor_forces()
    -> PyBullet
```

## RL action format

```python
[action_x, action_y, action_z, action_yaw]
```

Each value should be between `-1.0` and `1.0`.

## Observation format

The environment returns a NumPy array of shape `(16,)`:

```text
position xyz
velocity xyz
roll pitch yaw
angular velocity xyz
relative goal xyz
normalised goal index
```

## Environment options

- `drone_control/env.py` is the main RL environment.
- You can disable obstacles by creating the env with `enable_obstacles=False`.
- You can override goal and obstacle placement with the `goals` and `obstacles` constructor arguments.
- `scripts/test_model.py` supports `--debug` for additional episode termination logging.

## Important files

- `drone_control/config.py`: physics and environment configuration.
- `drone_control/pid.py`: PID/cascaded controller.
- `drone_control/mixer.py`: converts thrust + torque into four motor forces.
- `drone_control/quadrotor.py`: loads the drone URDF and applies motor forces in PyBullet.
- `drone_control/env.py`: Gymnasium-style RL environment.
- `scripts/check_project.py`: smoke test for the RL environment.
- `scripts/random_agent_demo.py`: random-action environment demo.
- `scripts/test_model.py`: evaluation runner for a saved PPO model.
