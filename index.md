---
title:
---
---

<!--&nbsp;    
<!-- insert one empty line -->
<!-- can also use "<a></a>" or "<br><br>"  -->

## About
This repository archives codes written or collected by [SHEN Haihui](https://shenhaihui.github.io) for the purpose of research in the areas of simulation optimization, ranking & selection, kriging metamodeling, etc.
These codes are mainly implementations of some models and algorithms developed by SHEN Haihui and other researchers.

**LICENSE:**
All codes written by SHEN Haihui can be freely redistributed and used under the terms of the
<a href="https://raw.githubusercontent.com/SimOpt/simopt.github.io/master/BSD License.txt" target="_blank">BSD 3-Clause License</a>.

**WARNING:**
These codes are written only for the purpose of demonstration and verification.
While the correctness has been carefully checked, the quality such as standardability, clarity, generality, and efficiency may have not been well considered.


&nbsp;    
## Codes Listed by Paper

* Haihui Shen, L. Jeff Hong, and Xiaowei Zhang (2018).
<a href="https://doi.org/10.1080/24725854.2018.1465242" target="_blank">Enhancing stochastic kriging for queueing simulation with stylized models.</a>
*IISE Transactions*, **50**(11):943-958.
<a href="https://shenhaihui.github.io/research/papers/SESK2018.pdf" target="_blank">PDF</a>  
[Codes](https://simopt.github.io/code/paperSESK2018/SESK2018.zip "Click to download the entire package")
(MATLAB R2015a. Last update: 2018-05-03)

* Haihui Shen, L. Jeff Hong, and Xiaowei Zhang (2021).
<a href="https://doi.org/10.1287/ijoc.2020.1009" target="_blank">Ranking and selection with covariates for personalized decision making.</a>
*INFORMS Journal on Computing*, **33**(4):1500-1519.
<a href="https://shenhaihui.github.io/research/papers/RSC2021.pdf" target="_blank">PDF</a> 
<a href="https://shenhaihui.github.io/research/papers/RSC2021_EC.pdf" target="_blank">E-Companion</a> 
<a href="https://arxiv.org/abs/1710.02642" target="_blank">arXiv</a>    
<a href="https://github.com/shenhaihui/rsc" target="_blank" title="View on GitHub">Codes</a>
(MATLAB R2018b. Last update: 2020-06-19)
<!-- <a href="https://arxiv.org/pdf/1710.02642.pdf" target="_blank">arXiv PDF</a> (an early version)  -->

* Liang Ding, L. Jeff Hong, Haihui Shen, and Xiaowei Zhang (2022).
<a href="https://doi.org/10.1002/nav.22028" target="_blank">Technical note—Knowledge gradient for selection with covariates: Consistency and computation.</a>
*Naval Research Logistics*, **69**(3):496-507.
<a href="https://shenhaihui.github.io/research/papers/IKG2022.pdf" target="_blank">PDF</a> 
<a href="https://shenhaihui.github.io/research/papers/IKG2022_Appx.pdf" target="_blank">Appendix</a>
<a href="https://arxiv.org/abs/1906.05098" target="_blank">arXiv</a>   
<a href="https://github.com/shenhaihui/ikg" target="_blank" title="View on GitHub">Codes</a>
(MATLAB R2018b. Last update: 2021-09-08)

* Guangxin Jiang, L. Jeff Hong, and <strong>Haihui Shen</strong> (2024).
<a href="https://doi.org/10.1287/ijoc.2023.0292" target="_blank">Real-time derivative pricing and hedging with consistent metamodels.</a>
*INFORMS Journal on Computing*, **36**(5):1168-1189.
<a href="https://shenhaihui.github.io/research/papers/GESK2024.pdf" target="_blank">PDF</a>
<a href="https://shenhaihui.github.io/research/papers/GESK2024_EC.pdf" target="_blank">E-Companion</a>   
<a href="https://github.com/INFORMSJoC/2023.0292" title="View on GitHub." target="_blank">Codes</a>	
(MATLAB R2022a. Last update: 2024-01)

* Xiuxian Wang, L. Jeff Hong, Zhibin Jiang, and Haihui Shen (2023).
<a href="https://doi.org/10.1287/opre.2021.0303" target="_blank">Gaussian process-based random search for continuous optimization via simulation.</a>
*Operations Research*, online.
<a href="https://www.researchgate.net/publication/351599952_Gaussian_Process_Based_Search_for_Continuous_Optimization_via_Simulation" target="_blank">ResearchGate</a>   
<a href="https://github.com/xiuxianwang/GPS-C-algorithm" title="View on GitHub." target="_blank">Codes</a>
(MATLAB. Last update: 2023)

* 石志浩, 沈海辉* (2024).
<a href="https://doi.org/10.16182/j.issn1004731x.joss.22-1214" target="_blank">不确定情景下AGV系统调度算法的离散事件仿真</a>.
系统仿真学报, **36**(2):385-404.
<a href="https://shenhaihui.github.io/research/papers/AGV2024.pdf" target="_blank">PDF</a>   
<a href="https://simopt.github.io/AGVSim" title="View on GitHub." target="_blank">AGV系统仿真平台</a>
(Beta版)

&nbsp;    
## Codes Listed by Content

### Simulation
* [Queueing Network Simulator](https://simopt.github.io/QNSim)  
&nbsp;- open queueing network that consists of a finite number of G/G/s/K stations

* [Esophageal Cancer Simulator](https://simopt.github.io/ECSim)    
&nbsp;- a Markov simulation model of esophageal cancer adapted from
<a href="https://doi.org/10.1093/jnci/djh039" target="_blank">Hur et al. (2004)</a>
and 
<a href="http://cancerpreventionresearch.aacrjournals.org/content/7/3/341" target="_blank">Choi et al. (2014)</a>

### Kriging Metamodeling
<!-- * Stochastic kriging, copyrighted by Barry L. Nelson et al. (2009) -->

* [Stochastic Kriging with Gradient (SKG)](https://simopt.github.io/SKG)    
&nbsp;- proposed by
<a href="https://doi.org/10.1287/opre.1120.1143" target="_blank">Chen et al. (2013)</a>

<!--
### Optimization via Simulation
* [Convergent Optimization via Most-Promising-Area Stochastic Search (COMPASS)]()    
&nbsp;- a locally convergent algorithm for discrete optimization via simulation    
&nbsp;- proposed by [Hong and Nelson (2006)](https://doi.org/10.1287/opre.1050.0237)
-->

<!--
* [Gaussian Process-based Search (GPS)](https://simopt.github.io/GPS)    
&nbsp;- a globally convergent algorithm for discrete optimization via simulation    
&nbsp;- proposed by [Sun et al. (2014)](https://doi.org/10.1287/opre.2014.1315)
-->

<!--
### Ranking & Selection
* [Ranking and Selection with Covariates (R&S-C)]()
-->

<!--
### Other Implementations
* [Queueing Network Approximation]()    
&nbsp;- a decomposition approximation of open finite-capacity queuing networks with BAS  
&nbsp;- proposed by [Osorio and Bierlaire (2009)](https://doi.org/10.1016/j.ejor.2008.04.035)
-->

### Useful Codes Developed by Others
* SimOpt Testbed 
[<a href="https://github.com/simopt-admin/simopt/wiki" target="_blank">github.com/simopt-admin/simopt/wiki</a>]
for comparison of simulation optimization solvers (algorithms)

* Stochastic Kriging 
[<a href="http://stochastickriging.net" target="_blank">stochastickriging.net</a>]

* Industrial Strength COMPASS (ISC) 
[<a href="http://www.iscompass.net" target="_blank">www.iscompass.net</a>]


<!--  **Example of <font color="red">colorful text in web view</font>** -->

&nbsp;    
## Contact

👨 SHEN Haihui  
✉️ shenhaihui<!-- -->@gmail.com  <!-- Disable auto-hyperlink -->  
🏠 [shenhaihui.github.io](https://shenhaihui.github.io)

---

© simopt.github.io  
Last Update: 2021-12-20
