## Twin Delayed DDPG (TD3)
* A modified version of DDPG
* [OpenAI spinning up](https://spinningup.openai.com/en/latest/algorithms/td3.html#background). 

* While DDPG can achieve great performance sometimes, it is frequently brittle with respect to hyperparameters and other kinds of tuning. 
* A common failure mode for DDPG is that the learned Q-function begins to dramatically overestimate Q-values, which then leads to the policy breaking, because it exploits the 
the errors in the Q-function.
* Twin Delayed DDPG (TD3) is an algorithm that addresses this issue by introducing three critical tricks:
  * **Clipped double Q-learning**. TD3 learns two Q-functions instead of one, and use the smaller of the two Q-values to form the targets in the Bellman error loss functions.
  * **Delayed Policy Updates**. TD3 updates the policy (and target networks) less frequently than the Q-function. 
  * **Target Policy Smoothing**. TD3 adds noise to the target action, to make it harder for the policy to exploit Q-function errors by soothing Q along changes in action.

## Abstract
* In value-based RL mehods, such as deep Q-learning, function approximation errors are known to lead to overestimated value estimates and suboptimal policies. This problem remains in the actor-critic settings.
* This paper proposes a method to minimize the overestimation problem via double Q-learning, by taking minimum value between a pair of critics to limit over-estimation. 
* Besides, delaying policy updates to reduce per-update error and further improve performance. 

## Introduction
* How Double DQN solves the problem of overestimation in Q-value? 
  * Double DQN estimates the value of current policy with a separate target value function, allowing actions to be evaluated without maximization bias. 
* This setting cannot be adopted to an actor-critic setting. Since the slow-changing policy in an actor-critic setting, the curretn and target value estimates remain too similar to avoid maximization bias.

## Overestimation Bias
* In Q-learning, the value estimate is updated with a greedy target ``y = r + gamma * max_a'Q(s',a')``. However, if the target is susceptible to error ``epsilon``, then the maximum over the value along with its error will generally be greater than the true maximum. 
* Overestimation of values also appears in actor-critic settings.
* Clipped Double Q-learning for actor-critic
  * Learn a pair of actors (pi1 and pi2) and critics (Q1 and Q2)
  * Form the value target via ``y1 = r + gamma * min_{i=1,2}Q_i(s', pi1(s'))``

## Addressing Variance
* Besides the impact on overestimation bias, high variance estimates provide a noisy gradient for the policy update. 
* Policy network should be updated at a lower frequency than the value network, to first minimize error in value network before introducing a policy update.
  * Delaying policy updates until the value error is as small as possible. 
  * The modification is to only update the policy and target networks after a fixed number of updates ``d`` to the critic. 
* Target policy smoothing regularization
  * Deterministic policies can overfit to narrow peaks in the value estimate.
  * Similar actions should have similar value.
  * Adding a small amount of random noise to the target policy to force the value network learn similar target values, i.e., smoothing the value estimate. 
