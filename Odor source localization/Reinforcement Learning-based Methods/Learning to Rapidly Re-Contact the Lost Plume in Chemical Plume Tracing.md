## Abstract
* Use reinforcement learning method to determine the bias angle in the track-out behavior. 
* Two RL methods, namely virtual trail following (VTF) and collaborative VTF (cVTF):
  * In VTF, the action-value is generalized from recently stored instances of successful Track-out activities;
  * In cVTF, multiple robots store their own instances, and learn from the stored instances
* The RL algorithm is Q-learning (Not Deep Q network)

## VTF and cVTF Methods
* Reward: length of period that the robot detects plumes
* Approximate Q value using locally weighted average (LWA) method
* Collect training data from real-world environment

