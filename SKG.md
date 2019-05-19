---
title: Stochastic Kriging with Gradient
---
---

&nbsp;    
<!-- insert one empty line -->
<!-- can also use "<a></a>" or "<br><br>"  -->

<!-- 
Markdown Cheatsheet https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
Mathematical formulae are supported by https://www.codecogs.com/latex/eqneditor.php
-->

## Stochastic Kriging with Gradient
This is an implementation of the Stochastic Kriging with Gradient (SKG) proposed by <a href="https://doi.org/10.1287/opre.1120.1143" target="_blank">Chen et al. (2013)</a>.  

The codes were written in MATLAB R2015a.
They (except for the third-party functions mentioned below) can be freely redistributed and used under the terms of the <a href="https://raw.githubusercontent.com/SimOpt/simopt.github.io/master/BSD License.txt" target="_blank">BSD 3-Clause License</a>.  

[Download the entire package](https://github.com/SimOpt/simopt.github.io/blob/master/code/QNSim/QNSim.zip?raw=true "Click to download")
with an example in it.

* Gaussian (or called squared exponential) correlation function of the form <img src="https://latex.codecogs.com/svg.latex?\inline&space;R(\boldsymbol{x}-\boldsymbol{y};\boldsymbol{\theta&space;})=\textup{exp}(-\sum_{i=1}^{d}\theta_i&space;|x_i-y_i|^2)">
with <img src="https://latex.codecogs.com/svg.latex?\inline&space;\theta_i>0"> for <img src="https://latex.codecogs.com/svg.latex?\inline&space;i=1,\ldots,d"> is used.
It is easy to modify the function <font color="brown">C</font> in "<font color="brown">neglogLL.m</font>" and "<font color="brown">SKGpredict.m</font>" to use other types of correlation function.

* By default, gradients along all coordinates are incorporated.
Modification will be required to contain only part of the gradients.

<!-- 
&nbsp;    
## Codes
-->

&nbsp;    
&nbsp;    
[>> **Go back to the homepage**](https://simopt.github.io)
