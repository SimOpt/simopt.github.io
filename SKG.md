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
They can be freely redistributed and used under the terms of the BSD 3-Clause License.

Download the entire package with an example in it.

* Gaussian correlation function of the form <img src="https://latex.codecogs.com/svg.latex?\inline&space;R(\boldsymbol{x}-\boldsymbol{y};\boldsymbol{\theta&space;})=\textup{exp}(-\sum_{i=1}^{d}\theta_i&space;|x_i-y_i|^2)">
with <img src="https://latex.codecogs.com/svg.latex?\inline&space;\theta_i>0"> for <img src="https://latex.codecogs.com/svg.latex?\inline&space;i=1,\ldots,d">.

* By default, gradients along all coordinates are incorporated.
It can be modified to contain only part of the gradients.

<!-- 
&nbsp;    
## Codes
-->

&nbsp;    
&nbsp;    
[>> **Go back to the homepage**](https://simopt.github.io)
