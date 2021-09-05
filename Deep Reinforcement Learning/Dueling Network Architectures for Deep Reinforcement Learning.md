
2016

## Abstract
* This paper presents a new neural network architecture (i.e., dueling network) for model-free reinforcement learning.
* The dueling network has to streams to separately estimate (scalar) state-value and the advantages of each action. 
* Motivation: for many states, it is unnecessary to estimate the value of each action choice. 

## Dueling Network Architecture
* Lower layers of the dueling network are convolutional as in the original DQNs.
* Use two sequences of fully connected layers to provide value (V) and advantage (A) functions.
* Two steams are combined to produce a single output Q function, i.e., Q = V+A. 
* To gain identifiability (i.e., given a Q value, A and V can be identified), the sum of A is forced to zero (i.e., normalizing A before adding with V to calculate Q).
* Q = V + (A- mean(A))
* Thus, V is more likely to be updated with A is less likely to be updated (due to the constrain applied on A). 
