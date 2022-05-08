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


## 界面说明
* GUI界面左侧以2D俯视图形式显示AGV路径网络和AGV的实时位置与状态，如图1-2所示。
  * 可通过拖拽窗口右下角调节见面大小和显示范围。

* 由于每条路径的长度可以不同，路径网络既可以采用标准化显示（以等长的边显示不同长度的通道，如图1所示），也可以采用真实比例显示（如图2所示），以满足不同的需求。

![GUI1](https://simopt.github.io/code/AGVSim/gui1.png)
图1：标准化显示（在setting.json中令realMapFlag为false）
<span style="font-size: 14px"> 

![GUI2](https://simopt.github.io/code/AGVSim/gui2.png)
图2：真实比例显示（在setting.json中令realMapFlag为true）

* 路径网络上红色方块表示随机出现在节点或通道的障碍。
 
* 黄色的多边形表示AGV，尖的一端是AGV的车头方向，上面的数字为AGV的编号。
  * 虚线框表示该AGV处于空闲状态，实线框表示该AGV处于工作状态，其中黑色线框表示没有负载，绿色线框表示有负载。

* GUI界面左下角显示了当前系统仿真时间（从0时刻开始运行）和当前任务池中以及未到来的任务数量。

* 底部四个按钮用于仿真的模式选择与控制。
  * 步进仿真按钮每点击一次，仿真向前推进一步，并伴随相应AGV或路径网络状态的显示更新（若有）;
  * 点击自动仿真按钮，则仿真持续自动向前推进且伴随动画显示，直至全部任务执行完毕，中途可以点击仿真暂停按钮退出自动仿真模式;
  * 点击直达仿真按钮，则在关闭动画显示的情况下以最快速度推进仿真直至全部任务执行完毕。     


* GUI界面右侧以文字显示调度信息（包括任务指派结果、路径规划情况、路径冲突与解除情况等）、障碍信息（出现与消失）以及AGV运行信息（包括路径开始、路径结束与到达离开节点等）。

<font color="red">显示异常解决</font>
 由于当前Beta版本的仿真平台暂不支持自适应显示调节，当显示器设定了自定义缩放大小时，可能出现GUI显示不全的情况
* 解决方法一：将自定义缩放大小设置为100%
* 解决方法二：为AGV系统仿真平台选择高DPI缩放替代，如图3所示。
![GUI3](https://simopt.github.io/code/AGVSim/gui_scale.png){:height="60%" width="60%"}    
图3：高DPI缩放替代


## 文件结构

```
|-- AGV系统仿真平台Beta.exe
|-- BatchRun.py
|-- map.json
|-- mission.json
|-- setting.json
`-- simulationResult.csv 
`-- log
    |-- log_date1
    |   |-- time1.log
    | 	`-- time2.log
    `-- log_date2
``` 
 
 
## 输入说明

平台输入包括三个json文件：
 * `map.json` 指定路径网络的结构和大小
 * `mission.json` 指定运输任务数量和起点-终点
 * `setting.json` 指定AGV数量、任务到来时间、路径时间不确定性、随机障碍、调度算法（任务指派策略、路径规划算法、路径冲突应对策略）及其参数、随机种子等

需要将三个json文件与平台程序放置在同一个目录下，如[文件结构](https://simopt.github.io/AGVSim-Help#%E6%96%87%E4%BB%B6%E7%BB%93%E6%9E%84)中所示。


### `map.json`

路径网络只接受网格拓扑结构地图，可通过设置路径网络中某些节点与通道的行驶时间为"Infinity"，实现对其他结构的模拟。
包括以下字段：

* "ROW": 行数
* "ROW_CNV": 经过路径网络转换后的地图行数`ROW_CNV = 2 * ROW - 1`
* "COL": 列数
* "COL_CNV": 经过路径网络转换后的地图列数`COL_CNV = 2 * COL - 1`
* "ROW_DIST": 平均行距（用于真实地图显示的比例尺缩放）
* "COL_DIST": 平均列距（用于真实地图显示的比例尺缩放）
* "nodeDlt": 默认速度下，节点与弧的完整时间，使用二维数组表示，对应关系如下图
```
"""
node0_1			arc0_1-1_1		node1_1
arc0_0-0_1					arc1_0-1_1
node0_0			arc0_0-1_0		node1_0

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

[
[[node0_1_dlt]		[arc0_1-1_1_dlt]	[node1_1_dlt]]
[[arc0_0-0_1_dlt]	[Infinity]		[arc1_0-1_1_dlt]]
[[node0_0_dlt]		[arc0_0-1_0_dlt]	[node1_0_dlt]]
]
"""
```

* "nodeLoc"节点与弧的位置，使用三维数组表示，对应关系如下图
```
"""
node0_1			arc0_1-1_1		node1_1
arc0_0-0_1					arc1_0-1_1
node0_0			arc0_0-1_0		node1_0

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

[
[[node0_1_loc]		[arc0_1-1_1_loc]	[node1_1_loc]]
[[arc0_0-0_1_loc]	[Infinity]		[arc1_0-1_1_loc]]
[[node0_0_loc]		[arc0_0-1_0_loc]	[node1_0_loc]]
]
"""
```

### `mission.json`

包括以下字段：

* "rMissions": 所有运输任务，使用三维数组表示。（目前运输任务的到来时间只由任务稀疏系数控制，运输任务中的时间暂不起作用，指定运输任务到来时间的功能将在后续开放）

```
[
[mission1Orig, mission1Dest, mission1Time]
[mission2Orig, mission2Dest, mission2Time]
...
]
```

"lengthList":对应的任务无冲突最短路时间（用于仿真指标计算，不影响仿真过程，可用欧式距离粗略代替）

"totalLength":所有任务无冲突最短路时间之和（用于仿真指标计算，不影响仿真过程，可用欧式距离粗略代替）

### `setting.json`

包括以下字段：

"assignStForMission": 任务驱动的任务指派策略选择，可设置为"NVF"、"LIVF"

 "assignStForCar": 车辆驱动的任务指派策略选择，可设置为"NMF"、"EMF"

 "routeAlgo": 路径规划算法选择，可设置为"TWRA"、"ASA"

 "conflictSt": 路径冲突应对策略选择，可设置为"CAS"、"CSS"、"MS"
 
 "rescheduleCycel": 路径冲突应对策略的重调度周期，仅在"conflictSt"为"CAS"、"MS"时生效

 "carNum": AGV数量，大于0的整数

 "sparsePara": 任务稀疏参数，大于0的实数，参数越大，任务到来越稀疏

 "barrierPara": 障碍参数，0~1的实数，表示系统中障碍平均占所有位置的比例

 "randomSeed": 随机种子设置，任意整数，用于复现仿真结果
 
 "interfencePara": 误差项参数，0~1的实数，用于控制误差项大小，参数越大，路径时间误差越大
 
 "realMapFlag": 是否以真实地图显示，可设置为ture（真实地图）与false（拓扑地图） 
 
 





## 显示：





## 输出：

平台完整运行完成后，会创建以日期-时间为区分的运行日志文件以及运行指标文件`simulationResult.csv`（如果已有csv文件，则追加填写，不覆盖原结果）




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
