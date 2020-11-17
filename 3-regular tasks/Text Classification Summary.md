refer:

Text Classification Algorithms: A Survey, Kamran Kowsari, 2019, [arxiv](https://arxiv.org/abs/1904.08067v3) 



#### 数据构建



##### 数据构建

根据业务目标，明确当前的问题及其边界，将其转化为模型可以解决的问题，据此，选择相应的训练数据。



##### 数据探索

探索性数据分析：

1. 基本统计

   文本长度、样本分布等

2. 文本聚类

   聚类结果以可视化方式呈现

###### Tools

Paper: Scattertext: a Browser-Based Tool for Visualizing How Corpora Differ

Scattertext visualizes differences and similarities of word frequencies in examples.

##### 非不平衡样本

针对样本分布不平衡问题：

1. 人工增加少类样本

2. 采样方法

   A class imbalance could be easily handled by ensuring that each minibatch will have at least one sample from every class (this leads to situations when some samples will be used much more frequently than another, but who cares).

   1）上采样

   增加样本数较少的样本，其方式是直接复制原来的样本。样本较少时采用。

   2）下采样

   减少样本数较多的样本，其方式是丢弃这些多余的样本（譬如随机选择、active learning选择等）。样本较多时采用。

   3）rejection sampling

   [rejection sampling](https://tensorflow.google.cn/api_docs/python/tf/data/experimental/rejection_resample) 

   [随机模拟的基本思想和常用采样方法](https://blog.csdn.net/xianlingmao/article/details/7768833) 

3. 相似性检索

   样本数较多的类别作为database，样本数较少的类别作为query。从database中检索top-5最相似的文本作为负样本。

4. 主动学习

   随机抽取多类样本，构建baseline模型，利用主动学习方式将多类样本中预测错的样本加入训练样本，重新训练模型，不断迭代。因此，可以选择hard example作为负样本。

5. 集成学习方法

   using ensemble method to train each classifier with an even distributed subset.

6. 代价敏感学习方法

   1) loss - Upweighting positive samples 

   Adjust the loss of unbalance fewer classes, force the models learning that class samples more seriously.

   

   This refers to increasing the losses of misclassified positive samples when training on datasets that have much fewer positive samples. This incentivizes the ML algorithm to learn parameters that are better for positive samples. For example:

   [weighted_cross_entropy_with_logits](https://tensorflow.google.cn/api_docs/python/tf/nn/weighted_cross_entropy_with_logits) 

   [sparse_softmax_cross_entropy](https://tensorflow.google.cn/api_docs/python/tf/losses/sparse_softmax_cross_entropy) 

   There is a standard losses function now that supports weights per batch:

   ```
   tf.losses.sparse_softmax_cross_entropy(labels=label, logits=logits, weights=weights)
   ```

   Where weights should be transformed from class weights to a weight per example (with shape [batch_size]).

   https://stackoverflow.com/questions/35155655/loss-function-for-class-imbalanced-binary-classifier-in-tensor-flow?answertab=votes#tab-top

   2) sample - 增加少量样本权重

   

   3) metric - 选择代价敏感评价函数（如AUC指标）

   AUROC is based on ture positive rate and false positive rate, which doesn't tell how well it works on each instance, so it's can't be maximize. 



###### Question

+ 如何处理多标签分类的非平衡问题？

  paper: Inverse random under sampling for class imbalance problem and its application to multi-label classification

+ Is there any loss function for unbalance dataset ?

  https://stackoverflow.com/questions/30486033/tackling-class-imbalance-scaling-contribution-to-loss-and-sgd?rq=1

  



##### 负样本

主要针对二分类问题中的负样本选择。

负样本选择方法：

1. 随机选择

2. 相似性选择

   利用相似性算法选择不同类别的样本作为该类别的负样本。



#### 数据预处理

主要功能模块：

Tokenization  - stop words remove, punctuation and special characters remove, lower case, abbreviation,  slang(俚语)...

Spelling Correction (optional) - Many techniques and methods are available for researchers including hashing-based and context-sensitive spelling correction techniques [50], as well as spelling correction using Trie and Damerau–Levenshtein distance bigram [51].



##### 归一化

文本归一化，包括特殊符号过滤、大小写归一、繁体转简体、全角转半角等操作。

###### 实体归一化

在分类任务中，可以通过NER技术将待分类文本中出现的地点，组织和人名替换为<place>，<org>和<person>，减少OOV，也有助于减少VOC的大小，加快收敛，节省存储和计算时间。



Case:

<https://github.com/xueyouluo/fsauor2018>



##### 向量化

基于字符级的输入：

数据预处理较少



基于词级的输入：

数据预处理主要在于分词，其准确性依赖于分词词典的构建。



character/word embedding vs one-hot embedding

当数据量足够时，one-hot embedding更有优势。

 

##### 文本增强

常见的文本增强方法：

1. 改写

   1）回译

   先翻译成其他语言，再翻译回中文

   2）相似句

   检索库中相近的Top-k句子，作为该句的相似句

   

2. 扩展

   主要针对短文本。

   1）同义词

   利用同义词库扩展当前文本

   2）知识图谱

   利用知识图谱扩展相关内容

   

#### 模型选择

设置baseline模型，探索简单模型在当前数据集的性能。

常见的baseline模型，主要有TF-IDF+SVM等。



##### 目标函数

目标函数的选择，关系到模型的优化方向，原则是尽可能与业务目标保持一致。

1. 二分类

   sigmoid cross entropy

   也可用于多标签分类问题.
   $$
   sigmoid(y) = \frac{1}{1+e^{-y}}
   $$
   $L(y,\hat{y}) = -\frac{1}{2}(\hat{y} \cdot log(sigmoid(y)) + (1-\hat{y}) \cdot log(1-sigmoid(y)))$

   

   balanced sigmoid cross entropy

   主要针对二分类非平衡样本
   $$
   sigmoid(y) = \frac{1}{1+e^{-y}}
   $$
   $L(y,\hat{y}) = -\frac{1}{2}(\beta \cdot \hat{y} \cdot log(sigmoid(y)) + (1-\beta) (1-\hat{y}) \cdot log(1-sigmoid(y)))$ 

   

   

2. 多分类

   softmax cross entropy
   $$
   softmax(y_i) = \frac{e^{y_i}}{\sum^n_{i=1} e^{y_i}}
   $$
   $L(y,\hat{y})=-\frac{1}{n} \sum^n_{i=1} \sum^m_{j=1} \hat{y}_{i,j} \cdot log(softmax(y_{i,j}))$, $m$ is the number of class.

   

   In sklearn, there are two modification for [this logloss function](https://github.com/scikit-learn/scikit-learn/blob/14031f6/sklearn/metrics/classification.py):

   1) if $softmax(y_{i,j})=0$,  then replace it with 1e-15​.
   
   2) move the $\frac{1}{n}$ in $log$ function.
   
   
   
   
   
   focal loss
   
   主要针对多分类非平衡样本
   $$
   softmax(y_i) = \frac{e^{y_i}}{\sum^n_{i=1} e^{y_i}}
   $$
   $L(y,\hat{y})=-\frac{1}{n} \sum^n_{i=1} \hat{y}_i \cdot \alpha_i \cdot (1-softmax(y_i))^\gamma log(softmax(y_i))$





###### Question

+ what's the difference between sigmoid and softmax ? What's the advantage and disadvantage each other ?

+ why the focal loss is better for unbalance dataset, especially for hard example ?

  [Focal Loss for Dense Object Detection - ICCV2017](https://arxiv.org/abs/1708.02002) 

+ why the center loss is better than softmax loss ?

  A Discriminative Feature Learning Approach for Deep Face Recognition
  论文链接：http://ydwen.github.io/papers/WenECCV16.pdf 

  代码链接：https://github.com/ydwen/caffe-face

+ 





#### 评价指标

主要功能模块：

recall, precision, accuracy, F-measure, micro-average, and macro average

These metrics are based on a “confusion matrix” that comprises true positives (TP), false positives (FP), false negatives (FN), and true negatives (TN).



scikit-learn: [f1_score](<https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html>), [precision_recall_fscore_support](<https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_fscore_support.html>), [classification_report](<https://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html>) 



##### 指标

Accuracy
$$
Accuracy = \frac{TP+TN}{TP+FP+TN+FN}
$$
It is the simplest method of evaluation but does not work for unbalanced data sets.



Precision
$$
Precision = \frac{TP}{TP+FP}
$$
Recall

$$
Recall = \frac{TP}{TP+FN}
$$


$F_1$-Score

当准确率和召回率权重一样时，选择该指标。



$F_\beta$-Score

当准确率和召回率重要性不一样时，通过$\beta$调节两者的权重。
$$
F_\beta = \frac{(1+\beta^2) \times P \times R}{ \beta^2 \times P + R}
$$
其中，$\beta^2=\frac{R_{weight}}{P_{weight}}$, $R_{weight}+P_{weight}=1$.



Confusion Matrix

![confusion_matrix](https://github.com/bifeng/daily_book_notes/raw/master/resource/confusion_matrix.jpg)



###### Macro/Micro

主要计算多个二分类的混淆矩阵，应用场景包括多次训练/测试、多个训练集的训练/测试、多分类任务的两两类别组合等。

|             | macro                                                        | micro                                                        |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| hypotheses  | each class has equal weight                                  | each instance has equal weight                               |
| calculation | 1.compute metric within each class; 2. average resulting metrics across classes | 1. aggregate outcomes across all classes; 2. compute metric with aggregate outcomes |
| preference  | Smallest classes have most influence                         | Largest classes have most influence                          |

+ If the classes have about the same number of instances, macro- and micro-average will be about the same.

+ If some classes are much larger (more instances) than others, and you want to:

  Weight your metric toward the largest ones, use micro-averaging.

  Weight your metric toward the smallest ones, use macro-averaging.

+ If the micro-average is much lower than the macro-average then examine the larger classes for poor metric performance.

+ If the macro-average is much lower than the micro-average then examine the smaller classes for poor metric performance.

refer: [University of Michigan Python Data Science Course](https://www.coursera.org/learn/python-machine-learning) 



Macro

设有n个混淆矩阵，计算出准确率和召回率的平均值 - 假设每一次的混淆矩阵（训练）是同等权重。

$macro_P = \frac{1}{n} \sum^n_{i=1} P_i $ 

$macro_R = \frac{1}{n} \sum^n_{i=1} R_i $ 

$macro_{F_1} = \frac{2 \times macro_P \times macro_R}{macro_P + macro_R}$



Micro

设有n个混淆矩阵，计算出混淆矩阵对应元素（TP，FP，FN，TN）的平均值 - 每一个样本的权重是一样的。

$micro_P = \frac{\bar{TP}}{\bar{TP}+\bar{FP}}$ 

$micro_R = \frac{\bar{TP}}{\bar{TP}+\bar{FN}}$ 

$micro_{F_1} = \frac{2 \times micro_P \times micro_R}{micro_P + micro_R}$ 



ROC

Receiver operating characteristics (ROC) 曲线描绘在不同的截断点时，(FPR,TPR)的曲线变化。

纵轴：TPR=实际正例分对的概率 = TP/(TP+FN)

横轴：FPR=实际负例分错的概率 = FP/(FP+TN)

判断标准：

1. 一个ROC曲线完全”包住“另一个ROC曲线--->第一个学习器效果更好

2. 两个ROC曲线相交--->利用ROC曲线下的面积（AUC，area under ROC curve，是一个数值）进行比较

Disadvantages:<br>Class imbalances (i.e., differences in prior class probabilities [220]) can cause ROC curves to poorly represent the classifier performance.



AUC

The area under ROC curve (AUC) [31,32] measures the entire area underneath the ROC curve.

Advantages: AUC leverages helpful properties such as increased sensitivity in the analysis of variance (ANOVA) tests, independence from decision threshold, invariance to a priori class probabilities, and indication of how well negative and positive classes are in regarding the decision index [221].

For binary classification tasks, AUC can be formulated as:
$$
AUC =
$$
For multi-class AUC, an average AUC can be defined [222] as follows:
$$
AUC = \frac{2}{|C|(|C|-1)} \sum^{|C|}_{i=1} AUC_i
$$
where C is the number of the classes.



PR Curve

纵轴：Precision

横轴：Recall

当正负样本差距不大的情况下，ROC和PR的趋势是差不多的；当正负类样本差距很大时，ROC的就不能很好的反应分类器的真实性能了，这时候PR将是更好的选择。当FP的数量有比较大的变化时，FP_rate= FP / N 因为N很大，所以FP_rate不会有很大变化，但是PR=TP / TP + FP ,它可以捕获到这个差异，所以效果会更好。

paper: The Relationship Between Precision-Recall and ROC Curves





 ##### 阈值

在分类问题中，涉及阈值选择的问题。

阈值选择方法：

1. 默认0.5作为阈值
2. 交叉验证选择最优阈值



#### 误差分析

分析模型的误差，针对各类误差进行修正。



常见的预测误差及解决方案：

1.  输出各个样本top-5的概率（假设10个意图，则输出该样本预测的前5个概率及其意图）

   检查并修正样本，最终确保top-1即为该样本的意图

2. 训练集未包含该类样本

   新增样本

3. 



###### Tools

Paper: Why Should I Trust You?: Explaining the Predictions of Any Classifier

LIME identifies significant words affecting intent classification confidence scores.







 

