refer:<br>[样本生而不等——聊聊那些对训练数据加权的方法](https://zhuanlan.zhihu.com/p/53545036)



## methods

### reweight by training loss

根据训练数据本身分布的假设不同，分为Hard Negative (Example) Mining和Curriculum/Self-Paced Learning两种方法，前者认为边界上hard example的分布是正确的，后者则认为可能包含outlier example，不必严格要求学习到，否则导致模型过于复杂、降低泛化性能。

#### Hard Negative (Example) Mining

如果一个样本训练得不够好，也就是loss高的话，那么说明现在的模型没有很好fit到这样的数据，所以应该对这样的样本给予更高的权重。这一类工作就对应到经典的Hard Negative (Example) Mining，近期的工作如Focal Loss也是这个思想。

#### Curriculum/Self-Paced Learning

学习需要循序渐进，应该先学习简单的样本，逐渐加大难度，最终如果仍然后Loss很大的样本，那么认为这些样本可能是Outlier，强行fit这些样本反而可能会使泛化性能下降。这一类中对应的是Curriculum Learning或者Self-Paced Learning类型的工作。



### reweight by training and validation loss

引入一个新的无偏验证集来提供更多的信息。然而这个验证集在实际应用中是否会引入一些overfitting的风险其实还有待更多应用的验证。（如何保证验证集是无偏的？）

将问题转化为：如何对每个样本加权，使得验证集上的loss下降

1. influence function

   使用了一个统计学中经典工具Influence Function。基本思路是考虑如果我们增加eps某一个样本的weight，会对model的参数有怎样的影响。

   Koh, Pang Wei, and Percy Liang. "Understanding black-box predictions via influence functions." *ICML* (2017). Best Paper [arxiv](https://arxiv.org/abs/1703.04730) 

2. meta-learning

   利用了Deep Learning中已有操作，使用meta-learning的办法去学习样本的weight。

   **当一个样本和validation set中的样本feature接近，且gradient方向接近的时候，那么我们会增加这个样本的weight。**换句话说，如果一个样本和validation set中的样本接近，且训练的目标一致，那么我们就应该更好地fit这个样本，因为它能直接帮助validation set降低loss。

   Ren, Mengye, et al. "Learning to reweight examples for robust deep learning." *ICML*(2018).




### other

Fan, Yang, et al. "Learning What Data to Learn." *arXiv preprint arXiv:1702.08635* (2017).







