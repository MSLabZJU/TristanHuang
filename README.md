# TristanHuang

## 个人介绍

2019届毕业研究生-黄美川

- :e-mail: 联系方式：[tristanhuang@foxmail.com](mailto:tristanhuang@foxmail.com)
- :computer: 个人主页：[tristanhuang.cn](http://tristanhuang.cn)
- :octopus: Github：[TristanHuang0501](http://github.com/TristanHuang0501)

## 硕士期间主要工作

读研期间，除了完成既有课程之外，也积极参与到实验室的项目开发中。

### 1.定位结果的手机终端显示

主要是完成定位结果在手机上的实时显示任务，场景主要有工控新楼 5 楼，新楼 511 室内和教九 526 装修前。

![手机定位显示](https://ws4.sinaimg.cn/large/006tKfTcly1g19iqhe277j30d108tta6.jpg)

### 2.免时钟同步、交互式声信号室内定位系统

利用 BeepBeep 原理，建立一种免时钟同步的声信号室内定位系统。具体的原理可以参看实验室往届师兄的毕业论文（文祥计、林峰）。系统主要分为两部分，一部分是声信号信标节点（Android 系统的 smartphone 或者 树莓派），另一部分是待定位目标，即用户的手机。目前需要工作在同一局域网下。

![声信号定位系统结构图](https://ws1.sinaimg.cn/large/006tKfTcly1g19iwwu47yj306l06kq2y.jpg)

由于适应比赛场地多楼层的需要，将节点网络设置成了两组，与用户交互的信标节点分别是 5 号点和 10 号点，该定位算法需要预知每个点与这两个点之间的距离，需要在实验前测量好并输入进去。楼层的切换导致交互节点的切换，楼层的判别由手机上的气压计变动所决定，在实验前，需设置好各楼层的气压值。

![手机端程序 UI](https://ws4.sinaimg.cn/large/006tKfTcly1g19jjgmo9vj305z0azt9j.jpg)

代码仓库为：
- 往届师兄的版本：TheUser 和 TheBeacon
- 比赛版本：AALocUser 和 AALocBeacon

### 3.跌倒检测相关的研究与系统实现

#### 3.1 开发基于 Android 的传感器数据采集应用

手机上有的传感器数据均可采集，一般包括 Accelerometers, Gyroscopes, Magnetometers, Pressure, Gravity, LinearAccelerometers, Rotation 等。
一次实验采集到的数据会在手机内存中存储为一个txt文件，文件中标注了设备型号、品牌、实验的时间、数据格式、传感器参数等详细信息，每一行记录一条传感器数据，同时记录下记录的时刻。

```plain
% LogFile created by the 'SensorInfo' App for Android.
% Date of creation: Tue Jan 06 11:22:53 GMT+08:00 2017
% Developed by Tristan in ISMC research group at ZJU, China.
% The 'SensorInfo' program stores information from Smartphone/Tablet internal sensors (Accelerometers, Gyroscopes, Magnetometers, Pressure, Gravity, LinearAccelerometers, Rotation) .
% 
% The model of device:  Nexus 4
% The Manufacturer:     LGE
% 
% LogFile Data format:
% Accelerometer data: 	'ACCE;AppTimestamp(s);SensorTimestamp(s);Acc_X(m/s^2);Acc_Y(m/s^2);Acc_Z(m/s^2);Accuracy(integer)'
% ... 中间省略
% LinearAcc data:   	'LACC;AppTimestamp(s);SensorTimestamp(s);Lacc_X(m/s^2);Lacc_Y(m/s^2);Lacc_Z(m/s^2);Accuracy(integer)'
% 
% The info of Sensors:
% Accelerometer Sensor:
% 			Name:       LGE Accelerometer Sensor
% 			Vendor:     InvenSense
% 			Power:      0.5
% 			MaxRange:   39.226593
% 			Resolution: 0.0011901855
% ... 中间省略
% Rotation Sensor:
% 			MaxRange:   1.0
% 			Resolution: 5.9604645E-8

MAGN;444173722;444173721;-6.3598633;-26.278687;-28.73993;3;
PRES;444173723;444173722;1001.87933;0;
... 中间省略
PRES;444173924;444173923;1001.84937;0;
MAGN;444173944;444173943;-6.298828;-25.439453;-28.079224;3;
```

#### 3.2 本地测量到的跌倒数据

在 MSLabPlatform/MSLabPlatform_Fall_Detection 中的 log_files 和 database 中，数据来源是上面实测得到的txt处理而来，处理的matlab代码在同一文件目录下。对这些数据的处理当时主要是用的 matlab ，并依托这些数据撰写了会议论文"Wavelet Package Analysis based Fall Detection and Diagnosis"。

![](https://ws2.sinaimg.cn/large/006tKfTcly1g1aar0rlevj30he0d2dja.jpg)

#### 3.3 发表一篇会议论文

M. Huang, X. Wang, P. Sun, S. Wang and Z. Wang, "Wavelet Package Analysis based Fall Detection and Diagnosis", 2018 37th Chinese Control Conference (CCC), Wuhan, 2018, pp. 4206-4211.
doi: 10.23919/ChiCC.2018.8483116

**Abstract:** As a possible hazard to public health, the fall problem has gradually attracted researchers' attention. Detecting the occurrence of fall and diagnosing its intensity can be critical and helpful for deciding the next move. In this work, a novel accelerometer-based signal processing and analysis framework for fall detection and diagnosis is proposed. Wavelet package decomposition (WPD) is introduced for denoising and multi-resolution time-frequency analysis of signals from smartphone's accelerometer sensor. The extraction of features takes into account the statistical properties in both time domain and wavelet domain. To reduce the computational complexity of training and testing the classifiers, the reduction of dimension is performed by additionally evaluating features with principal component analysis (PCA). Then these features become the input of the first classifier for fall detection and if a fall occurs, the second classifier for intensity diagnosis will take the matter further. Test subjects undertake the experiments of falls and activities of daily living (ADLs) to generate data for analysis. The performance of classification based on different algorithms including k-nearest neighbor (k-NN) and support vector machine (SVM) is presented and compared. The good results indicate this work's applicability in real-world scenarios.

**keywords:** intensity diagnosis;fall problem;public health;accelerometers;Fall detection;Multi-resolution analysis

URL: http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8483116&isnumber=8482271


![](https://ws3.sinaimg.cn/large/006tKfTcly1g1aao3mwi0j30ms096t96.jpg)

#### 3.4 MSL整合平台

即 MSLabPlatform 项目，项目包括 Android 端和 PC 端，其中 PC 端目前主要运行在 matlab 上，通过引入 Java api 实现与 Android 手机的 socket 连接并传输与获取数据。

#### 3.5 UCI 公开数据集及相关处理

UCI Machine Learning Repository: Simulated Falls and Daily Living Activities Data Set Data Set

URL：https://archive.ics.uci.edu/ml/datasets/Simulated+Falls+and+Daily+Living+Activities+Data+Set

该数据集相关的数据提取及相关代码处理在下面的 URL 中

URL：https://github.com/MSLabZJU/MSLabPlatform/tree/master/MSLabPlatform_Fall_Detection/uci%20data


## 毕业论文主要内容

跌倒及其后续所可能引发的问题对于老年人来说是生命健康的严重威胁，跌倒检测技术的研究可以减少跌倒后长时间救助缺失的现象，避免造成更严重的伤害。本文详细调研了国内外相关研究领域的研究，选择了基于可穿戴式设备实现跌倒检测。针对该类研究工作中常存在的传感器定制化、检测精度不高、设备放置位置侵入性较强、系统的功耗不合理和对网络传输可靠性要求高等问题，本文提出了低功耗的定位信息辅助决策的阈值算法和基于GBDT-SVM 融合模型的分类算法，创新性地使用双轨融合决策机制，并基于通用智能设备实现跌倒检测原型系统。本文的主要工作及创新性如下:

1)提出一种对跌倒敏感、对日常活动保持钝感的时序信号窗口提取方法，避免定长滑动窗口检测造成的持续性的功耗浪费，增强了算法在智能手表等资源受限设备上的适用性，减少了不必要的检测，也在一定程度上提升了检测精度。

2)提出一种定位信息辅助决策的阈值算法。针对跌倒动作的信号特点，选择了具有较好区分度且计算量较小的特征指标，以检测跌倒，保证用户的生命健康为第一准则，构建了跌倒事件查全率较高的阈值算法，再通过引入定位信息，利用跌倒后的人体高度信息排 除掉一部分非跌倒动作，降低了误报率。

3)提出一种 GBDT-SVM 融合模型的分类算法，取得了非常好地分类效果，且模型经过验证对现实中多种跌倒和日常活动具有非常好的泛化性能。使用 GBDT 模型对原始特征作自动组合，增强了原特征的非线性表达能力。同时，生成的新的稀疏 0/1 特征大大加快了模型训练和检测的速度，对于系统具体实现时保障远程处理速度有重要意义。

![组合特征与原始特征的效果比对](https://ws2.sinaimg.cn/large/006tKfTcly1g19i6kmzmfj30k0080wel.jpg)


4)系统实现上提出了一种适应不同场景和网络状况的双轨融合决策机制。一方面在本地执行低功耗的定位信息辅助阈值算法，另一方面在网络状况允许的条件下在远程进行更 复杂的基于 GBDT-SVM 融合模型的检测算法，两部分的检测相互独立，但最终按一定的规则融合决策，同时充分考虑了网络连接的延迟和不可用问题，决定采取何种程度的介入和提醒方式，增强了系统的整体可用性和实用性。在对原型系统的实际场景验证中，对固定 动作类型的检测精度可以达到 98% 以上，且对未知动作类型也能保证非常好地鲁棒性。

![跌倒检测系统架构图](https://ws2.sinaimg.cn/large/006tKfTcly1g19i3zvefkj31xw0na10l.jpg)