## Abstract
* This paper presents a deep deterministic policy gradient (DDPG) algorithm for operating over continous action spaces.
* DDPG is a combination of DQN and DPG, which is an actor-critic, model free algorithm. 

## Introduction
* DQN is successful but it can only handles discrete and low-dimensional action spaces.
* DDPG can handle problems with continuous action spaces, such as control problems.

## Algorithm
* Similar to DQN, a replay buffer is added, allowing the algorithm to benefit from learning across a set of uncorrelated transitions
* Soft targets: target networks are updated by having them slowly track the learned networks: ``theta' <- tau * theta + (1 - tau) * theta'`` with ``tau << 1``. 
* When learning from different feature vector obervations, different components of the observation may have different physical units (e.g., positions v.s. velocities). 
This can make it difficult for the network to learn effectively.
    * Solution: batch normalization. This technique normalizes each dimension across the samples in a minibatch to have unit mean and variance. 
    * It maintains a running average of the mean and varaince to use for normalization during testing. 
* Exploration: add noises to actor policy. 
