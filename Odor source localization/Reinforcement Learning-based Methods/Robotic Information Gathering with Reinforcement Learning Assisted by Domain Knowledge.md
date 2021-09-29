## Abstract
* We propose a solution that assists Reinforcement Learning with existing domain knowledge based on a model of the gas dispersion process. 
* Furthermore, the framework developed in this work can also be generalized to a large variety of information gathering tasks.


## Introduction
* This work proposes an algorithmic framework to solve robotic IG (information gathering) and enhance it by exploiting a priori domain knowledge about the environment. 
* In particular, we will show how to make use of a mathematical model in order to (i) shape the reward and (ii) to enhance the observation for the RL framework.

## Problem Statement
* Divide the search domain into ``C`` cells arranged in a regular grid.
* Each grid cell ``c`` is indexed by ``x_c``, ``y_c`` to define its position in teh grid. For each individual cell, we define two values ``f_c`` and ``u_c``, where ``f_c`` donates the gas concentration at ``x_c``, ``y_c``. Value ``u_c`` denotes the gas source strength, which has a value of 0 for those cells that do not contain a gas source.
* ``f_c`` is measurable using a sensor. In contrast, the gas source strength ``u_c`` is not directly measurable, and only be inferred from gas concentration measurements. 
* The goal of the mobile robot is to collect a sufficient amount of measurements so that we can accurately estimate the gas concentration ``f`` and source distribution ``u`` based on an inverse model of the gas dispersion process. 

## Reinforcement Learning Assisted by Domain Knowledge
* The whole system contains a forward model and an inverse model. 
  * The Forward model simulates the gas concentration distribution from a known source location and wind information; 
  * The measurements are fed into the inverse model to estimate the whole gas concentration and source distribution as well as the uncertainty map ``u``. 
  * The estimates are used to define the reward and observation for the RL algorithm which are used to train the movement policy. 
