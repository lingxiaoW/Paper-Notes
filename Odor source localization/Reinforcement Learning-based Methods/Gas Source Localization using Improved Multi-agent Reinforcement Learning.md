## Abstract
* This paper presents a method that combines the STE (source term estimation) using static SN and source seeking with mobile sensors. 

## Multi-agent RL in OSL
* In order to improve the efficiency and find the actual target source, multi-agent RL uses multiple agents to share experience and exchange information. 
* In multi-agent RL, a sharing Q-table method is implemented. 
  * In the shared Q-table, ``N`` Q values (where ``N`` is the number of agents) are combined using the weighted sum, where the weight is determined by the measured gas concentration.
* The agent are independent decision makers. Actions are determined based on a Boltzmann exploration procedure (similar to epsilon-greedy).
* Reward is designed based on two aspects:
  * 1. the comparison of the agent's individually measured gas concentration between two step;
  * 2. the difference between the current gas concentration measured by itself and the highest one in the group.
* Not deep reinformcement learning and no real-world experiments.
* Very simple simulation environment.

