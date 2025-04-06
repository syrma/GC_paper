# GC_paper
(single-file) implementations for PPO with Generalized Critic (Ensemble critic model)

[Link to experiment logs](https://wandb.ai/rlexp/GC_paper/reports/Experimental-Results--VmlldzoyOTg5NTky)

### Usage

```
GC_PPO.py [-h] [--kl_stop] [--kl_rollback] [--bootstrap] [--norm_rew]
                 [--norm_obs] [--load_dir LOAD_DIR] [--env_name ENV_NAME]
                 [--save_dir SAVE_DIR] [--num_critics NUM_CRITICS]
                 [--seed SEED [SEED ...]]
                 [--wandb_project_name WANDB_PROJECT_NAME]
                 [test]

Train or test PPO

positional arguments:
  test                  Test a saved or a random model

options:
  -h, --help            show this help message and exit
  --kl_stop             Early stopping
  --kl_rollback         Include early stopping with rollback in the training
  --bootstrap           Include bootstrapping when fitting the critic networks
  --norm_rew            Include Reward Scaling optimization
  --norm_obs            Include Observation Normalization optimization
  --load_dir LOAD_DIR   Optional: directory of saved model to test or resume
                        training
  --env_name ENV_NAME   Environment name to use with OpenAI Gym
  --save_dir SAVE_DIR   Optional: directory where the model should be saved
  --num_critics NUM_CRITICS
                        Number of critics
  --seed SEED [SEED ...]
                        Seed
  --wandb_project_name WANDB_PROJECT_NAME
                        Project name for Weights & Biases experiment tracking
```

Example:

```bash
$ python GC_PPO.py \
--num_critics 1 --env_name HopperBulletEnv-v0 \ 
--kl_rollback --norm_rew --bootstrap --seed 1
```

### Dependencies

- python 3 (3.12 or older)
- tensorflow 2.19
- gym (0.25 or older)
- tf_keras
- tensorflow_probability
- pybullet


We recommend running the script with [uv](https://github.com/astral-sh/uv) as it will automatically manage dependencies/versions (including python) without interferring with your system installation.

The previous example becomes as follows:

```bash
$ uv run GC_PPO.py \
--num_critics 1 --env_name HopperBulletEnv-v0 \ 
--kl_rollback --norm_rew --bootstrap --seed 1
```

### Notebook

A notebook version (.ipynb) can be used to test the algorithm in a simpler, more interactive environment, without the need to track the experiment on wandb. It can also be viewed fully online on [Collab](https://colab.research.google.com/drive/17n107Iv5EmYnvcmACqZBA_8U_G5zkQ1e?usp=sharing).
