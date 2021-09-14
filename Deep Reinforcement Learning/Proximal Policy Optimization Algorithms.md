## OpenAI Spinning up
* [link](https://spinningup.openai.com/en/latest/algorithms/ppo.html)
* PPO is motivated by the same question as TRPO: how can we take the biggest possible improvement step on a policy using teh data we currently have, without stepping so far that
we accidentally cause performance collapse? PPO is a family of first-order methods that use a few other tricks to keep new policies close to old. PPO methods are significantly 
simpler to implement, and empirically seem to perfrom at least as well as TRPO.
* PPO-Penalty and PPO-Clip: 
    * PPO-Penalty approximately solves a KL-constrained update like TRPO, but penalizes the KL-divergence in the objective function instead of making it a hard constraint, 
    and automatically adjusts the penalty coefficient over the course of training so that it's scaled appropriately.
    * PPO-Clip: doesn't have KL-divergence term in the objective and does not have a constraint at all. Instead relies on specialized clipping in the objective function to remove 
    incentives for the new policy to get far from the old policy. 
* PPO is an on-policy algorithm
