# Enriching Local and Global Contexts for Temporal Action Localization
## 摘要  
有效地解决时间动作定位(TAL)问题需要一个共同追求两个混淆目标的视觉表示，即时间定位的细粒度识别和动作分类的充分视觉不变性。我们通过在流行的两阶段时间本地化框架中丰富本地和全球背景来解决这一挑战，在这一框架中，首先产生行动建议，然后是行动分类和时间边界回归。我们提出的模型称为ContextLoc，可分为三个子网络:L-Net、G-Net和P-Net。L-Net通过对片段级功能的细粒度建模来丰富本地上下文，该功能被描述为一个查询和检索过程。G-Net通过对视频级表示进行更高层次的建模，丰富了全局环境。此外，我们还引入了一个新的上下文适应模块，以适应全球上下文不同的提议。P-Net进一步建模上下文感知的提议间关系。在我们的实验中，我们探索了两种已有的模型作为P-Net。在THUMOS14 (tIoU@0.5上的54.3%)和Activ- ityNet v1.3 (tIoU@0.5上的56.01%)数据集上的实验结果验证了我们提出的方法的有效性，这些结果超过了最新的技术水平。
## 1.Introduction
**task**：它的目的是对未修剪的视频中的动作进行分类，并定位它们的时间边界
**一步法**：One-stage approaches classify and locate action instances from an input video in a single shot.  
*就是说从帧入手，直接生成动作实例的分类与位置*
**两步法**： Two-stage approaches first generate category-agnostic action proposals and then per- form action classification and temporal boundary refinement  for each proposal. 
*先产生proposal，在进行分类与细化的定位*
**做好TAL，需要**：细粒度的定位以及能够实现动作分类的视觉不变性
**local context**：They contain fine-grained temporal information that is crit- ical to localization  
*能够从局部上下文中得到细粒度的定位信息*
*其他方法只用maxpool，不可避免地丢弃了细粒度的时间信息*
**global context**: 关注整个视频的信息，比如我们不太可能在家庭视频中看到体育活动
*其他方法忽略了global context*
### 本文贡献
提出了三种net
**L-Net**:收到self-attention启发，仍有query与key 只不过在L-Net算法中，query为 the feature of a proposal key为the feature of snippets 两者相互match 以便在local context细粒度的值融合到proposal中
**G-Net**:对global context 建模 通过整合video-level representation and features of each proposal 为了有效地集成视频级信息和提议级特征，我们提出了全局上下文自适应。它将视频级表征加到每个proposal中的local context，以便全局上下文分别适应它们
**P-Net**：P-Net 建模上下文感知的建议间关系。这包括由local context增强的提案级别特征之间的交互，以及适应不同提案的global context之间的交互。我们使用现有模型作为 P-Net 并研究两个候选模型：P-GCN [44] 和非本地网络 [40]。
**总结**：我们引入了一种新的网络架构，称为 ContextLoc，由三个子网络组成，即 L-Net、G-Net 和 P-Net。 L-Net 是同类中第一个使用提议来查询其中的片段并检索本地上下文以用细粒度的时间信息对其进行补充的。 G-Net 通过集成视频级表示来增强每个提案的特征。 我们引入了一种新的上下文适应过程来使全局上下文适应不同的提议。 虽然 P-Net 建立在现有网络上，但我们表明，无论其实例如何，P-Net 都是对我们的 L-Net 和 G-Net 的补充。 我们的 ContextLoc 统一了这三个子网络的各自优势
[论文解读](https://blog.csdn.net/Biany0h0/article/details/119534471)