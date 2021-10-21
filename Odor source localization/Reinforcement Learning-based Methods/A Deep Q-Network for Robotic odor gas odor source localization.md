## Abstract
* Apply deep Q-network to solve the odor source localization problem.
* Use an odor hits distribution model to model the odor concentration distribution in indoor environment.
* The deep Q-network takes 
  * Inputs: the stacked historic measurement data;
  * Outputs: the expected cumulative future reward of actions of the robots (Q-function).

## The Odor Source Localization Task
* Odor concentration is measured in a discrete number of hits.
  * The Poisson distribution model is utilized to model the odor hits distribution. 
* The simulator is too simple:
  * The airflow direction is fixed (along the x axis),
  * The resolution of the search map is small (9 by 9),
  * The robot can only move in 4 discrete directions.

## DQN based OSL algorithm
* The input layer of the CNN includes four matrices:
  * The first matrix is the olfactory robot trajectory matrix, in which the value of each cell is the number of times the olfactory robot passing the corresponding position.
  * The second and third matrices are the mean measured airflow direction matrix and the mean measured odor hits matrix, in which the value of each cell is the average value of measured
  airflow direction and measured odor hits
  * The fourth matrix is the current map matrix, in which the value of the cell where the robot is located is 2, and the value of the cells where there are obsacles is 1, the others 
  are 0.
* The outputs of CNN are robot actions. 
