[Transfer Learning - Machine Learning's Next Frontier](http://ruder.io/transfer-learning/index.html) 

https://en.wikipedia.org/wiki/Domain_adaptation



refer:
[迁移学习简明手册](https://github.com/jindongwang/transferlearning-tutorial) 



### Awesome

+ [awesome-transfer-learning](https://github.com/artix41/awesome-transfer-learning)

+ [awsome-domain-adaptation](https://github.com/zhaoxin94/awsome-domain-adaptation) 

  

### scholars

+ Qiang Yang [site](http://www.cse.ust.hk/~qyang/) 
+ 

### Literature Review

+ A survey on transfer learning [Pan and Yang, 2010]

  :star::star::star::star::star:

### papers

+ Distant domain transfer learning [Tan et al., 2017]
+ Transitive transfer learning [Tan et al., 2015]
+ 



### 基本概念

迁移学习作为机器学习的一个重要分支，侧重于将已经学习过的知识迁移应用于新的问题中。



迁移学习的必要性：

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/transfer_learning_why.png" width="600" height="150" alt="transfer_learning_why"></img>
</div>




迁移学习，是指利用**数据**、**任务**、或**模型**之间的相似性，将在<u>旧领域</u>学习过的模型，应用于<u>新领域</u>的一种学习过程。

迁移学习的形式化：给定一个有标记的源域$\cal{D}_s = \{x_i,y_i\}_{i=1}^{n}​$和一个无标记的目标域$\cal{D}_t = \{x_j,y_j\}_{j=n+1}^{n+m}​$。这两个领域的数据分布$P(x_s)​$和$P(x_t)​$不同，即$P(x_s) \neq P(x_t)​$。迁移学习的目的就是要借助$D_s ​$的知识，来学习目标域$D_t ​$的知识(标签)。



#### 前提条件

数据 - 分布

任务

模型



#### 应用场景

Given source and target domains $\cal{D}_s$ and $\cal{D}_t$ where $\cal{D} = \{\cal{X}, P(x)\}$ and source and target tasks $\cal{T}_s$ and $\cal{T}_t$ where $\cal{T} = \{\cal{Y}, P(y|x) \}$ source and target conditions can vary in four ways, which we will illustrate in the following again using our document classification example:

| scenarios                                                    | example                                                      | methods                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------- |
| $\cal{X_s} \neq \cal{X_t}$  -  feature space                 | e.g. the documents are written in two different languages.   | cross-lingual adaptation, ...           |
| $P(x_s) \neq P(x_t)$  -  marginal probability distribution   | e.g. the documents discuss different topics.                 | domain adaptation, ...                  |
| $\cal{Y_s } \neq \cal{Y_t }$  -  label space                 | e.g. documents need to be assigned different labels in the target task. In practice, this scenario usually occurs with scenario 4, as it is extremely rare for two different tasks to have different label spaces, but exactly the same conditional probability distributions. | domain-invariant representation, ...    |
| $P(y_s|x_s) \neq P(y_t|x_t)$  -  conditional probability distribution | e.g. source and target documents are unbalanced with regard to their classes. | over-sampling, under-sampling, or SMOTE |



#### 核心问题



迁移学习的核心是，找到源领域和目标领域之间的相似性，并加以合理利用。

1）如何寻找相似性？

2）如何度量和利用这种相似性？





#### 负迁移

负迁移指的是，在源域上学习到的知识，对于目标域上的学习产生负面作用。

产生负迁移的原因主要有：
• 数据问题：源域和目标域压根不相似，谈何迁移？
• 方法问题：源域和目标域是相似的，但是，迁移学习方法不够好，没找到可迁移的成分。



### 研究方法

|              | 研究方法 |      |      |      |      |
| ------------ | -------- | ---- | ---- | ---- | ---- |
| 数据         |          |      |      |      |      |
| 特征         |          |      |      |      |      |
| 条件概率分布 |          |      |      |      |      |
|              |          |      |      |      |      |
|              |          |      |      |      |      |



按学习方法的分类形式，最早在迁移学习领域的权威综述文章[Pan and Yang, 2010] 给出定义。它将迁移学习方法分为以下四个大类：

1. 基于样本的迁移学习方法(Instance based Transfer Learning)
2. 基于特征的迁移学习方法(Feature based Transfer Learning)
3. 基于模型的迁移学习方法(Model based Transfer Learning)
4. 基于关系的迁移学习方法(Relation based Transfer Learning)

这是一个很直观的分类方式，按照数据、特征、模型的机器学习逻辑进行区分，再加上不属于这三者中的关系模式。

#### 基于实例的迁移

简单来说就是通过权重重用，对源域和目标域的样例进行迁移。就是说直接对不同的样本赋予不同权重，比如说相似的样本，我就给它高权重，这样我就完成了迁移，非常简单非常非常直接。



这类方法通常假设源域和目标域的概率分布是不同，而条件概率分布相同。

该方法的核心是如何估计样本的权重或提高目标域的实例权重。

通常只在领域间分布差异较小时有效。



#### 基于特征的迁移

就是更进一步对特征进行变换。意思是说，假设源域和目标域的特征原来不在一个空间，或者说它们在原来那个空间上不相似，那我们就想办法把它们变换到一个空间里面，那这些特征不就相似了？这个思路也非常直接。这个方法是用得非常多的，一直在研究，目前是感觉是研究最热的。





这类方法通常假设源域和目标域间有一些交叉的特征（**共享的特征空间**）。

该方法的核心是如何找一个好的特征变换方法或统一特征空间。



#### 基于模型的迁移

就是说构建参数共享的模型。这个主要就是在神经网络里面用的特别多，因为神经网络的结构可以直接进行迁移。比如说神经网络最经典的finetune就是模型参数迁移的很好的体现。



这种迁移方式要求的假设条件是：源域中的数据与目标域中的数据可以共享一些模型的参数（**共享的模型参数**）。



#### 基于关系的迁移

这个方法用的比较少，这个主要就是说挖掘和利用关系进行类比迁移。比如老师上课、学生听课就可以类比为公司开会的场景。这个就是一种关系的迁移。


这类方法通常假设源域和目标域的样本之间存在相似的关系（**共享的样本关系**）。



### 研究分支-领域自适应

领域自适应问题是迁移学习的研究内容之一，它侧重于解决特征空间一致、类别空间一致，仅特征分布不一致的问题。而迁移学习也可以解决上述内容不一致的情况。

领域自适应研究问题解决的就是协方差漂移现象（即数据的边缘概率分布发生变化）。

领域自适应(Domain Adaptation): 给定一个有标记的源域$\cal{D}_s = \{x_i,y_i\}_{i=1}^{n}​$和一个无标记的目标域$\cal{D}_t = \{x_j,y_j\}_{j=n+1}^{n+m}​$，假定它们的特征空间相同，即$\cal{X}_s = \cal{X}_t​$，并且它们的类别空间也相同，即$\cal{Y}_s = \cal{Y}_t​$ 以及条件概率分布也相同，即$\cal{Q}_s(y_s|x_s)  = \cal{Q}_t(y_t|x_t) ​$。但是这两个域的边缘分布不同，即$P(x_s) \neq P(x_t)​$。迁移学习的目标就是，利用有标记的数据$\cal{D}_s ​$去学习一个分类器$f : x_t \rightarrow y_t ​$来预测目标域$\cal{D}_t ​$的标签$y_t \in \cal{Y}_t​$.

#### 数据分布自适应法



#### 特征选择法



#### 子空间学习法



### 研究分支-深度迁移学习

#### 深度网络的可迁移性

康奈尔大学的Jason Yosinski 等人[Yosinski et al., 2014]在ImageNet的1000类上，划分为两个数据集，每份500个类别，分别训练了一个8层的AlexNet网络，并利用finetune方法探索了网络的可迁移性，得到以下结论：

• 神经网络的前3层基本都是general feature，进行迁移的效果会比较好；
• 深度迁移网络中加入fine-tune，效果会提升比较大，可能会比原网络效果还好；
• Fine-tune 可以比较好地克服数据之间的差异性(**分布**)；<br>• 深度迁移网络要比随机初始化权重效果好；
• 网络层数的迁移可以加速网络的学习和优化。

#### finetune



finetune的基本假设是训练数据和测试数据服从相同的数据分布

finetune的核心问题是选择固定哪些层。



#### feature-based



feature-based的核心问题是选择提取哪些层。



#### 深度网络自适应

深度网络自适应的核心在于，找到网络需要进行自适应的层，并且对这些层加上自适应的损失度量。



### 研究分支-深度对抗网络迁移





### Question

+ 迁移学习的前提条件？

+ 迁移学习的方法适用场景？

  

+ 领域自适应的应用场景？

+ 深度迁移学习的前提条件？

  

+ How many sample is enough for transfer learning?

+ 

