## OpenAI Spinning up
* [Link](https://spinningup.openai.com/en/latest/algorithms/sac.html)
* Soft actor critic (SAC) is an algorithm that optimizes a stochastic policy in an off-policy way, forming a bridge between stochastic policy optimization and DDPG-style approaches.
* A central feature of SAC is entropy regularization. 
  * The policy is trained to maximize a trade-off between expected return and **entropy**, a measure of randomness in the policy 
  * This has a close connection to the exploration-exploitation trade-off: increasing entropy results in **more exploration**, which can accelerate learning later on.
  * It can also prevent the policy from prematurely converging to a bad local optimum. 
* Entropy-regularized RL
  * Entropy says how random a random variable is: if a coin is weighted so that it almost always comes up heads, it has lower entropy; if it's evenly weighted and has a half chance of either outcome, it has high entropy.
  * Let ``x`` be a random variable with probability mass or density function ``P``. The entropy ``H`` of ``x`` is: ``H(p) = E_{x~p}[-logP(x)]``
  * In entropy-regularized RL, the agent gets a bonus reward at each time step proportional to the entropy of the policy at that timestep.  
* Soft Actor-Critic
  * SAC concurrently learns a policy ``pi_theta`` and two Q-functions ``Q1`` and ``Q2``.
  * Learning Q:
    * Like TD3, both Q-functions are learned with mean square Bellman error (MSBE, i.e., TD error) minimization, by regressing to a single shared target.
    * Like TD3, the shared target is computed using target Q-networks.
    * Like TD3, the shared target makes use of the **clipped double-Q** trick
    * Unlike TD3, the target also comes a term: entropy regularization
    * Unlike TD3, the next-state actions used in the target come from the current **current policy** instead of a target policy
    * Unlike TD3, there is no target policy smoothing, i.e., no noises adding on teh actor policy. 

## Abstract
* RL suffer from two major challenges: 
 * Very high sample complexity;
 * Brittle convergence properties 
* In the soft actor-critic framework, the actor aims to maxmize expected reward while also maximizing entropy. 
 * That is, to succeed at the task while acting as randomly as possible. 
 * Combine off-policy updates with a stable stochastic actor-critic formulation. 

## Introduction
* Use maximum entropy framework, which augments the standard maximum reward reinforcement learning objective with an entropy maximization term to improve exploration.
* 

         
