# Key words
* Human-Robot teaming
* Temporal plannng networks (TPN)

# Abstract
* Robots need to deal with uncertainty due to 1) working with humans who are unpredictable; 2) operate in a dynamic environment.
* Ingoring all uncertainties is dangerous, while accounting for all possible outcomes is often computationally infeasible.
* Temporal planning network (TPN) is a middle-ground approach between two aforementioned options. 

# Introduction
* TPNs were originally designed to control robotic space explorers. 
* TPNs is complex in construction. TPNs need manually encoding with the help of a domain expert. 

# Background
* [Temploral planning](https://users.aalto.fi/~rintanj1/jussi/temporalplanning.html)
  * The most basic form of planning views actions as atomic entities that are taken one at a time in a sequence.
  * When multiple things can be happening at a time, it is necessary to model the duration and concurrency of actions and events. 
  * Multiple actions can be taken simultaneously, their durations may vary, and actions and events may have complex interdependencies which determine which combinations are possible. 
