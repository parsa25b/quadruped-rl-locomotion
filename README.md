# Training Quadruped Locomotion using Reinforcement Learning in Mujoco

A custom gymnasium environment for training quadruped locomotion using reinforcement learning in the Mujoco simulator. The environment has been set up for the Unitree Go1 robot, however, it can be easily extended to train other robots as well. 

There are two MJCF models provided for the Go1 robot. One tuned for position control with a proportional controller, and one model which directly takes in torque values for end-to-end training. This repository mainly focuses on the model with position controller.

### Trained Model
https://github.com/nimazareian/quadruped-rl-locomotion/assets/99502915/8afddece-8186-4b9d-8352-594dcef4d53d

## Setup
```bash
python -m pip install -r requirements.txt
```

## Train

```bash
python agent.py --mode train
```

## Displaying Trained Models 

```bash
python agent.py --mode train --model_path <path to model zip file>
```

For example, to run a pretrained model which outputs motor position and has the robot desired velocity set to <Vx=1, Vy=0, Wz=0>, you can run:

```bash
python train.py --run test --model_path .\models\2024-04-28_22-10-59=1_pos_ctrl_20mil_iter_walking_with_normal_steps\final_model.zip
```

<details>
  <summary>Additional arguments for customizing training and testing</summary>

    usage: train.py [-h] --run {train,test} [--run_name RUN_NAME] [--num_parallel_envs NUM_PARALLEL_ENVS]
                    [--num_test_episodes NUM_TEST_EPISODES] [--record_test_episodes] [--total_timesteps TOTAL_TIMESTEPS]      
                    [--eval_frequency EVAL_FREQUENCY] [--model_path MODEL_PATH] [--seed SEED]

    optional arguments:
    -h, --help            show this help message and exit
    --run {train,test}
    --run_name RUN_NAME   Custom name of the run. Note that all runs are saved in the 'models' directory and have the       
                            training time prefixed.
    --num_parallel_envs NUM_PARALLEL_ENVS
                            Number of parallel environments while training
    --num_test_episodes NUM_TEST_EPISODES
                            Number of episodes to test the model
    --record_test_episodes
                            Whether to record the test episodes or not. If false, the episodes are rendered in the window.    
    --total_timesteps TOTAL_TIMESTEPS
                            Number of timesteps to train the model for
    --eval_frequency EVAL_FREQUENCY
                            The frequency of evaluating the models while training
    --model_path MODEL_PATH
                            Path to the model (.zip)
    --seed SEED

</details>

## Note

This repository serves for education purposes and is by no mean finalized!
