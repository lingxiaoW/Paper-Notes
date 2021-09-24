## Abstract
* Object: use smart phone to estimate positions
* Problem: Conventional smartphone orientation estimates are unreliable. 
* Propose a two-stage, data-driven pipeline using a smartphone that first estimates device orientations and then estimates device position. 
* The orientation module relies on a recurrent neural network and Extended Kalman Filter to obtain orientation estimates.
* The position module then passes those measurements through another recurrent network to perform localization. 

## Introduction
* Two-stage model: 1. estimate device orientation using a nueral network; 2. use the obtained orientation to calculate positions.

## Method
* Orientation Network (OrientNet):
  * Inputs: accelerometer, gyroscope, and magnetometer;
  * Output: absolute orientation and an orientation co-variance for the EKF.
  * Architecture: 2-layer LSTM with 100 hidden units + 2-layer FNN.
  * Training procedure: 1) Ellipsoid-fit calibration on raw magnetometer values; 2) negative log likelihood (NLL) loss is used to train the covariance estimator for each orientation output.
* Position Network:
  * Inputs: world-frame gyroscope and accelerometer as inputs
  * Outputs: final user position
  * Architecture: 2-layer BiLSTM with a hidden size of 100 + 2-layer FNN. The resulting vector is then passed to a linear layer that converts it to a two-dimensional Cartesian 
  displacement relative to the start of each window. 
