## Abstract
* Autonomous urban driving navigation is a problem, exspecially in complex environment and terrible weather conditions. 
* IPP-RL: Imitation Pure-Purseuit-Reinforcement Learning.
* In the IPP model. the visual information captured by camera can be compensated by the calculated steering angle, thus it could perform well under bad weather conditions. 
* Training process: imitation learning on driving data and then use reinforcement learning (DDPG) in the second stage training. 

## Introduction
* Problem: vision based end-to-end approaches autonomous urban driving is effected heavily by image corruptions; depending on cameras solely makes these methods difficult to adapt
to extreme weather conditions because of image noises. 
* Address these challenges by combining reinforcement learning with imitation learning and using the steering angle calculated by PP algorithm as additional input. 
* Integrating the traditional steering method and behavior cloning approach into a neural network should be able to provide a robust steering method for terrible driving conditions. 
* Towards the challenge of generalization, it can be addressed by reinforcement learning. 

## Methods
* In the IPP pretrain stage, the training data is a set of driving videos collected by the expert. It consists of high-level commands, location, and RGB image information. 
* Use ego-centric RGB image, measured speed, steering angle calculated by PP as inputs; experts' action as ground truth; to train the neural network. 
* In the reinforcement learning stage, model-free algorithm DDPG is selected, which consists of an actor-network and a critic-network. The actor-network is initially same as IPP-network.
* Pure pursuit (PP, used to build the relationship between the curretn position and a selected target point, predicting the steering angle of the front wheel). 
