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
  * Very high sample complexity (even simple tasks can require millions of steps of data collection, and complex behaviors with high-dimensional observations might need substantially more);
  * Brittle convergence properties (RL methods are brittle with respect to their hyperparameters)
* In the soft actor-critic framework, the actor aims to maxmize expected reward while also maximizing entropy. 
  * That is, to succeed at the task while acting as randomly as possible. 
  * Combine off-policy updates with a stable stochastic actor-critic formulation. 

## Introduction
* Use maximum entropy framework, which augments the standard maximum reward reinforcement learning objective with an entropy maximization term to improve exploration.
* Soft actor-critic incroporates three key ingredients: 
  * an actor-critic architecture with separate policy and value function networks;
  * an off-policy formulation that enables reuse of previously collected data for efficiency;
  * entorpy maximization to enable stability and exploration. 

## From Soft Policy Iteration to Soft Actor-Critic
* Policy iteration: policy evaluation + policy improvement.
  * Policy evaluation: we wish to compute the value of a policy ``pi`` according to the maximum entropy objective. 
    * ``Q(s_t, a_t) = r(s_t, a_t) + gamma * E_{s_{t+1} ~ p}[V(s_{t+1})]`` where ``V(s_t)=E_{a_t~pi}[Q(s_t, a_t)-log pi(a_t|s_t)]``
  * Policy improvement: we update the policy towards the exponential of the new Q-function (this particular choice of update can be guaranteed to result in an improved policy in terms of its soft value).
    * Use Kullback-Leibler divergence to restrict the policy to some set of policies. 
* Soft actor-critic
  * Use function approximators for both the state value ``V(s)``, Q-function ``Q(s,a)``, and a tractable policy ``pi(a|s)`` (for continuous action space, the output fo the policy network could be Gaussian with mean and covariance given by neural networks).
  * The updating equations of three networks can be found in paper. 

         
