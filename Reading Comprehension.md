[Must-read papers on Machine Reading Comprehension](https://github.com/thunlp/RCPapers)



### Challenge

+ when to give no answer?

  SQuAD2.0 tests the ability of a system to not only answer reading comprehension questions, but also abstain when presented with a question that cannot be answered based on the provided paragraph.

  目前主流的模型采用的是“多任务”的思想，即机器需要同时完成两件事：

  1）预测一个问题是否可答

  2）预测该问题在篇章中的答案

  模型需要从训练样例中学习到哪些问题是可以回答，哪些问题是不能回答的（在训练样本中有对应的标记），对于可回答的问题同时要学习如何判断篇章的起止位置从而抽取出对应的答案。在预测时，需要注意的是“可答”和“不可答”问题之间是需要有一个界线来划分。所以，如何权衡这两类回答的比例也是一个很难的问题。绝大多数模型目前采用 **手工阈值** 的方法来决定这个界限，但这样的方法 **普适性较差**，应进一步寻求一个 **自动阈值**的方法来平衡这两类问题的答案输出。

+ 



### STOA

<https://paperswithcode.com/task/machine-reading-comprehension>



### Dataset

+ SQuAD

  https://rajpurkar.github.io/SQuAD-explorer/

  Know What You Don't Know: Unanswerable Questions for SQuAD [arxiv](https://arxiv.org/abs/1806.03822) 

### Tools

+ jack

  Jack the Reader

  <https://github.com/uclmr/jack>



### Literature Review

- Neural Reading Comprehension and Beyond, Danqi Chen, 2018 [code](https://github.com/danqi/thesis) | [zh](<https://chendq-thesis-zh.readthedocs.io/en/latest/>) 
  - [x] Neural Reading Comprehension 

### Paper

- BERT + DAE + AoA

  **DAE（DA Enhanced）**，这里的 DA 有两层含义，一个是数据增强（Data Augmentation），另一个是领域自适应（Domain Adaptation）。

  **Attention-over-Attention**

- Learning to Ask Unanswerable Questions for Machine Reading Comprehension, Haichao Zhu, Li Dong, Furu Wei, Wenhui Wang, Bing Qin, **Ting Liu**, ACL 2019, [arxiv](<https://arxiv.org/abs/1906.06045>) 

  >We propose a data augmentation technique by automatically generating relevant unanswerable questions according to an answerable question paired with its corresponding paragraph that contains the answer.
  >
  >
  >
  >We train question answering models with augmentation data in two separate phases. 
  >
  >In the first phase, we train the models by combining the augmentation data and all 86, 821 SQuAD 2.0 answerable examples. 
  >
  >Subsequently, we use the original SQuAD 2.0 training data alone to further fine-tune model parameters.

  

- Adversarial Examples for Evaluating Reading Comprehension Systems, Robin Jia, Percy Liang, EMNLP 2017 - Outstanding Paper Award. [arxiv](https://arxiv.org/abs/1707.07328) | [code](https://github.com/robinjia/adversarial-squad) | [Robin Jia](http://stanford.edu/~robinjia/) 

  - [x] Adversarial Learning

- Attention-over-Attention Neural Networks for Reading Comprehension, Yiming Cui, Zhipeng Chen, Si Wei, Shijin Wang, Ting Liu, Guoping Hu, ACL 2017 [arxiv](https://arxiv.org/abs/1607.04423) 

  https://stanfordnlp.github.io/coqa/

  https://rajpurkar.github.io/SQuAD-explorer/

- Machine Comprehension Using Match-LSTM and Answer Pointer, Shuohang Wang, Jing Jiang, 2016, [arxiv](https://arxiv.org/abs/1608.07905) | [code](https://github.com/shuohangwang/SeqMatchSeq)  

- Teaching Machines to Read and Comprehend, Karl Moritz Hermann, Tomáš Kočiský, Edward Grefenstette, Lasse Espeholt, Will Kay, Mustafa Suleyman, Phil Blunsom, NIPS 2015 [nips](http://papers.nips.cc/paper/5945-teaching-machines-to-read-and-comprehend) 

  - [x] data scarcity

