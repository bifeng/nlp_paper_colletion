more:

https://lilianweng.github.io/lil-log/2018/11/30/meta-learning.html

[ICLR 2017 | Highlight 1: Meta- and Few-shot Learning](https://mp.weixin.qq.com/s/PQDOC9e8DBai4bx4PEoIqA) 



Few-shot Learning - State of the Art, Dr. Joseph Shtok Research Staff Member at Computer Vision and Augmented Reality Team IBM Research AI, Haifa Lab, IMVC 2019

Few-shot Learning: A Survey, Yaqing Wang, Quanming Yao, 2019, [arxiv](https://arxiv.org/abs/1904.05046v1) 

refer: 

小样本学习（Few-shot Learning）综述, 耿瑞莹、李永彬、黎槟华, 阿里巴巴智能服务事业部小蜜北京团队 [site](https://mp.weixin.qq.com/s?__biz=MzI0NTE4NjA0OQ==&mid=2658360388&idx=2&sn=cf49a5d9810687eab3f6f7f8341dd6eb) 



### Question

+ The few shot is deal with the balanced dataset, using 5-way or 10-way setting, support set and query set are from the test dataset (But in reality, we don't know the label of support set, so the support set must construct from train data), how to use it in real world application with large numbers of relation types (such as 50-way) ?

  https://github.com/thunlp/FewRel/issues/9
  
+ what they learned ? why it works ?

### Summary

1. For prototypical networks, it produce multiple prototype for each classes.

   a prototypical class is calculate by the average encoder of batch size * K.

2. For train/eval/test, the min number of instance in each classes is K + Q.

1) The train data is totally unrelated the eval or test data (Those labels are never seen in train data). The support set and query set is sampled from each dataset.

2) 

Training Step:
The normal training steps in few shot learning is to select N classes for each batch and K instances for each class in the support set.
(For proto network, it's beneficial to use more classes. so, it maybe more than N classes.)

The classes in the query set come from the N classes in the support set, and the instances is shuffled.

So, the model should learn how to determine the classes of each instances in the query set, this is multi-class classification problem.

(For proto network, it's decide by the distance between the prototypical class of support set and the query set.)

Testing Step:
The normal testing steps in few shot learning is to select N classes for each batch and K instances for each class in the support set.
And the N classes is not used in training step.

3. Current few shot learning is major for balance classes.



### Task/Problem Statement

**Task**: N-way k-shot learning task. i.e. we're given k (e.g. 1 or 5) labeled examples for N classes that we have not previously trained on and asked to classify new instances into the N classes.

（无需重新训练模型，对于少量标注样本的新类别，可以完成新类别的分类）

**Problem Statement**: Using a large annotated offline dataset, perform given task for novel categories, represented by just a few samples each.

![few shot problem statement](https://github.com/bifeng/daily_book_notes/raw/master/resource/problem_statement.png)



**Few-shot classification** is a task in which a classifier must be adapted to accommodate new classes not seen in training, given only a few examples of each of these classes. A naive approach, such as re-training the model on the new data, would severely overfit. 



For train, both the supporting set and the query set should come from the train dataset. The same for the validation and test phase. Note that the train, val and test datasets DO NOT share relations types.

### Challenge

- 





### Motivation

For learn **invariant/general representation** from few dataset, we should bring in any extra supervised information or exploit prior knowledge from other tasks or domain ... 





### Definition

Definition 2.1 (Machine learning). A computer program is said to learn from experience E with respect to some classes of task T and performance measure P if its performance can improve with E on T measured by P.

Definition 2.2. Few-Shot Learning (FSL) is a type of machine learning problems (specified by E, T and P) where E contains little supervised information for the target T .



Task Formulation (few-shot relation classification)

We intend to obtain a function $F: (\cal{R},\cal{S},x) \rightarrow y$. 

$\cal{R}=\{r_1,\dots,r_m\}$ defines the relations that the instances are classified into.<br>$\cal{S} = \{(x^1_1,r_1),(x^2_1,r_1),\dots,(x^{n_1}_1,r_1),\dots,(x^1_m,r_m),(x^2_m,r_m),\dots,(x^{n_m}_m,r_m)\}$ is a support set including $n_i$ instances for each relation $r_i \in \cal{R}$.

For relation classification, a data instance $x^j_i$ is a sentence accompanied with a pair of entities. 

<u>The query data $x$ is an unlabeled instance to classify, and $y \in \cal{R}$ is the prediction of $x$ given by $F$.</u>

For $N$ way $K$ shot learning, $N=m=|\cal{R}|$, $K=n_1=\dots=n_m$. 



### Architecture

形式化来说，few-shot 的训练集中包含了很多的类别，每个类别中有多个样本。在训练阶段，会在训练集中**随机抽取** C 个类别，每个类别 K 个样本（总共 CK 个数据），构建一个 meta-task，作为模型的支撑集（support set）输入；再从这 C 个类中剩余的数据中抽取一批（batch）样本作为模型的预测对象（batch set）。即要求模型从 C*K 个数据中学会如何区分这 C 个类别，这样的任务被称为 C-way K-shot 问题。

训练过程中，每次训练（episode）都会采样得到不同 meta-task，所以总体来看，训练包含了不同的类别组合，这种机制使得模型学会不同 meta-task 中的共性部分，比如如何提取重要特征及比较样本相似等，忘掉 meta-task 中 task 相关部分。通过这种学习机制学到的模型，在面对新的未见过的 meta-task 时，也能较好地进行分类。

（本质上，就是控制训练学习的方式，即训练过程每个epoch的分布）



### Application

+ computer vision applications

  character recognition (benchmarks dataset-Ominiglot), image classification (benchmarks dataset-miniImageNet)

  more computer vision applications can be explored, such as image retrieval [117], object tracking [13], gesture recognition [86], image captioning and visual question answering [26] and video event detection [135].

  For example, how to transfer information from the coarse image classification task of animals to the fine-grained image classification task of dogs. The discrepancy cannot be well handled so far.

+ natural language processing

  examples include few-shot translation [52] and. language modeling [125].

  intent classification.

+ recommendation

  cold-start item recommendation has been considered in [124].

+ medical applications

  few-shot drug discovery is attempted in drug discovery [3].

+ robotics and game playing

  robotics and game playing by reinforcement learning [111] from limited experience in new environment starts to draw attention [28, 32, 77]. Existing application includes one-shot imitation [28], multi-armed bandits [28], visual navigation [28], continuous control in locomotion [32]. Recently, [2, 82] further considers these applications in dynamic environment.



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
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/few_shot_learning_methods_taxonomy.png" width="800" height="500" alt="few_shot_learning_methods_taxonomy"></img>
</div>

#### Data

Use prior knowledge to augment data so as to provide an accurate empirical risk minimizer of smaller variance and to meet the sample complexity S needed by common model and algorithms.

Motivation: Synthesize/Augment more data from the novel classes to facilitate the regular learning

GANs

Low-Shot Learning from Imaginary Data, Wang et.al., 2018

$\triangle - encoder$ Schwartz et.al., NeurIPS 2018

Semantic Feature Augmentation in Few-shot Learning, Chen et.al., 2018

#### Model

Design H based on prior knowledge in experience E to **constrain** the complexity of H and reduce its sample complexity S. (减小函数的假设空间)

##### Memory

Motivation: *use (recurrent) network with external or internal memory*

Networks in networks/ Networks generating networks

Memory Augmented Model, Meta Network, ...

##### Metric

**Metric learning**

Motivation: *Learn a `semantic` embedding space using a distance loss function* 

**Training:** achieve good distributions for offline categories

**Inference:** Nearest Neighbor in the embedding space

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

###### Match Network

attention function:

The authors choose a straightforward softmax over cosine similarities in the embedding space as their attention function *a(x, x_i).* 

embedding functions:

The possibility for the support set and query set embedding functions, *f* and *g*, to be different is left open in order to grant more flexibility to the model. 

They propose that the embedding functions *f(x^)* and *g(x_i)* should take on the more general form *f(x^, S)* and *g(x_i, S)* where *S* is the support set. The reasoning behind this is that if two of the support set items are very close, e.g. we are performing fine-grained classification between dog breeds, we should change the way the samples are embedded to increase the distinguishability of these samples (How to do it?).



###### Prototypical Networks

The key assumption is made is that there exists an embedding in which samples from each class cluster around a single **prototypical representation** which is simply the mean of the individual samples. 

Another contribution of this paper is a persuasive theoretical argument to use <u>euclidean distance</u> over cosine distance in metric learning that also justifies <u>the use of class means</u> as prototypical representations. The key is to recognise that squared euclidean distance (but not cosine distance) is a member of a particular class of distance functions known as **Bregman divergences**. ... 

###### Relation Networks

之前的距离度量方式是强约束，relation networks认为距离的度量也可以学习，从而将距离度量方式转变为软约束。





###### Question

+ why Matching Networks is better than siamese networks?

  siamese networks is not optimal as the initial embedding function is trained to maximise performance on a different task! However, Matching Networks combine both embedding and classification to form an end-to-end **differentiable nearest neighbours****classifier.** ???

+ How to increase the distinguishability of the support set ?

+ 







#### Algorithm

Take advantage of prior knowledge to search for the θ which parameterizes the best h ∈ H. The prior knowledge alters the search by providing good initial point to begin the search, or directly providing the search steps. It skipped the optimization for empirical risk and directly targets at $h^∗$. (提供一个好的搜索起始点或搜索路径)



##### Optimization

Motivation: *optimize the model parameters explicitly for fast learning* (普通的梯度下降方法难以在 few-shot 场景下拟合)



###### Optimization as a model



###### Model-Agnostic Meta-Learning







###### Meta-SGD





###### Latent Embedding Optimization













### Question

- Why always use 5-way 1-shot or 5-way 5-shot in few shot learning ?

- How to training model with less parameter for few shot data ?

- How to training model with more sensitive gradient descent ?

  





