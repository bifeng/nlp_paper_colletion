### Question

+ How to prediction relation type for multiple sentence share a pair of entities ? It will output multi-label ?

+ Can apply it on unequal size of sentence sets ? 取众数或中位数 ?

  

### Task

Given a set of sentences $\{x_1, x_2, \dots,x_n\}$ and two corresponding entities, our model measures the probability of each relation $r$.



### Contribution

+ For multiple sentences share a pair entities, use the sentence level attention can utilize all informative sentence that contribute to the this entity relation type.

  (Compare to multi-instance single-label, it assume that only one sentence is active for this entity pair, Hence, it will lose a large amount of rich information containing in those neglected sentences. Use sentence level attention over multiple instances, which can utilize all informative sentences.)

+ It can be used in multiple sentences (sentences bag) relation extraction, and also single sentence relation extraction.





#### The objective function

We define the objective function using cross-entropy <u>at the set level</u> as follows:
$$
J(\theta) = \sum^s_{i=1} \log p(r_i|S_i, \theta)
$$
where $s$ indicates the number of sentence sets and $\theta$ indicates all parameters of our model.

### Architecture

![PCNN_architecture](https://github.com/bifeng/nlp_paper_notes/raw/master/image/PCNN_architecture.png)

其中，输入层的$x_1, \dots, x_n$表示实体对应的$n$个句子，经过中间层CNN编码得到$\rm{x}_1,\dots, \rm{x}_n$各个句子的分布式表示，再经过句子级的注意力权重$\alpha_1, \dots, \alpha_n$，最终获得句子集合的表示$\rm{s}$.

考虑句子集$\{x_1,x_2,\dots,x_n\}$和两个对应的实体，我们的模型主要预测实体关系$r$的概率。

该模型主要分为两个部分：句子编码器，实例的注意力选择

1. 句子编码器

   给定一个句子及相应的两个实体（一对实体关系），利用卷积神经网络构建句子的分布式表示。

![PCNN_encoder](https://github.com/bifeng/nlp_paper_notes/raw/master/image/PCNN_encoder.png)

如上图所示，利用CNN/PCNN将句子"Bill Gates is the founder of Microsoft."转化为分布式表示$\rm{x}$。首先将句子中的每个单词转化为实值特征向量，并和每个单词的位置向量共同作为输入的向量表示；其次，卷积层、最大池化层和非线性转换层用于构建句子的分布式表示$\rm{x}$.

2. 实例的注意力选择

   利用句子级的注意力方法选择那些真正表达对应关系的句子。考虑实体对（head, tail）包含$n$个句子集合$S$，$S=\{x_1,x_2, \dots, x_n\}$.

   为了利用所有句子的信息，首先将集合$S$表示为实值向量$\rm{s}​$：
   $$
   \rm{s} = \sum_{i=1}^{n} \alpha_i x_i
   $$
   其中，$\alpha_{i}$是各个句子向量$\rm{x}_i$的选择性注意力权重。该权重定义如下：
   $$
   \alpha_{i} = \frac{exp(e_i)}{\sum_{k} exp(e_k)}
   $$
   其中，$e_i$为查询函数，该函数可以衡量输入句子$x_i$和预测关系$r​$的匹配程度。我们选择双线性形式定义查询函数：
   $$
   e_i = \rm{x}_i A r
   $$
   其中，$\rm{A}$是加权对角矩阵，$\rm{r}$为查询向量，即实体关系$r$的表示。

    

### Experimental Setting

The NYT dataset.

We use the word2vec tool to train the word embeddings on NYT corpus. We keep the words which appear more than 100 times in the corpus as vocabulary. Besides, we concatenate the words of an entity when it has multiple words.





