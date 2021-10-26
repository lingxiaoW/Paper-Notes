## Abstract
* We propose a solution that assists Reinforcement Learning with existing domain knowledge based on a model of the gas dispersion process. 
* Incorporate a priori domain knowledge (from physics) by designing appropriate rewards and observation inputs for the RL algorithm. 

## Introduction
* This work proposes an algorithmic framework to solve robotic IG (information gathering) and enhance it by exploiting a priori domain knowledge about the environment. 
* In particular, this paper shows how to make use of a mathematical model to 
  * (i) shape the reward and 
  * (ii) to enhance the observation for the RL framework.
* This idea is motivated by the hypothesis that it is of advantage to provide priori ifnromation available to the robot with otherwise has to be learned with high effort.

## Problem Statement
* Divide the search domain into ``C`` cells arranged in a regular grid.
* Each grid cell ``c`` is indexed by ``x_c``, ``y_c`` to define its position in teh grid. For each individual cell, we define two values ``f_c`` and ``u_c``, where ``f_c`` donates the gas concentration at ``x_c``, ``y_c``. Value ``u_c`` denotes the gas source strength, which has a value of 0 for those cells that do not contain a gas source.
* ``f_c`` is measurable using a sensor. In contrast, the gas source strength ``u_c`` is not directly measurable, and only be inferred from gas concentration measurements. 
* The goal of the mobile robot is to collect a sufficient amount of measurements so that we can accurately estimate the gas concentration ``f`` and source distribution ``u`` based on an inverse model of the gas dispersion process. 

## Reinforcement Learning Assisted by Domain Knowledge
* The whole system contains a forward model and an inverse model. 
  * The Forward model simulates the gas concentration distribution from a known source location and wind information; 
  * The measurements are fed into the inverse model to estimate the whole gas concentration and source distribution as well as the uncertainty map ``u``. 
  * The estimates are used to define the reward and observation for the RL algorithm which are used to train the movement policy (i.e., model-based rewards).

## Model-based reward
* The definition of reward uses the gas concentration estimate ``f_hat``, the source estimate ``u_hat``, and the uncertainty map ``h_hat`` (i.e., the variance of the concentration). 
* The actual gas concentration is compared with the estimated value, i.e., ``f_hat-f``, and the reward is defined according to this difference. 
