

## Motivation

1. 可解释性
2. 易于优化



## Paper

+ 《Next-generation architectures bridge gap between neural and symbolic representations with neural symbols | Microsoft Research》 http://t.cn/AiD4sRFc 
+ Harnessing Deep Neural Networks with Logic Rules
  Zhiting Hu, Xuezhe Ma, Zhengzhong Liu, Eduard Hovy, Eric Xing ACL 2016 **Outstanding Paper Award**! [arxiv](<https://arxiv.org/abs/1603.06318>) 



## Methods

+ 深度学习模型结果作为特征

  分别训练
  协同训练

  深度学习模型结果相当于预处理，作为特征

  

  LSTM+CRF - (序列标注任务)

  

  CNN+CRF

  DeepLab: Semantic Image Segmentation with Deep Convolutional Nets, Atrous Convolution, and Fully Connected CRFs 
  [Liang-Chieh Chen](<http://liangchiehchen.com/projects/DeepLab.html>), George Papandreou, Iasonas Kokkinos, Kevin Murphy, Alan L. Yuille [arxiv](<https://arxiv.org/abs/1606.00915>) :star::star::star::star:

  

+ 规则为主，模型为辅

  头部问题用模板和规则的方式处理。如模板的挖掘，可以采用BootStraping方法. 规则包括无监督学习、半监督学习方式，基于语言学规则实现，可覆盖大部分场景。

  长尾问题采用模型来处理，泛化剩余部分.

  
  
  refer: AIcon 2019
  
  知识图谱在小米的落地与挑战 https://aicon.infoq.cn/2019/beijing/#speakers







