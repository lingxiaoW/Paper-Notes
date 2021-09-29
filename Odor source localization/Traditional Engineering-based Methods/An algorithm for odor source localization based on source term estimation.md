## Abstract
* Finding sources of airborne chemicals with mobile sensing systems finds applications across the security, safety, domestic,
medical, and environmental domains.
* Presents an algorithm based on source term estimation and POMDP.

## Introduction
* Benefits of using engineering-based (i.e., probabilistic) methods: 
  * They generate a rich set of information about the environment or the source characteristics.
  * Since the framework is probabilistic, the provided information is associated with an amount of uncertainty, which
  shows how trustworthy the data are.
  * Compared to other categories, probabilistic algorithms are more flexible in terms of the type of underlying hardware.

* Source term estimation (STE)
  * STE algorithms rely on plume model and aim to learn the parameters of the model while the sensory system gathers data in the environment.
  * When used on mobile robots, STE algorithms can be coupled with a navigation strategy which makes the data collection more time-efficient.

## Method
* The general idea of STE is to rely on a plume concentration model whose parameters have to be estimated throughout the experiment.
* The nature of the parameters depends on the model of choice, but, in any case, they include the source poistion, which 
is the goal of the OSL problem. 
* Plume model:
  * Gaussian concentration plume model
* Estimate Gaussian plume model parameters:
  * ``P(m|D)=P(m)P(D|m)/P(D)``
  * ``m`` is a the set of model parameters.
  * ``D`` is the obtained data through sampling.
  * ``P(D|m)`` defines the probability of obtaining a set of data, given a set of parameters.
* Navigation, i.e., choose the next point that gives the rich information
  * ``V = alpha * V_KLD + (1-alpha) * V_source``
  * ``V_KLD`` is the KL divergence between P and Q, where P is ``P(m|D)`` and Q is the predicted probability that is calculated separately for each of the target points (a target point is one of four neighor points around the robot).
  * ``V_source`` is the source position leading to the maximum ``P(m|D)`` 
