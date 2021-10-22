## Abstract
* This paper demonstrates the phototaxis of a nano drone in an obstacle field. The drone is directed by a deep reinforcement learning model, and by carefully designing the network 
inputs, the inference frequency is up to 100 Hz.

## Method
* Design a source-seeking nano drone for finding the light source.
* The drone carries a light sensor, a multiranger to detect obstacles, a flow deck to track its motion. 
* The simultion environment is called Air Learning.
* Inputs of the deep neural network include:
  * Range readings from the multiranger (4 variables, L1 to L4)
  * S1 and S2, which are calculated from the light intensity measurement, where s1 represents the gradient of the light intensity and s2 represents the distance to the source.
* Outputs of the depp nueral network include three actions, commanding the drone to move forward, left, and right.
* Rewards: positive reward for finidng the source; negative reward for failed finding the source; positive reward for the robot getting closer to the odor source location (is the
light source location given in the reward?).
