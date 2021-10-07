## Abstract
* The paper sets a new foundation for data-driven inertial navigation research, where the task is the estimation of positions and orientations of a moving subject from a sequence of IMU sensor measurements.
* This paper presents:
  * a new benchmark containing IMU sensor data from 100 human subjects with ground-truth 3d trajectories under natural human motions
  * novel neural inertial navuigation architectures
  * qualitative and quantitative evaluations of the competing methods over three inertial navigation benchmarks. 

## Introduction
* IMU is ubiquitous;
* Traditional methods using IMU to perform inertial navigation have many constraints:
  * e.g., an IMU must be attached to a foot; IMU is assumed to be rigidly attached to a body; a subject must walk forward so that the motion direction becomes a constant in device coordination frame.
* Data-driven approaches have made a break-through in loosing these constraints, where the acquisition of IMU sensor data and ground truth motion trajectories allows supervised learning.
* This paper seeks to take data-driven inertial navigation research to the next level via 1) providing the largest inertial navigation database; 2) presenting a novel neural networks for inertial navigation; 3) presenting comparison to state-of-art.

## THe RoNIN Dataset
* The RoNIN dataset is better than the existing datasets in terms of three factors: scale, diversity, and fidelity.
* Use two-device data acquisition protocol, where one device is used to capture ground-truth trajectories and one device is for collecting IMU data.

## Robust Neural Inertial Navigation (RoNIN)
* RoNIN is a combination of ResNet, LSTM, or Temporal Convolutional Network (TCN) as its backbone. 
* RoNIN seeks to regress a velocity vector given an IMU sensor history.
 
