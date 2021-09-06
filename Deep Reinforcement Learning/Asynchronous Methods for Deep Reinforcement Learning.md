## Abstract

* This paper presents asynchronous variants of four standard reinforcement learning algorithms: one-step Sarsa, one-step Q-learning, n-step Q-learning, and advantage actor-critic. 
* The best perfroming method is an asynchronous variant of actor-critic.
* Instead of experience replay, they asynchronously execute multiple agent in parallel, on multiple instances of the environments.
* Instead of running on multiple machines, their asynchronous methods run on a single machine with a standard multi-core CPU.

## Asynchronous RL Framework
* Goal: find RL algorithms that can train deep neural network policies reliably and without large resource requirements. 
* Having multiple actors-learners running in parallel are likely to be exploring different parts of the environment.
* Use n-step forward return to update the policy (i.e., actor)network.
* Network structure: a convolutional neural network that has one softmax output for the policy network and one linear output for the value function with all non-output layers shared.


