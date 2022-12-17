# GC_paper
(single-file) implementations for PPO with Generalized Critic (Ensemble critic model)

[Link to experiment logs](https://wandb.ai/rlexp/GC_paper/reports/Experimental-Results--VmlldzoyOTg5NTky)

### Usage

```bash
#script mode (includes experiment tracking with wandb) 
python GC_PPO.py \
--num_critics 1 --env_name HopperBulletEnv-v0 \ 
--kl_rollback --norm_rew --bootstrap --seed 1
```
