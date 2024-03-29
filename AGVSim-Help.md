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
&nbsp;  

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
 * `setting.json` 指定AGV数量、任务到来时间、路径时间不确定性、随机障碍、调度算法（任务指派策略、路径规划算法、路径冲突应对策略）及其参数、随机种子、路径网络显示模式、直接进入直达仿真

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

* "rMissions": 所有运输任务，使用三维数组表示。
  * 目前运输任务的到来时间只由任务稀疏参数控制，运输任务中的时间暂不起作用，指定运输任务到来时间的功能将在下一版本中实现。

```
[
[mission1Orig, mission1Dest, mission1Time]
[mission2Orig, mission2Dest, mission2Time]
...
]
```

* "lengthList": 对应的任务在忽略所有不确定性以及路径冲突情况下的最短行驶时间  
  * 可由A*算法求出；若想更加简单，可用欧式距离粗略计算
* "totalLength": 在忽略所有不确定性以及路径冲突情况下全部任务的最短行驶时间的总和 
  * 该数值用于定义任务稀疏参数，控制任务带来的密集程度


### `setting.json`

包括以下字段：

* "assignStForMission": 任务驱动的任务指派策略，可设置为"NVF"、"LIVF"
* "assignStForCar": 车辆驱动的任务指派策略，可设置为"NMF"、"EMF"
* "routeAlgo": 路径规划算法，可设置为"TWRA"、"ASA"
* "conflictSt": 路径冲突应对策略，可设置为"CAS"、"CSS"、"MS"
* "rescheduleCycel": 路径冲突应对策略的重调度周期，仅在"conflictSt"为"CAS"、"MS"时生效
* "carNum": AGV数量，大于0的整数
* "sparsePara": 任务稀疏参数，大于0的实数，数值越大，任务到来越稀疏
* "barrierPara": 障碍频繁参数，0~1的实数，表示系统中障碍平均占所有位置的比例
* "randomSeed": 随机种子设置，任意整数，用于控制随机数序列
* "interfencePara": 不确定性参数，0~1的实数，数值越大，表示AGV在路径上行驶的时候，实际用时与期望用时之间偏差的随机性越大
* "realMapFlag": 是否以真实比例显示路径网络，可设置为ture（真实比例）或false（标准化显示） 
* "directFlag": 是否直接进入直达仿真模式，可设置为false（否，默认情况）或 ture（是，用于[批量运行](https://simopt.github.io/AGVSim-Help#%E6%89%B9%E9%87%8F%E8%BF%90%E8%A1%8C)）

关于各参数的详细说明，请见石志浩&沈海辉（2022）。
 
## 输出说明

平台完整运行完成后（即，设定的运输任务全部执行完毕），会创建以日期-时间为区分的运行日志文件（GUI界面右侧文字的文字信息）以及调度效果指标文件`simulationResult.csv`（如果已有csv文件，则追加填写，不覆盖原结果），
文件保存位置如[文件结构](https://simopt.github.io/AGVSim-Help#%E6%96%87%E4%BB%B6%E7%BB%93%E6%9E%84)中所示。
 
关于各指标的详细说明，请见石志浩&沈海辉（2022）。

## 批量运行
* 默认情况下，"directFlag"为false，此时打开`AGV系统仿真平台Beta.exe`，仿真不会自动运行，需要点击相应按钮使仿真以某种模式开始。当仿真结束（即，设定的运输任务全部执行完毕）之后，会跳出对话框提示，点击确定之后程序关闭。
* 若将"directFlag"改为true，则打开`AGV系统仿真平台Beta.exe`时仿真便自动以直达仿真模式运行，当仿真结束之后程序自动关闭；该运行方式专为批量运行而设置。
* `AGV系统仿真平台Beta.exe`每完整运行一次，即为在指定的随机数种子（"randomSeed"）下，将设定的运输任务执行完毕。
* 对于一个特定的调度问题，为了得到准确的关于调度效果指标的估计，必须在不同的随机数下重复运行`AGV系统仿真平台Beta.exe`，最终在输出文件`simulationResult.csv`中计算平均值。这便需要不断地修改`setting.json`中的"randomSeed"并且重复打开`AGV系统仿真平台Beta.exe`。
* 上述过程可通过在Python中运行`BatchRun.py`实现批量运行，只需在代码中设置所需的"randomSeed"遍历范围。该程序会将"directFlag"临时设为true，以实现在无需人工干预的情况下重复运行`AGV系统仿真平台Beta.exe`。
* 在使用`BatchRun.py`进行批量运行时，可以结合Python中的多线程功能，以缩短运行时间。
* 需要注意，由于当前Beta版本的仿真平台默认每一次运行结束之后都会输出日志文件，而该文件大小比较大，因此如果重复次数设置得较大时，需要确保平台所在磁盘具有足够的存储空间，或者手动或在`BatchRun.py`中增加相应的功能定期地对日志文件进行清理。
 
&nbsp;    
## 参考文献
石志浩, 沈海辉 (2022). 不确定情景下AGV系统调度算法的离散事件仿真.

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
