## OpenAI Spinning up
* [link](https://spinningup.openai.com/en/latest/algorithms/trpo.html#background)
* TRPO (Trust Region Policy Optimization) updates policies by taking the largest step possible to improve performance, while satisfying a special constraint on how close the new
and old policies are allowed to be. The constraint is expressed in terms of KL-divergence, which is a measure of distance between probability distributions.
* TRPO keeps new and old policies close in parameter space.
* TRPO is an **on-policy** algorithm.

## Abstract
* This paper presents an iterative procedure for optimizing policies, with guaranteed monotonic improvement. 

