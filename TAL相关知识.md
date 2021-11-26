# Temporal Action Detection (Localization)
## 伪标签（Pseudo-Labelling）——锋利的匕首
[相关讲解](https://zhuanlan.zhihu.com/p/157325083?from_voters_page=true)  
>粗略来讲，伪标签技术就是利用在已标注数据所训练的模型在未标注的数据上进行预测，根据预测结果对样本进行筛选，再次输入模型中进行训练的一个过程。  
## 标签稀疏：多分类问题中每一类样本数量不多
[卷积神经网络中一维卷积的计算过程](https://www.cnblogs.com/talkaudiodev/p/14287562.html)  
[理解Focal Loss](https://zhuanlan.zhihu.com/p/80594704)  
>而本文的作者认为，易分样本（即，置信度高的样本）对模型的提升效果非常小，模型应该主要关注与那些难分样本  

[如何理解fine-grained和coarse-grained？](https://www.zhihu.com/question/299171510)  
[如何理解visual invariance(不变性)](https://zhuanlan.zhihu.com/p/21464947)  
>在视觉领域，一个古老/经典的问题是各种不变性：当你看到一个人的脸时，不论ta的脸在你视野中的什么位置（位置不变性），ta朝向什么角度（角度不变性），离你有多远（大小/距离不变性），等等，在这些不同情况下，你的眼睛所看到的图像都是极为不同的，但你都可以轻松地认出ta是谁。这是如何做到的呢？  

[action proposal(dection)](https://blog.csdn.net/sinat_35177634/article/details/88918421)
>其主要目的是将长视频根据语义分割成多个segment，因为现在的针对视频的任务对长视频处理并不理想，比如视频的action detection和caption等。因此需要现将长视频分割成多个短视频，再进行处理。temporal action proposals是根据长视频的动作语义信息在时间维度来对长视频进行分割，保证每个segment包含一个action。本文将介绍两种方法，一种是2016年在ECCV上提出的DAPs，另一个是2017年CVPR的SST，SST也是DAPs的改进版，也是我们重点讨论的

## TAL的一步法和两步法
**一步法**：One-stage approaches classify and locate action instances from an input video in a single shot.  
*就是说从帧入手，直接生成动作实例的分类与位置*
**两步法**： Two-stage approaches first generate category-agnostic action proposals and then per- form action classification and temporal boundary refinement  for each proposal. 
*先产生proposal，在进行分类与细化的定位*
[非极大值抑制（non-maximum suppression）的理解](https://blog.csdn.net/xiexu911/article/details/80609298)
[optical flow 光流](https://en.wikipedia.org/wiki/Optical_flow)

[Video Analysis 相关领域解读之Temporal Action Detection(时序行为检测)](https://zhuanlan.zhihu.com/p/26603387)
[[ECCV 2018] 用于时序动作提名生成的边界敏感网络BSN](https://zhuanlan.zhihu.com/p/39327364)


提出TAL在弱监督：*Tempo- ral localization of fine-grained actions in videos by domain transfer from web images.*   
使用软选择模块（类似于注意力机制）*Untrimmednets for weakly supervised action recognition and detection.*  
提出a sparse loss function to facilitate the selection of segments：*Weakly supervised action localization by sparse temporal pooling network*
autoloc提出OIC