

### innovations

multi-task learning - learning representations universal across tasks.

language model pre-training - learning universal language representations



### Architect

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/MT_DNN_architect.png" width="800" height="600" alt="MT_DNN_architect"></img>
</div>




task-specifics layers

four types of NLU tasks: 

+ single-sentence **classification**

  

+ pairwise text classification (**inference**)

  

  What's stochastic answer network (SAN)?

  SAN, a state-of-the-art neural NLI model. Rather than directly predicting the entailment given the input, it uses multi-step reasoning which maintains a state and iteratively refines its predictions.

  

+ text similarity scoring (**regression**)

  

+ relevance **ranking**

  QNLI is a version of Stanford Question Answering Dataset. The task involves assessing whether a sentence contains the correct answer to a given query.

  In GLUE, QNLI is defined as a binary classification task. We formulate it as a pairwise ranking task, where the model is expected to rank the candidate that contains the correct answer higher than the candidate that does not. We will show that this formulation leads to a significant improvement in accuracy over binary classification.

  

The firs two classification tasks share the same objective which is cross entropy loss, the regression task use the mean squared error as the objective, the ranking task follows the pairwise learning-to-rank paradigm.

shared layers

+ Lexicon encoder

  word, segment, positional embedding

+ Transformer encoder

  a multilayer bidirectional Transformer encoder

#### pre-training

The parameters of the lexicon encoder and Transformer encoder are learned using two unsupervised prediction tasks: masked language modeling and next sentence prediction.(In this study we use the pre-trained $BERT_{LARGE}$ models released by the authors.)

#### multi-task fine-tuning

MT-DNN uses MTL in the fine-tuning stage with multiple task-specific layers in its model architecture.

MTL is particularly useful for the tasks with little in-domain training data.

### domain adaptation

1. fine-tune the MT-DNN model on eight GLUE tasks, excluding WNLI;
2. create for each new task (SNLI or SciTail) a task-specific model, by adapting the trained MT-DNN using task-specific training data;
3. evaluate the models using task-specific test data.



### summary

+ MT-DNN也验证了Bert两阶段模型第二个阶段-fine-tuning（**多任务**）是非常有效的。
+ 



### Question

+ MTL仅仅利用三个目标函数（分类、回归、排序）结合十多个分布完全不同的数据集进行训练，就可以实现每个数据集的精度提升以及领域自适应！为什么？

  

+ Why select these four type NLU tasks?

+ 

+ Which layer is the task specific representation in domain adaptation?

+ 





