# CoLA: Weakly-Supervised Temporal Action Localization with Snippet Contrastive Learning
## Abstract  
弱监督时间动作定位(WS- TAL)的目标是在只有视频级标签的未修剪视频中定位动作。现有模型大多遵循分类定位过程:定位对视频级分类贡献最大的时间区域。一般来说，他们单独处理每个片段(或框架)，从而忽略了卓有成效的时间上下文关系。这里出现了单片段欺骗问题:硬片段宠物太模糊，无法分类。在本文中，我们认为通过比较来学习有助于识别这些硬片段，我们建议利用片段对比学习来定位动作，简称CoLA。具体来说，我们提出了一个Snippet Contrast (SniCo) Loss来细化特征空间中的硬Snippet表示，它指导网络感知精确的时间边界，避免时间间隔中断。此外，由于访问帧级注释是可行的，我们引入了硬代码段挖掘算法来定位潜在的硬代码段。大量的分析证明，这种挖掘策略有效地捕获了硬片段，SniCo损失导致了更多信息的特征表示。大量的实验表明，CoLA在THUMOS 14和ActivityNet v1.2数据集上取得了最先进的结果。
## 解决问题
难片段模糊，无法分类，可能被错误的分类，进而导致得到的时间边界模糊。如何选择难片段，本文先使用对T-CAS进行阈值处理，使用膨胀腐蚀操作找到难边界，包括难动作和难背景，难片段 简单正例 简单负例一同做对比学习 优化snippet-level feature 以及获得more informative feature distribution