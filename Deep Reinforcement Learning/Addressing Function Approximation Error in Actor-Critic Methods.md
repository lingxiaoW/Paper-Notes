## Twin Delayed DDPG (TD3)
* A modified version of DDPG
* [OpenAI spinning up](https://spinningup.openai.com/en/latest/algorithms/td3.html#background). 

## Abstract
* While DDPG can achieve great performance sometimes, it is frequently brittle with respect to hyperparameters and other kinds of tuning. 
* A common failure mode for DDPG is that the learned Q-function begins to dramatically overestimate Q-values, which then leads to the policy breaking, because it exploits the 
the errors in the Q-function.
* Twin Delayed DDPG (TD3) is an algorithm that addresses this issue by introducing three critical tricks:
  * **Clipped double Q-learning**. TD3 learns two Q-functions instead of one, and use the smaller of the two Q-values to form the targets in the Bellman error loss functions.
  * **Delayed Policy Updates**. TD3 updates the policy (and target networks) less frequently than the Q-function. 
  * **Target Policy Smoothing**. TD3 adds noise to the target action, to make it harder for the policy to exploit Q-function errors by soothing Q along changes in action.

