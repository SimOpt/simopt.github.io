---
title: Queueing Network Simulator
---
---

&nbsp;    
<!-- insert one empty line -->
<!-- can also use "<a></a>" or "<br><br>"  -->

<!-- 
Markdown Cheatsheet https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
Mathematical formulae are supported by https://www.codecogs.com/latex/eqneditor.php
-->

# Queueing Network Simulator

### Queueing Network Details  

This simulator can simulate **open queueing network** that consists of a **finite number of GGsK stations** to provide service.
External customers may enter the network via each station.
A customer that completes the service at one station may be routed to another to receive further service or leave the network **subject to probability**.

#### The notations and more details
1. The network has <img src="https://latex.codecogs.com/svg.latex?{N}"> stations.  
2. Station <img src="https://latex.codecogs.com/svg.latex?{i}"> has <img src="https://latex.codecogs.com/svg.latex?{s_i}">
identical servers, each of which has the service rate <img src="https://latex.codecogs.com/svg.latex?{\mu_i>0}">, for
<img src="https://latex.codecogs.com/svg.latex?{i=1,\ldots,N}">.
All the stations follow the first-in-first-out (FIFO) discipline.  
3. The arrival rate of external customers to station <img src="https://latex.codecogs.com/svg.latex?{i}"> is 
<img src="https://latex.codecogs.com/svg.latex?{\lambda_i\geq&space;0}">, for <img src="https://latex.codecogs.com/svg.latex?{i=1,\ldots,N}">.
There exists some <img src="https://latex.codecogs.com/svg.latex?{i}"> for which <img src="https://latex.codecogs.com/svg.latex?{\lambda_i>0}">.  
4. A customer that completes the service at station <img src="https://latex.codecogs.com/svg.latex?{i}">
is routed to station <img src="https://latex.codecogs.com/svg.latex?{j}">
with probability <img src="https://latex.codecogs.com/svg.latex?{P_{ij}}">
and leaves the network with probability
<img src="https://latex.codecogs.com/svg.latex?\inline&space;P_{i0}=1-\sum_{j=1}^N&space;P_{ij}" title="P_{i0}=1-\sum_{j=1}^N P_{ij}">,
for <img src="https://latex.codecogs.com/svg.latex?{i,j=1,\ldots,N}">.
There exists some <img src="https://latex.codecogs.com/svg.latex?{i}"> for which <img src="https://latex.codecogs.com/svg.latex?{P_{i0}>0}">.  
5. Station <img src="https://latex.codecogs.com/svg.latex?{i}"> has capacity <img src="https://latex.codecogs.com/svg.latex?{K_i}">, i.e. the maximum number of customers allowed in the station, including those waiting in queue and those being served,
for <img src="https://latex.codecogs.com/svg.latex?{i=1,\ldots,N}">.
The capacity can be finite or infinite.

#### Customers' behavior when a station is at full capacity
1. If an external customer arrives at a station when it is full, then the customer will not enter the network and is lost permanently.  
2. If an internal customer who finishes the service at station <img src="https://latex.codecogs.com/svg.latex?{i}"> and is routed to station <img src="https://latex.codecogs.com/svg.latex?{j}"> finds that station <img src="https://latex.codecogs.com/svg.latex?{j}"> is full, then the customer is blocked at station <img src="https://latex.codecogs.com/svg.latex?{i}"> and occupy the original server until there is a place at station <img src="https://latex.codecogs.com/svg.latex?{j}">.
The blocked customers, either at the same station or at different stations, are unblocked with a FIFO discipline.
This blocking mechanism is known as blocking-after-service (BAS).

#### About deadlock
For queueing network with closed loop and finite capacity, deadlock phenomenon may occur. In this simulator, when deadlock occurs, it is solved by swapping instantaneously.


### Code Details

The codes were written in MATLAB R2015a.
They (except for the third-party functions mentioned below) can be freely redistributed and used under the terms of the <a href="https://raw.githubusercontent.com/SimOpt/simopt.github.io/master/LICENSE" target="_blank">BSD 3-Clause License</a>.  

Download the entire page with an example in it.

#### Structure

Before calling the simulator, we first need to find all the closed loop in the network (in order to handle the potential deadlock).
It is achieved by a third-party function "<font color="brown">find_elem_circuits.m</font>" (author: Chris Maes [gist.github.com/cmaes/1260153](https://gist.github.com/cmaes/1260153)).
Moreover, the function "<font color="brown">find_elem_circuits.m</font>" relies on a function "<font color="brown">components.m</font>",
which is a function in the graph package MatlabBGL (author: David Gleich [dgleich.github.io/matlab-bgl](http://dgleich.github.io/matlab-bgl)).
The identified closed loops is then passed into the simulator together with all other network parameters.

#### Inputs and outputs

* *Input: QueuePra - queueing network parameters*  
  - total station number
  - arrival rate and distribution (needs to modify "<font color="brown">inter_arrival_time.m</font>") to each station  
  - server number at each station  
  - service rate and distribution (needs to modify "<font color="brown">service_time.m</font>") of a server in each station  
  - transition (routing) probability matrix  
  - capacity (wating space + server number) of each station  
  - the list of all loops of the network (where the deadlock may happen) identified by "<font color="brown">find_elem_circuits.m</font>"  

* *Inputs: SimPra - simulation parameters*  
  - time length for one replication  
  - warm up length to let the queue be steady  
  - number of simulation replication  
  - random seed  

* *Outputs:*  
  - stationary distribution for each station  
  - averaged number of customers in each station & the whole system (waiting + serving), and the variance of the AVERAGED number
  - averaged number of customers waiting in each station queue & the whole system, and the variance of the AVERAGED number
  - averaged sojourn time\* in each station & the whole system (waiting + serving), and the variance of the AVERAGED number
  - averaged waiting time\* in each station queue & the whole system, and the variance of the AVERAGED number
  

\* 
*Note about the calculation of averaged sojourn time and waiting time:
Only consider the customers ever enter the station, i.e., the rejected customers are not counted.
Besides, if a customer never enters station 1, he will not be counted when calculating sojourn time for station 1.
If a customer enters station 1 more than once, he is still regarded as one customer.
(It is not difficult to modify the code to count all arrivals.)*

block time is considered as waiting time ??

blocked customer is considered as in queue ??


&nbsp;    
&nbsp;    
[>> **Go back to the homepage**](https://simopt.github.io)


---

© 2017-2018 simopt.github.io  
Last update: 2018-05-03
