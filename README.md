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

- Dynamic Programming
  - advantages:
    - can be applied to a broad range of **universal** system models
    - Various different terms can be easily **integrated into the cost function**
    - even **non convex optimization problems** can be solved globally
  - disadvantages:
    - due to the **curse of dimensionality**, is very limited to small order system models
    - not possible to generate trajectories online that are sufficiently smooth to be used as system inputs for vehicle applications
  - to combine Dynamic Programming with other optimization methods
    - [34] Path planning on grid maps with unknown goal poses
    
- Indirect Methods
  - can only be applied to local optimization problems
  - show great potential with respect to trajectory generation in some special cases
    - [19] Automatic collision avoidance during parking and maneuvering - an optimal control approach.
    
- Direct Methods
  - convert **the optimal control problem (OCP)** into **nonlinear programming (NLP)** that can be solved using numerical NLP solvers.
  - are very adequate for finding local solutions to nonlinear problems in real-time
    - [39] Automatic collision avoidance using model-predictive online optimization
    - [41] Trajectory planning for Bertha - A local, continuous method
    - [15] Semi-autonomous vehicle control for road departure and obstacle avoidance
    - [14] Spatial predictive control for agile semi-autonomous ground vehicles
  - Apart from Interior Point Methods, **sequential quadratic programming (SQP)-solvers** are well-established for solving NLPs
  - solving NLPs is very **time-consuming**, as these solvers brake down the NLP into **smaller linear-quadratic programs (QP)** that are solved iteratively using forward simulation of the system dynamics
  
- to reduce the computational effort
  - [10] suggests the formulation of linear-quadratic optimal control problems for trajectory generation.
    - [10] A linear time varying model predictive control approach to the integrated vehicle dynamics control problem in autonomous systems
      - no iterations and no initial starting guess
      - only a single QP-problem
      - makes the use of **linear model predictive control (LMPC)** highly favorable for **real-time trajectory generation** with high replanning frequencies.
      - to apply LMPC to the **lateral vehicle guidance problem**
        - [20], [21] and [11] use LMPC for designing a lateral vehicle controller for tracking a given collision free evasive path
          - [20] Ltv-mpc approach for lateral vehicle guidance by front steering at the limits of vehicle dynamics
          - [21] Optimal vehicle dynamics control for combined longitudinal and lateral autonomous vehicle guidance
          - [11] Active front steering using stable model predictive control approach
      - include the collision avoidance functionality into the **reference tracking concept**, by separating the lateral vehicle guidance task into a high-level trajectory generation layer for collision avoidance and a low-level control layer for stabilizing the vehicle
        - [9] A hierarchical model predictive control framework for autonomous ground vehicles
        - [14] Spatial predictive control for agile semi-autonomous ground vehicles
        
- Similar to our work
  - using LMPC for trajectory optimization for lateral vehicle guidance
    - [1] An optimal-control-based framework for trajectory planning, threat assessment, and semi-autonomous control of passenger vehicles in hazard avoidance scenarios
    
- In contrast to our approach
  - the optimal control problem is formulated only for straight roads and constant speeds
    - in [28], where the linear system is chosen such that the vehicle heading is used as a system input resulting in kinodynamically infeasible trajectories
      - [28] Ltv-mpc based path planning of an autonomous vehicle via **convex optimization**.
    - In [35], a problem formulation is presented that allows for path tracking of low curvature roads
      - [35] Linear model predictive control for lane keeping and obstacle avoidance on low curvature roads
- generate trajectories that are similar to **human driving behavior**
    - [36] A behavioral planning framework for autonomous driving  
  - **minimize the lateral vehicle jerk** and **limiting the lateral vehicle acceleration** dependent on the current curvature value
    - [17] Toward human-like motion planning in urban environments
  - to **allow offsets** to a given reference under consideration of the vehicles environment
    - [26] Combining local trajectory planning and tracking control for au-tonomous ground vehicles navigating along a reference path
    - [25] A novel path tracking controller for ackerman steering vehicles
