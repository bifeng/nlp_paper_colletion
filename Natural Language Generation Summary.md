refer: [大众点评信息流基于文本生成的创意优化实践](https://mp.weixin.qq.com/s/HWqFpDhvhGrJtNTSLsO3Eg)



### Application

**Text2Text:** 

machine translation

semantic parsing (AMR parsing/SQL parsing)

code generation

summarization generation

keyphrase Generation

paraphrase generation

story generation

text generation

chatbot

commonsense Inference

**Data2Text**

**Image2Text**

### Challenges

#### The "UNK" problem

Specific entities, low frequency words cannot be generated

由于decoder部分产生词汇的来源是通过训练语料得到的词汇表，但是在实际测试过程中，测试集中的词不一定完全在训练集中出现，也就超出了decoder的预测范围。这种现象通常称为OOV问题（Out of Vocabulary）。

#### The repetition problem

由于decoder过度依赖其输入，也就是先前的总结词，会导致一个词的出现触发无尽的重复。



#### The representation problem

只有表示并学习到原文的语义意图才能更好的控制标题生成，这个本身在NLU就是难点，在生成式中就更为突出。



#### The constrain problem

1. Constrain the output space to selections that matter
   Inference: Avoid invalid parses
   Training: Do not waste modeling power in distinguishing invalid parses from valid ones!

2. 生成式本质作为语言模型无法在句子层面对业务目标直接做优化，即根据不同的场景和目标能控制它说什么、怎么说。

   生成式模型其本质是一个Language Model，它的训练目标是最小化Word级别的交叉熵Loss，而最终我们的需要评价的其实是句子级别的业务目标（如标题的点击率），这就导致了训练目标和业务指标不一致。



控制，在解码端表现为两类，一类我们称之为Hard Constrained（强控制），即在数据端给定（或没有给定）的信息，一定要在解码端进行（或不进行）相应描述，这个适用于地域类目等不能出错的信息。比如这家商户在上海，生成时不能出现除上海以外的地域信息，否则容易造成歧义。另一类称之为Soft Constrained（弱控制），不同于NMT问题，在文案生成上即便是完全相同的输入，不同的输出都是允许的，比如同一商户，最终的文案可以选择不同的卖点去描述不同的内容。



解决这个问题有三个可行的方向：

第一是在Context中显式地加入需要控制的Label（如业务目标的Label），让模型学习到两者的差异；第二是在Decoder的Beam Search计算概率的同时，添加一个打分控制函数；第三则是在训练的Decoder中，建立一个全局损失函数参与训练，类似于NMT中增加的Coverage Loss。



### Architecture

Seq2Seq + Attention



Representation:
**Contextual Embedding**

**Tree-Based Embedding** - 通过树形结构进行建模，包括很多方式如传统的语法树，在语法结构上做Tree Base的RNN，用根结点的Embedding即可作为上下文的表征。Tree本身可以通过构造的方式，也可以通过学习的方式（比如强化学习）来进行构建。最终Task效果，既和树的结构（包括深度）有关，也受“表示”学习的能力影响，调优难度比较大。



### Methods

#### Token-based Decoding



#### Grammar-based Decoding

+ Lexically Constrained Decoding for Sequence Generation Using Grid Beam Search, Chris Hokamp, Qun Liu, ACL 2017 [arxiv](https://arxiv.org/abs/1704.07138) | [code](https://github.com/chrishokamp/constrained_decoding) 
+ 



#### Extractive and Generative Combined

Copy机制（使用Copy机制的原始目的，是为了解决生成式的OOV（超出词表范围）问题）

+ A Retrieve-and-Edit Framework for Predicting Structured Outputs, Tatsunori B. Hashimoto, Kelvin Guu, Yonatan Oren, Percy Liang, NeurIPS 2018 [arxiv](https://arxiv.org/abs/1812.01194) | [code](https://worksheets.codalab.org/worksheets/0x1ad3f387005c492ea913cf0f20c9bb89/#)  
+ 

