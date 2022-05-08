---
title: AGV系统仿真平台
---
---

<!-- &nbsp;    -->
<!-- insert one empty line -->
<!-- can also use "<a></a>" or "<br><br>"  -->

<!-- 
Markdown Cheatsheet https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
Mathematical formulae are supported by https://www.codecogs.com/latex/eqneditor.php
-->

## AGV系统仿真平台（Beta版）

![GUI](https://simopt.github.io/code/AGVSim/gui1.png)

### 软件下载

### 软件使用说明
[软件使用说明](https://github.com/SimOpt/AGVSim)

### 论文xx第4节中的实验
[实验](https://github.com/SimOpt/AGVSim/tree/main/ExperimentsInPaper)


<!-- 
### Queueing Network Details  

This simulator can simulate **open queueing network** that consists of a **finite number of G/G/s/K stations** to provide service.
External customers may enter the network via each station.
A customer that completes the service at one station may be routed to another to receive further service or leave the network **subject to probability**.

#### The notations and more details
1. The network has <img src="https://latex.codecogs.com/svg.latex?{N}"> stations.  
2. Station <img src="https://latex.codecogs.com/svg.latex?{i}"> has <img src="https://latex.codecogs.com/svg.latex?{s_i}">
identical servers, each of which has the service rate <img src="https://latex.codecogs.com/svg.latex?{\mu_i>0}">, for
<img src="https://latex.codecogs.com/svg.latex?{i=1,\ldots,N}">.
All the stations follow the first-in-first-out (FIFO) discipline.
And there is only one queue for each station.  
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
Moreover, it is allowed that a customer finishing service is routed to the same station (re-enter), i.e., <img src="https://latex.codecogs.com/svg.latex?{P_{ii}}"> can be nonzero.
In this case, the customer will join the end of the queue (if any) of this station while the first customer in queue (if any) move into the vacated server simultaneously.
5. Station <img src="https://latex.codecogs.com/svg.latex?{i}"> has capacity <img src="https://latex.codecogs.com/svg.latex?{K_i}">, i.e. the maximum number of customers allowed in the station, including those waiting in queue and those in the servers,
for <img src="https://latex.codecogs.com/svg.latex?{i=1,\ldots,N}">.
The capacity can be finite or infinite.

#### Customers' behavior when a station is at full capacity
1. If an external customer arrives at a station when it is full, then the customer will not enter the network and is lost permanently.  
2. If an internal customer who finishes the service at station <img src="https://latex.codecogs.com/svg.latex?{i}"> and is routed to station <img src="https://latex.codecogs.com/svg.latex?{j}"> finds that station <img src="https://latex.codecogs.com/svg.latex?{j}"> is full, then the customer is blocked at station <img src="https://latex.codecogs.com/svg.latex?{i}"> and occupy the original server until there is a place at station <img src="https://latex.codecogs.com/svg.latex?{j}">.
The blocked customers, either at the same station or at different stations, are unblocked with a FIFO discipline.
This blocking mechanism is known as blocking-after-service (BAS).

#### About deadlock
For queueing network with closed loop and finite capacity, deadlock phenomenon may occur.
In this simulator, when deadlock occurs, it is solved by *swapping* instantaneously.
Besides, when a customer re-enters a station, he has higher priority than those blocked in other stations.


### Code Details

The codes were written in MATLAB R2015a.
They (except for the third-party functions mentioned below) can be freely redistributed and used under the terms of the <a href="https://raw.githubusercontent.com/SimOpt/simopt.github.io/master/BSD License.txt" target="_blank">BSD 3-Clause License</a>.  

[Download the entire package](https://github.com/SimOpt/simopt.github.io/blob/master/code/QNSim/QNSim.zip?raw=true "Click to download")
with an example in it.


#### Structure

Before calling the simulator, we first need to find all the closed loop in the network (in order to handle the potential deadlock).
It is achieved by a third-party function "<font color="brown">find_elem_circuits.m</font>" (author: Chris Maes [gist.github.com/cmaes/1260153](https://gist.github.com/cmaes/1260153)).
Moreover, the function "<font color="brown">find_elem_circuits.m</font>" relies on a function "<font color="brown">components.m</font>",
which is a function in the graph package MatlabBGL (author: David Gleich [dgleich.github.io/matlab-bgl](http://dgleich.github.io/matlab-bgl)).
The identified closed loops are then passed into the simulator together with all other network parameters.

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
  - averaged number of customers in each station<sup><font color="red">1</font></sup> & the whole system, and the variance of the AVERAGED number
  - averaged number of customers waiting in each station queue & the whole system<sup><font color="red">2</font></sup>, and the variance of the AVERAGED number
  - averaged sojourn time<sup><font color="red">3</font></sup> in each station & the whole system (waiting + serving), and the variance of the AVERAGED number
  - averaged waiting time<sup><font color="red">3,4</font></sup> in each station queue & the whole system, and the variance of the AVERAGED number
-->  



&nbsp;    
## 作者

👨 [石志浩](https://shizh825.github.io)  
👨 [沈海辉](https://shenhaihui.github.io)

&nbsp;    
&nbsp;    
[>> **Go back to the homepage**](https://simopt.github.io)


---

© simopt.github.io  
Last Update: 2022-05-04
