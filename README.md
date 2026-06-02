# AI in Robotics: Reconnaissance Drone

## Project 

AI in Robotics: PyBullet Drone RL Control

A reinforcement learning project for simulated quadrotor drones using PyBullet and Gymnasium. The repository includes the RL environment, controllers, and evaluation scripts for training and testing drone navigation and obstacle avoidance.

## Resources

- Repository: `https://github.com/ChadMackinlay/41118_Reconnaissance_drone`
- Code: `drone_control/`, `scripts/`, `train_drone_multi_goal.py`,  `yolo_test.py`
- Dependencies: `requirements.txt`
- Models and checkpoints: `checkpoints/`, `*.zip`
- Example scripts: `scripts/check_project.py`, `scripts/random_agent_demo.py`, `scripts/test_model.py`

## Install Info

1. Clone the repository:
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
4. Verify installation:
```bash
python scripts/check_project.py
```

## Run Commands

### Run a random policy demo
```bash
python scripts/random_agent_demo.py --gui
```

### Test a trained model
```bash
python scripts/test_model.py --gui --debug --model your_model_name.zip
```

### Train a model
```bash
python train_drone_multi_goal.py
```

### Run the model
```bash
python yolo_test.py
```
