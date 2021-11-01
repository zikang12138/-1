# ACM-Net
## introdution
### 目前存在的
**formulate  the  weakly-supervised  temporal  actionlocalization  as  a  video  recognition  problem  and  introducea  foreground-background  separation  attention  mechanism  toconstruct  video-level  features:**
*.  Nguyen,  T.  Liu,  G.  Prasad,  and  B.  Han,  “Weakly  supervised  actionlocalization by sparse temporal pooling network,” inCVPR, 2018.
[12]  K. Min and J. J. Corso, “Adversarial background-aware loss for weakly-supervised temporal activity localization,” inECCV, 2020.
[13]  T. Yu, Z. Ren, Y. Li, E. Yan, N. Xu, and J. Yuan, “Temporal structuremining for weakly supervised action detection,” inICCV, 2019.
[14]  P.  X.  Nguyen,  D.  Ramanan,  and  C.  C.  Fowlkes,  “Weakly-supervisedaction localization with background modeling,” inICCV, 2019.*
**MIL:**  
Treat  the  entire  untrimmed  video  as  a  bagcontaining both positive and negative instances, i.e. foregroundaction  instances  frames  and  background  non-action  frames  
These methods first apply a classifier to obtain temporal-pointclass  activation  sequence  (CAS)  and  then  employ  a  top-kmechanism to aggregate the video-level classification scores
*[19]  S. Paul, S. Roy, and A. K. Roy-Chowdhury, “W-talc: Weakly-supervisedtemporal activity localization and classification,” inECCV, 2018.
[20]  Y. Yuan, Y. Lyu, X. Shen, I. W. Tsang, and D.-Y. Yeung, “Marginalizedaverage  attentional  network  for  weakly-supervised  learning,”  inICLR,2019.
[21]  P.  Lee,  Y.  Uh,  and  H.  Byun,  “Background  suppression  network  forweakly-supervised temporal action localization,” inAAAI, 2020.
[22]  Z.  Luo,  D.  Guillory,  B.  Shi,  W.  Ke,  F.  Wan,  T.  Darrell,  and  H.  Xu,“Weakly-supervised  action  localization  with  expectation-maximizationmulti-instance learning,” inECCV, 2020*
### 存在问题
难以区分context与action,
### METHODOLOGY
**freature extraction:**RGB 与光流 I3D
**Feature Embedding:**卷积特征F  X=ReLU(Conv(F,theta))
**Action Class Activation Modeling:** CAS=MLP(X,theta)
**Action Context Attention Modeling** 𝐴=Softmax(Conv(𝑋,𝜃𝑎𝑡𝑡ºº)) A={(att_ins att_con att_bak} CAS_ins=att_int*CAS 同理 CAS_con CAS——bak都能得到
**Multiple-Instance  Learning**top-k 取各个branch的CAS k最大的平均，用softmax计算p 分别为p_ins p_con p_bak
*top-k 计算每类的CAS的最大k值的平均 作为该类出现的概率表示*
每一个分支的损失，L=-ylog(p) y_ins=[yn=1,y(c+1)=0] y_con=[yn=1 y(c+1)=1] y_bak=[yn=0 y(c+1)=1]
L_cls=Lins+Lcon+Lbak
**Optimization Objects** L=L_cls+L_add   L_add=L_gui+L_feat+L_spa
L_gui 优化片段级别的结果 使用p与att_ins att_ins是片段级注意力，p是上文得出的
L_feat 为了feature更加的distinguishable
