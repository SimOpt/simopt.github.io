---
title: Esophageal Cancer Simulator
---
---

&nbsp;    
<!-- insert one empty line -->
<!-- can also use "<a></a>" or "<br><br>"  -->

<!-- 
Markdown Cheatsheet https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
Mathematical formulae are supported by https://www.codecogs.com/latex/eqneditor.php
-->

## [Esophageal Cancer Simulator](https://simopt.github.io/ECSim)

Esophageal adenocarcinoma (EAC) is a main sub-type of esophageal cancer, while Barrett's esophagus (BE) is a precursor to EAC (see the figure below).
Recently, chemoprevention has received substantial attention as a method to lower the progression of BE to EAC, and aspirin and statin are two particular drugs that are demonstrated to be effective (<a href="https://doi.org/10.1053/j.gastro.2011.08.036" target="_blank">Kastelein et al. 2011</a>).
For each BE patient, the progression rate to cancer depends on a variety of factors including age, weight, lifestyle habits such as smoking and alcohol use, the grade of dysplasia, etc.
In addition, each patient may have a different response to drugs depending on his or her drug resistance and tolerance.
Hence, it is conceivable that the best treatment regimen for BE is patient-specific.

<!-- ![image](https://simopt.github.io/code/ECSim/EC.jpg)  -->
![EC Figure](https://simopt.github.io/code/ECSim/EC.jpg){:height="70%" width="70%"}  
<!-- *Note: [Original Image](https://commons.wikimedia.org/wiki/File:Diagram_showing_oesophageal_cancer_that_has_spread_(M_staging)_CRUK_175.svg)
by Cancer Research UK / Wikimedia Commons / 
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.en).*  -->
<span style="font-size: 14px"> 
<em>
Note: 
<a href="https://commons.wikimedia.org/wiki/File:Diagram_showing_oesophageal_cancer_that_has_spread_(M_staging)_CRUK_175.svg" target="_blank">Original Image</a> 
by Cancer Research UK / Wikimedia Commons / 
<a href="https://creativecommons.org/licenses/by-sa/4.0/deed.en" target="_blank">CC BY-SA 4.0</a>.
</em>
</span>  



<!-- <img src="https://simopt.github.io/code/ECSim/EC.jpg" width = "70%" height = "70%" alt="EC Figure" align=center /> -->

Here is a discrete-time Markov chain model adopted from
<a href="https://doi.org/10.1093/jnci/djh039" target="_blank">Hur et al. (2004)</a>
and 
<a href="http://cancerpreventionresearch.aacrjournals.org/content/7/3/341" target="_blank">Choi et al. (2014)</a>
, and it simulates the transitions among different health states of a BE patient until death, and the transition diagram of the model is shown as follows.
See more details of the model <a href="https://simopt.github.io/code/ECSim/ModelDescription.pdf" target="_blank">here</a>. 

![Diagram](https://simopt.github.io/code/ECSim/TransitionDiagram.jpg){:height="50%" width="50%"}


I have implemented this model and the codes were written in MATLAB R2018b.
They can be freely redistributed and used under the terms of the <a href="https://raw.githubusercontent.com/SimOpt/simopt.github.io/master/BSD License.txt" target="_blank">BSD 3-Clause License</a>.  

[Download the codes](https://github.com/SimOpt/simopt.github.io/blob/master/code/ECSim/ECSim.zip?raw=true "Click to download")
with an example in it.


&nbsp;    
&nbsp;    
[>> **Go back to the homepage**](https://simopt.github.io)


---

© simopt.github.io  
Last Update: 2020-06-26
