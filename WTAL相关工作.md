# 弱监督动作定位汇总
简称|方法介绍|出处|年份
:-:|:-:|:-:|:-:
UntrimmedNet|first to present weakly-supervised temporal action localization, which cou- ples classification module and selection module to learn an action localization model|UntrimmedNets for Weakly Supervised Action Recognition and Detection *Wang et al* |2017 
STPN|designs attention weights modules|Weakly Supervised Action Localization by Sparse Temporal Pooling Network*Phuc Nguyen et al*|2018    
AutoLoc|proposal Outer-Inner-Contrastive(OIC) |AutoLoc: Weakly-supervised Temporal Action Localization in Untrimmed Videos|2018
CMCS|using Context Modeling|Completeness Modeling and Context Separation for Weakly Supervised Temporal Action Localization *Daochang Liu et al*|2019  
BM|using Background Modeling|Weakly-supervised Action Localization with Background Modeling *Phuc Xuan Nguyen et al*|2019   
|MAAN|proposed a novel marginalized average aggregation module and latent discriminative probabilities to reduce the difference between the most salient regions and the others|Marginalized  Average  Attentional  Network  forWeakly-Supervised Learning*Yuan et al*|2019
|TSM|each action instance as a multi-phase process to effectivately characterize action instances|Temporal structure mining for weakly supervised action dection|2019  
|Clean-Net|introduced  an  action  proposal  eval-uator  that  provides  pseudo-supervision  by  leveraging  thetemporal contrast in snippets||2019
|WSGN|assigns a weight to each frame prediction based onboth  local  and  global  statistics|Weakly  su-pervised  Gaussian  networks  for  action  detection.|2020
BaSNet|designs a background suppression network to suppress background activation|Background suppression network for weakly-supervised temporal action localization|2020  
UM|top-k|UntrimmedNets for Weakly Supervised Action Recognition and Detection|2020  
TSCN|introduces a two-stream consensus network, which employs an iterative refinement training strategy to obtain a precise prediction.|Two-stream consensus network for weakly-supervised temporal action localization|2020  
DGAM|uses conditional variational auto-encoder to solve the action context confusion problem.|Weakly-supervised action localization by generative attention modeling|2020  
ActionBytes|brings in short trimmed videos to assist in learning to localize untrimmed videos.|Actionbytes: Learn- ing from trimmed videos to localize actions|2020  
ACL|utilizes class-specific and class-agnostic attention simultaneously.|Learning temporal co-attention models for unsupervised video action localization|2020  
A2CL-PT|adopts an adversarial approach to localize more complete actions|Adversarial background-aware loss for weakly-supervised temporal activity localization|2020  
EM- MIL|proposes an expectation-maximization multiple instance learning framework to optimize the likeli- hood of lower bound|Weakly-supervised action localization with expectation- maximization multi-instance learning|2020
ACM-Net|three-branch (background context instance)|ACM-Net: Action Context Modeling Network for Weakly-Supervised Temporal Action Localization|2021  
CoLA|本文认为大多数方法忽略了context，并且出现了snip cheating问题：hard snippet 太模糊难以分类。本文通过比较学习 并且引入了SniCo|CoLA: Weakly-Supervised Temporal Action Localization with Snippet Contrastive Learning|2021  

# CAS的生成方式
|Method|Operations|
:-:|:-:|  
UntrimmedNets (Wang et al. 2017)|FC
STPN (Nguyen et al. 2018)|FC+ReLU+FC
3C-Net (Narayan et al. 2019)|[FC+ReLU]×2+FC  
BaS-Net (Lee et al. 2020)|[Conv+ReLU]×2+Conv 
A2CL-PT (Min and Corso 2020)|FC+ReLU+Conv
ACL (Gong et al. 2020b)|Conv+ReLU+FC
EM-MIL (Luo et al. 2020)|Conv+ReLU+FC
SF-Net (Ma et al. 2020)|[FC+ReLU]×2+FC
ACM-Net(Sanqing Qu et al)|[Conv1d+Softmax]×2+FC

# aggregation operations
![aggregation operations](image\aggregation.png)  
