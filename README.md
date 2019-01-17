# Robotics-Control-02-Constrained-Linear-Time-Varying-MPC
Paper reading: 'Robotics-Control-02-Constrained-Linear-Time-Varying-MPC'

### Abstract
- Formulating the system dynamics linearly in combination with a **quadratic cost function** has two great advantages:
  - not only to achieve **collision avoidance** with both static and dynamic obstacles, 
  - but also aspects of **human driving behavior** can be considered.
  - can be solved very **efficiently**
  - Additionally, due to an elaborate problem formulation, reference curves with discontinuous, **high curvatures will be effortlessly smoothed out** by the algorithm.
- applicable to different **traffic scenarios**
  - parking
  - highway driving

### INTRODUCTION
- Related works
  - driver in various **monotonous** and challenging driving situations, see [33] and [27].
    - [27] A perspective on emerging automotive safety applications, derived from lessons learned through participation in the darpa grand challenges.
    - [33] An evaluation of driver reactions to new vehicle parking assist technologies developed to reduce driver stress.
  - focuses on trajectory generation algorithms that can cope with **complex traffic featuring dynamic, time-critical street scenarios, such as merging into fast traffic flow, to pass opposing traffic, or to avoid other moving vehicles** [38]
    - [38] Optimal trajectories for time-critical street scenarios using discretized terminal manifolds
  - **human** driving behavior
    - [17] Toward human-like motion planning in urban environments
    - [26] Combining local trajectory planning and tracking control for au-tonomous ground vehicles navigating along a reference path
  - **rule-based** methods: for isolated dynamic traffic scenarios
    - [37] A robust algorithm for handling moving traffic in urban scenarios
      - When trying to integrate these heuristics into a universal concept, these approaches quickly **reach their limits** resulting in poor performance or even accidents
        - [13] The MIT-Cornell collision and why it happened
  - **potential field** methods
    - [7] A predictive potential field concept for shared vehicle guidance
    - [23] A generalized potential field approach to obstacle avoidance control
      - there are still open issues as **system dynamics and constraints** are difficult to integrate within this approach.
        - [22] Potential field methods and their inherent limitations for mobile robot navigation
  - **optimization techniques** have been applied successfully
    - [16] On-road motion planning for autonomous vehicles
    - [1] An optimal-control-based framework for trajectory planning, threat assessment, and semi-autonomous control of passenger vehicles in hazard avoidance scenarios
    - [31] Obstacle avoidance of autonomous vehicles based on model predictive control
    - [38] Optimal trajectories for time-critical street scenarios using discretized terminal manifolds
