## Abstract
* Double deep Q-network (DDQN) paper
* The popular Q-learning algorithm is known to overestimate action values since it includes a maximization step over estimated action values, which tends to prefer overestimated to underestimated values. 
* This paper proposes an adaptation to the DQN algorithm that reduces the observed overestimations. 

## Overestimation Problem
* In Q and Deep Q learning, the target ``y`` is calcualted by selecting the action that gives the maximal Q value, such as:
`` y = r + gamma * max_a Q(S_{t+1}, a; theta^-) `` where ``theta^-`` represents parameters in the target network.  
* The max operation makes it more likely to select overestimated values.

## Double DQN
* The idea of Double DQN is to reduce overestimations by decomposing the max operation in the target into action selection and action evaluation. 
* The target in Double DQN is formed as:
`` y = r + gamma * Q(S_{t+1}, argmax_a Q(S_{t+1}, a; theta), theta^-) `` where ``theta^-`` is the target network.
