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

### 平台简介
本平台是石志浩&沈海辉（2024）中设计开发的基于离散事件仿真技术的AGV系统仿真平台。
它可以灵活地设置调度问题，并选择调度算法中的任务指派策略、路径规划算法和路径冲突应对策略进行仿真。
该平台具有可视化的界面，可以直观地观察AGV的运行状态和调度算法的表现，也可以输出最终的仿真实验统计数据。
关于本平台的设计背景、逻辑架构、内置调度算法等的详细说明，请见石志浩&沈海辉（2024）。 


### 软件下载
[[AGV系统仿真平台Beta_220509.zip]](https://simopt.github.io/code/AGVSim/AGV系统仿真平台Beta_220509.zip)

压缩包中包含文件

```
|-- AGV系统仿真平台Beta.exe
|-- BatchRun.py
|-- map.json
|-- mission.json
|-- setting.json
|-- 说明.txt
``` 

### 使用说明
[[全部]](https://simopt.github.io/AGVSim-Help)
[[界面]](https://simopt.github.io/AGVSim-Help#%E7%95%8C%E9%9D%A2%E8%AF%B4%E6%98%8E)
[[输入]](https://simopt.github.io/AGVSim-Help#%E8%BE%93%E5%85%A5%E8%AF%B4%E6%98%8E)
[[输出]](https://simopt.github.io/AGVSim-Help#%E8%BE%93%E5%87%BA%E8%AF%B4%E6%98%8E)
[[批量运行]](https://simopt.github.io/AGVSim-Help#%E6%89%B9%E9%87%8F%E8%BF%90%E8%A1%8C)

### 石志浩&沈海辉（2024，§4）中的实验输入
[[文中实验输入文件与说明.zip]](https://simopt.github.io/code/AGVSim/文中实验输入文件与说明.zip)

压缩包中包含文件

```
|-- map.json
|-- mission.json
|-- 总体说明.txt
|-- 4.2 CAS中重调度周期的影响
    |-- setting_Case1_重调度周期x.json
    |-- setting_Case2_重调度周期x.json
    |-- setting_Case3_重调度周期x.json
    |-- 说明.txt
|-- 4.3 AGV调度算法效果对比
    |-- setting_Case1_冲突应对策略x.json
    |-- setting_Case2_冲突应对策略x.json
    |-- setting_Case3_冲突应对策略x.json
    |-- 说明.txt
|-- 4.4 CSS特性探究
    |-- setting_维度x.json
    |-- 说明.txt
``` 


&nbsp;    
## 参考文献
石志浩, 沈海辉 (2024).
<a href="https://doi.org/10.16182/j.issn1004731x.joss.22-1214" target="_blank">不确定情景下AGV系统调度算法的离散事件仿真</a>.
系统仿真学报, **36**(2):385-404.

&nbsp;    
## 作者

👨 [石志浩](https://shizh825.github.io)  
👨 [沈海辉](https://shenhaihui.github.io)

&nbsp;    
&nbsp;    
[>> **Go back to the homepage**](https://simopt.github.io)


---

© simopt.github.io  
Last Update: 2024-11-13
