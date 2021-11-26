# Graph Convolutional Networks for Temporal Action Localization
**利用图来构建proposal的关系**   
**与self-attention相比：**self-attention是通过自动学习的聚合权重把其他所有proposal的信息都聚合到一个proposal上，因为proposal数量通常很多，使得计算量巨大，成本太高。
而 GCN只是聚合相邻node的信息，使得计算量大幅度降低。
**图的构建**Contextual Edges r(pi,pj)=tIoU(pi,pj)
r>theta 
Surrounding edges  if r(pi,pj)=0 d(pi,pj)=|ci-cj|/U(pi,pj) d(pi,pj)<theta  
X(k)=AX(k-1)W(k) A:邻接矩阵 W：参数   
A余弦相似度 
[GCN for Temporal Action Localization论文详细解读](https://zhuanlan.zhihu.com/p/134638106)