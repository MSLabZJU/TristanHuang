# TristanHuang
2019届毕业研究生-黄美川

:e-mail: 联系方式：[tristanhuang@foxmail.com](mailto:tristanhuang@foxmail.com)
:computer: 个人主页：[tristanhuang.cn](http://tristanhuang.cn)


## 硕士期间主要工作
读研期间，除了完成既有课程之外，也积极参与到实验室的项目开发中。

### 1.实验室交互式定位系统（基于智能手机）开发
2. 跌倒检测系统研究与实现

## 

## 毕业论文主要内容

跌倒及其后续所可能引发的问题对于老年人来说是生命健康的严重威胁，跌倒检测技术的研究可以减少跌倒后长时间救助缺失的现象，避免造成更严重的伤害。本文详细调研了国内外相关研究领域的研究，选择了基于可穿戴式设备实现跌倒检测。针对该类研究工作中常存在的传感器定制化、检测精度不高、设备放置位置侵入性较强、系统的功耗不合理和对网络传输可靠性要求高等问题，本文提出了低功耗的定位信息辅助决策的阈值算法和基于GBDT-SVM 融合模型的分类算法，创新性地使用双轨融合决策机制，并基于通用智能设备实现跌倒检测原型系统。本文的主要工作及创新性如下:

1)提出一种对跌倒敏感、对日常活动保持钝感的时序信号窗口提取方法，避免定长滑动窗口检测造成的持续性的功耗浪费，增强了算法在智能手表等资源受限设备上的适用性，减少了不必要的检测，也在一定程度上提升了检测精度。


2)提出一种定位信息辅助决策的阈值算法。针对跌倒动作的信号特点，选择了具有较好区分度且计算量较小的特征指标，以检测跌倒，保证用户的生命健康为第一准则，构建了跌倒事件查全率较高的阈值算法，再通过引入定位信息，利用跌倒后的人体高度信息排 除掉一部分非跌倒动作，降低了误报率。

3)提出一种 GBDT-SVM 融合模型的分类算法，取得了非常好地分类效果，且模型经过验证对现实中多种跌倒和日常活动具有非常好的泛化性能。使用 GBDT 模型对原始特征作自动组合，增强了原特征的非线性表达能力。同时，生成的新的稀疏 0/1 特征大大加快了模型训练和检测的速度，对于系统具体实现时保障远程处理速度有重要意义。

4)系统实现上提出了一种适应不同场景和网络状况的双轨融合决策机制。一方面在本地执行低功耗的定位信息辅助阈值算法，另一方面在网络状况允许的条件下在远程进行更 复杂的基于 GBDT-SVM 融合模型的检测算法，两部分的检测相互独立，但最终按一定的规则融合决策，同时充分考虑了网络连接的延迟和不可用问题，决定采取何种程度的介入和提醒方式，增强了系统的整体可用性和实用性。在对原型系统的实际场景验证中，对固定 动作类型的检测精度可以达到 98% 以上，且对未知动作类型也能保证非常好地鲁棒性。