## Abstract

* RL algorithms may be acceptable for a simulator, but it severely limits the applicability of deep RL to many real-world tasks, where the agent must learn in the real environment. 
* In many real-world settings of RL, we have access to data of the system being operated by its previous controller, but we don't have access to an accurate simulator of the system.
* This paper presents an algorithm, deep Q-learning from demonstration (DDfD), that leverages small sets of demonstration data to massively accelerate the learning process. 
* DQfD works by combining temporal difference updates with supervised classification of the demonstrator's actions. 

## Deep Q-Learning from Demonstrations

* We want the agent to learn as much as possible from the demonstration data before running on the real system (i.e., pre-train). 
* The goal of the pre-training phase is to learn to imitate the demonstrator with a **value function** that satisfies the Bellman equation so that it can be updated with TD updates
once the agent starts interacting with the environment.
* During the pre-training phase, the agent samples mini-batches from the demonstration data and updates the network by applying four losses:
  * 1-step double Q-learning loss
  * n-step double Q-learning loss
  * a supervised large margin classification loss
  * L2 regularization loss

* The supervised loss is used for classification of the demonstrator's actions, while the Q-learning loss ensures that the network satisfies the Bellman equation and can be
used as a starting point for TD learning. Regularization loss is to prevent the overfitting on a small scale demonstration data.

* Double Q-learning loss:
  * <img src="https://render.githubusercontent.com/render/math?math=e^{i \pi} = -1"> v v
