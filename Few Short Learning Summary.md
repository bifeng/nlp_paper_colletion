more:

https://lilianweng.github.io/lil-log/2018/11/30/meta-learning.html

[ICLR 2017 | Highlight 1: Meta- and Few-shot Learning](https://mp.weixin.qq.com/s/PQDOC9e8DBai4bx4PEoIqA)

Few-shot Learning: A Survey, Yaqing Wang, Quanming Yao, 2019, [arxiv](https://arxiv.org/abs/1904.05046v1) 

refer: 

小样本学习（Few-shot Learning）综述, 耿瑞莹、李永彬、黎槟华, 阿里巴巴智能服务事业部小蜜北京团队





### Definition

Definition 2.1 (Machine learning). A computer program is said to learn from experience E with respect to some classes of task T and performance measure P if its performance can improve with E on T measured by P.

Definition 2.2. Few-Shot Learning (FSL) is a type of machine learning problems (specified by E, T and P) where E contains little supervised information for the target T .



### Motivation

For learn **invariant/general representation** from few dataset, we should bring in any extra supervised information or exploit prior knowledge from other tasks or domain ... 



### Relevant Learning Problems

Few-shot learning can be supervised learning, semi-supervised learning and reinforcement learning, depending on what kind of data is available apart from the little supervised information.

+ Semi-supervised learning

  Semi-supervised [145] learning learns the optimal hypothesis $o^∗$ from input x to output y by experience E consisting of both labeled and unlabeled examples.

  Special Case:

  Positive-unlabeled learning [67] where only positive and unlabeled samples are given. The unlabeled samples can be either positive or negative.

  Active learning [102] selects informative unlabeled data to query an oracle for output y. This is usually used for applications where annotation is costly, such as pedestrian detection.

+ Transfer learning

  Transfer learning [85] transfers knowledges learned from source domain and source task where sufficient training data is available, to target domain and target task where training data is limited.

  Types:

  Domain adaptation [10] where the tasks are the same but the domain is different. For example, the task is sentiment analysis, while the source domain data is about customer comments for movies while the target domain data is about customer comments for daily goods.

  Zero-shot learning [64] learning directly uses prior knowledge from other data sources to construct hypothesis h. It recognizes new class with <u>no supervised training examples</u> by linking them to existing classes that one has already
  learned. It is suitable for situations where supervised examples are extremely difficult or expensive to get, such as neural activity encoding.

  Few-shot learning manages to learn from <u>limited training examples</u> with the help of prior knowledge.

  Both FSL and zero-shot learning are extreme cases in transfer learning, as they need to <u>transfer prior knowledge learned from other tasks or domain</u> [38]. However, FSL and zero-shot learning learns for new class using different strategies.

+ Meta-learning

  Meta-learning [100] or learning-to-learn [47] that improves performance P on task T by data set of the task T and the meta knowledge extracted across tasks by a meta-learner. Here, learning occurs at two levels: meta learner gradually learns generic information (meta knowledge) across tasks, and learner rapidly generalizes meta-learner for new task T using task-specific information. It can be used for scenarios where meta knowledge is useful, such as learning optimization algorithms [4, 66], reinforcement learning [32] and FSL problems [98, 125].

### Core Issues

The empirical risk minimizer is no longer reliable (not good nor stable), this is the core issue underneath FSL. Therefore, FSL is much harder than common machine learning settings.



### Methods

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/few_shot_learning_methods.png" width="800" height="300" alt="few_shot_learning_methods"></img>
</div>

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/few_shot_learning_methods_taxonomy.png" width="800" height="300" alt="few_shot_learning_methods_taxonomy"></img>
</div>

#### Data

Use prior knowledge to augment data so as to provide an accurate empirical risk minimizer of smaller variance and to meet the sample complexity S needed by common model and algorithms.

#### Model

Design H based on prior knowledge in experience E to **constrain** the complexity of H and reduce its sample complexity S. (减小函数的假设空间)

##### Memory

Motivation: *use (recurrent) network with external or internal memory*

Memory Augmented Model, Meta Network, ...

##### Metric

Motivation: *learn an efficient distance metric* 

Siamese Network, Match Network, Prototype Network, Relation Network, Induction Network

###### Architecture

| Model                                     | Encoder | Induction       | Relation            |
| ----------------------------------------- | ------- | --------------- | ------------------- |
| Siamese Network [Koch et al., 2015]       | Bi-LSTM | None            | Absolute Difference |
| Match Network [Vinyals et al., 2016]      | Bi-LSTM | None            | Cosine Distance     |
| Prototypical Network [Snell et al., 2017] | Bi-LSTM | Average         | Euclidean Distance  |
| Relation Network [Yang et al., 2018]      | Bi-LSTM | Sum             | Neural Network      |
| Induction Network [Geng et al., 2019]     | Bi-LSTM | Dynamic Routing | Neural Tensor layer |
|                                           |         |                 |                     |
|                                           |         |                 |                     |

Encoder 模块用于获取每个样本的语义表示，可以使用典型的 CNN、LSTM、Transformer 等结构.

Induction 模块用于从支撑集的样本语义中归纳出类别特征.

Relation 模块用于度量 query 和类别之间的语义关系，进而完成分类。

#### Algorithm

Take advantage of prior knowledge to search for the θ which parameterizes the best h ∈ H. The prior knowledge alters the search by providing good initial point to begin the search, or directly providing the search steps. It skipped the optimization for empirical risk and directly targets at $h^∗$. (提供一个好的搜索起始点或搜索路径)



##### Optimization

Motivation: *optimize the model parameters explicitly for fast learning* (普通的梯度下降方法难以在 few-shot 场景下拟合)

Optimization as a model



### Challenge

+ How to construct the training set with support set ?
+ 







### Question

- How to select a good support set (支撑集) ?

- How to training model with less parameter for few shot data ?

- How to training model with more sensitive gradient descent ?

  





