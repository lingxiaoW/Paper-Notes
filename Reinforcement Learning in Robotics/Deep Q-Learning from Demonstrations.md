https://danieltakeshi.github.io/2019/04/30/il-and-rl/

## Abstract

* RL algorithms may be acceptable for a simulator, but it severely limits the applicability of deep RL to many real-world tasks, where the agent must learn in the real environment. 
* In many real-world settings of RL, we have access to data of the system being operated by its previous controller, but we don't have access to an accurate simulator of the system.
* This paper presents an algorithm, deep Q-learning from demonstration (DDfD), that leverages small sets of demonstration data to massively accelerate the learning process. 
* DQfD works by combining temporal difference updates with supervised classification of the demonstrator's actions. 
* Straightforward solution of performing supervised learning on the demonstration data and then applying RL is not ideal since we want to use the demonstration data continuously throughout training as needed, rather than ignoring it. 

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

* 1-step double Q-learning loss:
  * J_DQ = (R(s,a) + y * Q'(s_{t+1}, a_{t+1}^max) - Q(s,a))^2, 
  * where a_t+1^max = argmax_a Q(s_t+1, a) and Q' is the target Q network
* n-step double Q-learning loss (using forward view, where t is the current time step):
  * J_n = r_t + yr_t+1 + ... + y^{n-1}r_{t+n-1} + max_a y^n Q(s_{t+n}, a)
  * n-step returns helps propagate the values of the expert's trajectory to all the earlier states, learning to better pre-training.
* Supervised large margin classification loss
  * J_E = max_a [Q(s,a) + L(a_E, a)] - Q(s,a_E)
  * where a_E is the action the expert takes at state s,
  * L(a_E, a) is a margin function that is 0 when a=a_E and positive otherwise (where DQfN used 0.8).
  * J_E is designed to make the Q-values of non-demonstrator to be smaller than Q-values that the demonstrator actually took. 
* Loss function: 
  * J(Q) = J_DQ + lamba_1 * J_n + lambda_2 * J_E + lambda_3 * J_L2 (where DQfN sets lambda_1 and lambda_2 as 1 and lambda_3 as 1e-5).


## Algorithm Deep Q-Learning from Demonstrations
* **Inputs**: D (replay buffer): initialized with demonstration data set; theta: initialize weights of behavior network; theta': initialize weights of target network; tau: frequency at which to update target network; k: number of pre-training gradient updates
* **For** steps t in 1,2,3,...,k do
  * Sample a mini-batch of n transitions from D with prioritization
  * Calculate loss J(Q) using target network
  * Perform a gradient descent step to udpate theta (minimize J(Q))
  * if t mod tau = 0 then theta' <- theta
* **End For**
* **For** steps t in 1,2,3,... do
  * Sample action from behavior policy a
  * Play action a and observe (s',r)
  * Store (s,a,r,s') into D, overwriting oldest self-generated transition if over capacity (never remove demonstration data)
  * Sample a mini-batch of n transitions from D with prioritization
  * Calculate loss J(Q) using target network
  * Perform a gradient descent step to update theta
  * if t mod tau = 0 then theta' <- theta
  * s <- s'
* **End For**
