## Abstract

The paper presents a model-free reinforcement learning on real robotics with sparse rewards. It combines the deep deterministic policy gradient (DDPG) with human demonstration: by adding humn demonstrations in the replay buffer of DDPG training process. Both human demonstrations and actual interactions (from neural networks conducted in simulation) are used to fill a replay buffer.

The add of human demonstrations replaces the need for carefully engineered rewards, and reduce the exploration problem encountered by classical RL approaches in these domains.


## DDPG from Demonstrations (DDPGfD)
The algorithm modifies DDPG to take advantage of demonstrations. DDPGfD loads the demonstration transitions into the replay buffer before the training begins and keeps all transitions forever. It modifies the DDPG in the following ways:

1) Transitions from a human demonstrator are added to the replay buffer;
2) Sampling from replay buffer are prioritized. The probability of sampling a transition is proportional to its priority, which is the sum of TD error, actor loss, a small constant to ensure all transitions being sampled, and a positive constant to increase the probability of human demonstrations being sampled; 
3) The critic learns a mix of a single step return, n-step returns, and a L2 regularization;
4) Learning multiple times per environment step (this means increasing the frequency of minibatch updates relative to environment steps);

    L1 and L2 regularization: adds penalty as model compleixty increases to prevent overfit.
    L1 regularization: |omega|, where omega is the coefficient of a neural network. 
    L2 regularization: omega^2, where omega is the coefficient of a neural network. 
    The difference is that L1 shrinks the less important feature's coefficient to zero thus, removing some features altogether. 
