more:

[如何打造高质量的机器学习数据集？](<https://www.zhihu.com/question/333074061/answer/773825458>)



refer:

[深度学习中有什么方法可以找出训练集中脏数据(比如标记错误的数据)？](https://www.zhihu.com/question/298719271)





### Books

+ Natural Language Annotation
+ Human-in-the-Loop Machine Learning





### Paper





+ MultiWOZ
+ Swag: A Large-Scale Adversarial Dataset for Grounded Commonsense Inference.
+ ...
+ ImageNet, ShapeNet, OpenImage...



### Architecture

generate datasets -> baseline -> badcase study -> update strategies -> generate datasets



step 1 - converge in training dataset

step 2 - validate in develop/validation set

step 3 - badcase study



### Principles

+ baseline 

  should simple enough without too much parameter tuning

  should without overfitting
  
+ human labeled develop and validation set





### Strategies 

Semi-supervised learning



#### Check

标注质量检查主要由两个问题：一个是错标，一个是漏标。

1. 快速检测可以用hmm，或者crf，自训练并自测。有点：速度比深度学习模型要快，而且可以找到很多提示性信息。比如模型预测出来了，我们没标出来，则推荐给我们候选漏标集合；如果模型没预测出来，但是我们标注出来了，则推荐给我们错标集合。
2. 边界一致性检查。很多时候不同标注人员，边界标的不一致，比如xx元，有的人标了元，有的人没标元，会导致正负样本矛盾。可以去边界左边的字构成集合，去边界右边的字构成集合，取交集，来查找边界一致性。
3. 上下文相似性计算。查找统一字段上下文构成集合，查找偏差过大的上下文数据。





### Tools

- <https://www.datasetlist.com/tools/>

  Annotation tools for building datasets
  
- <https://github.com/heartexlabs/awesome-data-labeling>







