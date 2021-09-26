## Abstract
* Finding sources of airborne chemicals with mobile sensing systems finds applications across the security, safety, domestic,
medical, and environmental domains.
* Presents an algorithm based on source term estimation and POMDP.

## Introduction
* Benefits of using engineering-based (i.e., probabilistic) methods: 
  * 1. they generate a rich set of information about the environment or the source characteristics.
  * 2. since the framework is probabilistic, the provided information is associated with an amount of uncertainty, which
  shows how trustworthy the data are.
  * 3. compared to other categories, probabilistic algorithms are more flexible in terms of the type of underlying hardware.

* Source term estimation (STE)
  * STE algorithms rely on plume model and aim to learn the parameters of the model while the sensory system gathers data in the environment.
  * When used on mobile robots, STE algorithms can be coupled with a navigation strategy which makes the data collection more time-efficient.

## Method
* The general idea of STE is to rely on a plume concentration model whose parameters have to be estimated throughout the experiment.
* The nature of the parameters depends on the model of choice, but, in any case, they include the source poistion, which 
is the goal of the OSL problem. 
