https://ieeexplore.ieee.org/abstract/document/9351818

## Extensions to Reinforcement Learning

* Reward Shaping: allos a reward function to be engineered in a way to provide more frequent feedback signal on appropriate behaviors (useful in sparse rewards).

* Learning from Demonstrations: supervised learning (learning from expert demonstration) + reinforcement learning.
  * DQfD (Deep Q learning from Demonstration): pre-trains the agent and uses expert demonstrations by adding them into the replay buffer with additional priority. 
  * IRL (Inverse Reinforcement Learning): infer the reward function that justifies demonstrations of the expert. 
  * GAIL (Generative Adversarial Imitation Learning): GAIL trains a policy close enough to the expert policy to fool a discriminator.

## RL for Autonomous Driving Tasks

* RL can be applied in 
  * Controller optimization
  * Path planning and trajectory optimization
  * motion planning and dynamic path planning
  * development of high-level driving policies for complex navigation tasks
  * scenario-based policy learning for highways, intersections, erges, and splits
  * reward learning with IRL from expert data for intent prediction fro traffic actors (e.g., pedestrain, vehicles)
  * Learning of policies that ensures safety and perform risk estimation. 

* State Space, Action Space, and Rewards
  * State space: position, heading, velocity of ego-vehicle, lane information, etc. 
  * Action space: continuous-value control (steering angle, throttle, and brake); discrete control (gear selection). 
  * Rewards: distance travelled towards destination, speed of ego vehicle, etc. (depending on the AD task).

* Sample Efficiency
  * Animals are able to learn new tasks in just a few trials, benefiting from prior knowledge about the environment.
  * For RL, the learning process requires too many samples to learn a reasonable policy. 
  * Transfer leanring in RL: enables the reuse of previously trained policy for a source task to initialize the learning of a target task. 
