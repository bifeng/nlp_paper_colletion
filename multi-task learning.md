refer:<br>An Overview of Multi-Task Learning in Deep Neural Networks, Sebastian Ruder, 2017 [arxiv](https://arxiv.org/abs/1706.05098) | [site](http://ruder.io/multi-task/) 



https://en.wikipedia.org/wiki/Multi-task_learning

https://github.com/sebastianruder/NLP-progress/blob/master/english/multi-task_learning.md



### Literature review

+ R. Caruana. Multitask Learning. Machine Learning, 28(1):41-75, 1997.
+ An Overview of Multi-Task Learning in Deep Neural Networks, Sebastian Ruder, [arxiv](https://arxiv.org/abs/1706.05098) :star::star::star:

### paper

+ **Sebastian Ruder**, Joachim Bingel, Isabelle Augenstein, Anders Søgaard (2019). [Latent Multi-task Architecture Learning](https://arxiv.org/abs/1705.08142). In *Proceedings of AAAI 2019*, Honolulu, Hawaii. [Slides](https://drive.google.com/file/d/1To0SNI9PJS0Roqt0vJyHnCLyKqukwnxE/view?usp=sharing), [poster](https://drive.google.com/file/d/1KmgFeKva0roXaBavz2dpUZ6t6wydRVDh/view?usp=sharing), [code](https://github.com/sebastianruder/sluice-networks) 
+ (MT-DNN) Multi-Task Deep Neural Networks for Natural Language Understanding, Xiaodong Liu, Pengcheng He, Weizhu Chen, Jianfeng Gao, 2019 [arxiv](https://arxiv.org/abs/1901.11504) 
+ A Unified Architecture for Natural Language Processing: Deep Neural Networks with Multitask Learning, Ronan Collobert, Jason Weston, 2008 ICML
+ 

loss function

+ Multi-Task Learning Using Uncertainty to Weigh Losses for Scene Geometry and Semantics, Alex Kendall, Yarin Gal, Roberto Cipolla, CVPR 2018 [arxiv](https://arxiv.org/abs/1705.07115) | [code](https://github.com/yaringal/multi-task-learning-example) 

### tools

- [decaNLP](https://github.com/salesforce/decaNLP) 
- 



### Multi-Task Learning

==Notes==: The NLP progress largely contribute by amounts of data, which benefits in two forms. <br>First, limited of labeled data for supervised learning, but mainly in written (standard) language (not spoken language), can not transfer to other scenes.<br>Second, amounts of unlabeled data for word embedding used as pre-training models, such as word2vec, fasttext, elmo, bert and so on, transfer the general knowledge to other scenes. <br>But, even for that, the progress in vertical field still difficult to move forward.  

MTL comes in many guises: joint learning, learning to learn, and learning with auxiliary tasks are only some names that have been used to refer to it. 

MTL improves generalization by leveraging the domain-specific information contained in the training signals of related tasks.

### motivation

we can motivate multi-task learning from a machine learning point of view: We can view multi-task learning as a form of inductive transfer. Inductive transfer can help improve a model by introducing an inductive bias, which causes a model to prefer some hypotheses over others. For instance, a common form of inductive bias is ℓ1 regularization, which leads to a preference for sparse solutions. In the case of MTL, the inductive bias is provided by the auxiliary tasks, which cause the model to prefer hypotheses that explain more than one task. As we will see shortly, this generally leads to solutions that generalize better.

### Why does MTL work?

+ Implicit data augmentation

  If a task is very <u>noisy</u> or <u>data is limited</u> and high-dimensional, it can be difficult for a model to differentiate between relevant and irrelevant features. MTL effectively increases the sample size and reduce the noise.

+ regularization

  MTL acts as a regularizer by introducing an inductive bias. As such, it reduces the risk of overfitting as well as the Rademacher complexity of the model, i.e. its ability to fit random noise.

  




### MTL in non-neural models



### MTL in Deep Learning





### Application Scenario/Auxiliary tasks

relationship of tasks:

- sequence

  we only care about one main task.

  [Caruana, 1998] uses tasks that predict different characteristics of the road as auxiliary tasks for predicting the steering direction in a self-driving car;

  [Liu et al., 2015] jointly learn query classification and web search;

  

  we predicting the features as an auxiliary task (hints).

  [Yu and Jiang, 2016] who predict whether an input sentence contains a positive or negative sentiment word as auxiliary tasks for sentiment analysis.

  [Cheng et al., 2015] who predict whether a name is present in a sentence as auxiliary task for name error detection.

  

  we can use the present to predict the future, or using the future to predict the present.

  In some situations, some features only become available after the predictions are supposed to be made. But it can be used as an auxiliary task to impart additional knowledge to the model during training.

  

  

- parallel

  similarity of task

  we are interested in obtaining predictions for multiple tasks at once.

  

  Using less quantized auxiliary tasks, as they might be learned more easily due to their objective being smoother.

- hierarchy

  

  

- representation learning for domain adaptation

  MTL will help the model to generalize to new tasks in the future as a hypothesis space that performs well for a sufficiently large number of training tasks will also perform well for learning novel tasks as long as they are from the same environment. (Using two stage training strategy to do domain adaptation like in the MT-DNN model)



#### What  scenario/auxiliary tasks are helpful?

our understanding of tasks – their similarity, relationship, hierarchy, and benefit for MTL – is still limited



### Question

+ multi-task learning 如何用于摘要/问答的句子选择和句子排序任务？
+ 



