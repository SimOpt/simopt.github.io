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

## AGV系统仿真平台（Beta版）使用说明



### 界面说明
GUI界面左侧以2D俯视图形式显示AGV路径网络和AGV的实时位置与状态，如图1-2所示。
由于每条路径的长度可以不同，路径网络既可以采用标准化显示（以等长的边显示不同长度的通道，如图1所示），
也可以采用真实比例显示（如图2所示），以满足不同的需求。

![GUI1](https://simopt.github.io/code/AGVSim/gui1.png)
图1：标准化显示（在setting.json中令realMapFlag为false）
<span style="font-size: 14px"> 

![GUI2](https://simopt.github.io/code/AGVSim/gui2.png)
图2：真实比例显示（在setting.json中令realMapFlag为true）

路径网络上红色方块表示随机出现在节点或通道的障碍。黄色的多边形表示AGV，尖的一端是AGV的车头方向，上面的数字为AGV的编号。虚线框表示该AGV处于空闲状态，实线框表示该AGV处于工作状态，其中黑色线框表示没有负载，绿色线框表示有负载。GUI界面左下角显示了当前系统仿真时间（从0时刻开始运行）和当前任务池中以及未到来的任务数量。底部四个按钮用于仿真的模式选择与控制：步进仿真按钮每点击一次，仿真向前推进一步，并伴随相应AGV或路径网络状态的显示更新（若有）；点击自动仿真按钮，则仿真持续自动向前推进且伴随动画显示，直至全部任务执行完毕，中途可以点击仿真暂停按钮退出自动仿真模式；点击直达仿真按钮，则在关闭动画显示的情况下以最快速度推进仿真直至全部任务执行完毕。GUI界面右侧以文字显示调度信息（包括任务指派结果、路径规划情况、路径冲突与解除情况等）、障碍信息（出现与消失）以及AGV运行信息（包括路径开始、路径结束与到达离开节点等）。

### 软件使用说明
[软件使用说明](https://github.com/SimOpt/AGVSim)

### 论文xx第4节中的实验
[实验](https://github.com/SimOpt/AGVSim/tree/main/ExperimentsInPaper)




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
