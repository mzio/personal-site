---
title: "PersonalEnv Setup"
date: 2019-03-28T14:32:57-04:00
draft: true
summary: "Notes on creating PersonalEnv, a personalization RL locomotion environment on top of Gym and PyBullet."
tags: ["PersonalEnv", "Reinforcement Learning"]
---

# Comparisons between PyBullet-Gym MuJoCo and Roboschool implementations

### Environments

- The `env_bases` classes are the same, along with the `humanoid_env` class.
  - This suggests that differences are just in the actual `humanoid` model.

### Robots / Agents

- `robot_bases`:

  - The MuJoCo implementation has an extra attribute `self.add_ignored_joints` and initial parameter `add_ignored_joints=False`
  - MuJoCo version also has extra code for if a joint is ignored. See [line 83](https://github.com/benelot/pybullet-gym/blob/master/pybulletgym/envs/mujoco/robots/robot_bases.py)

- `walker_base`:
  - Roboschool implementation has tries to run `self.scene.actor_introduce(self)` and passes if there's an error. MuJoCo just has that without the `try ... except` statement.
