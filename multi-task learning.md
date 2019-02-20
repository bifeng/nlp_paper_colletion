https://github.com/sebastianruder/NLP-progress/blob/master/english/multi-task_learning.md



### Literature review

+ An Overview of Multi-Task Learning in Deep Neural Networks, Sebastian Ruder, 2017 [arxiv](https://arxiv.org/abs/1706.05098) 

  http://ruder.io/multi-task/

+ 

### paper

+ (MT-DNN) Multi-Task Deep Neural Networks for Natural Language Understanding, Xiaodong Liu, Pengcheng He, Weizhu Chen, Jianfeng Gao, 2019 [arxiv](https://arxiv.org/abs/1901.11504) 
+ A Unified Architecture for Natural Language Processing: Deep Neural Networks with Multitask Learning, Ronan Collobert, Jason Weston, 2008 ICML
+ 

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

+ domain adaptation

  MTL will help the model to generalize to new tasks in the future as a hypothesis space that performs well for a sufficiently large number of training tasks will also perform well for learning novel tasks as long as they are from the same environment. (Using two stage training strategy to do domain adaptation like in the MT-DNN model)



### MTL in non-neural models



### MTL in Deep Learning



### Auxiliary tasks



### What auxiliary tasks are helpful?



### Question

+ multi-task learning 如何用于摘要/问答的句子选择和句子排序任务？
+ 



