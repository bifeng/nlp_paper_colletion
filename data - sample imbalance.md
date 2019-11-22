<http://glemaitre.github.io/imbalanced-learn/index.html>



refer:<br>[样本生而不等——聊聊那些对训练数据加权的方法](https://zhuanlan.zhihu.com/p/53545036)<br>[如何解决数据不平衡问题？](https://mp.weixin.qq.com/s/orf_UaDFCKIaYjslbItcfQ) - 目标检测中的不平衡问题的进展

# methods

## reweight

### reweight by training loss

根据训练数据本身分布的假设不同，分为Hard Negative (Example) Mining和Curriculum/Self-Paced Learning两种方法，前者认为边界上hard example的分布是正确的，后者则认为可能包含outlier example，不必严格要求学习到，否则导致模型过于复杂、降低泛化性能。

#### Hard Negative (Example) Mining

如果一个样本训练得不够好，也就是loss高的话，那么说明现在的模型没有很好fit到这样的数据，所以应该对这样的样本给予更高的权重。这一类工作就对应到经典的Hard Negative (Example) Mining，近期的工作如Focal Loss也是这个思想。

#### Curriculum/Self-Paced Learning

学习需要循序渐进，应该先学习简单的样本，逐渐加大难度，最终如果仍然后Loss很大的样本，那么认为这些样本可能是Outlier，强行fit这些样本反而可能会使泛化性能下降。这一类中对应的是Curriculum Learning或者Self-Paced Learning类型的工作。

- Bengio, Yoshua, et al. "Curriculum learning". In ICML, 2009.
- Kumar M. Pawan, Packer Benjamin, and Koller Daphne "Self-paced learning for latent variable models". In NIPS, 2010.
- ...

### reweight by training and validation loss

引入一个新的无偏验证集来提供更多的信息。然而这个验证集在实际应用中是否会引入一些overfitting的风险其实还有待更多应用的验证。（如何保证验证集是无偏的？）

将问题转化为：如何对每个样本加权，使得验证集上的loss下降

1. influence function

   使用了一个统计学中经典工具Influence Function。基本思路是考虑如果我们增加eps某一个样本的weight，会对model的参数有怎样的影响。

   Koh, Pang Wei, and Percy Liang. "Understanding black-box predictions via influence functions." *ICML* (2017). Best Paper [arxiv](https://arxiv.org/abs/1703.04730) | [code](https://github.com/kohpangwei/influence-release) 

2. meta-learning

   利用了Deep Learning中已有操作，使用meta-learning的办法去学习样本的weight。

   **当一个样本和validation set中的样本feature接近，且gradient方向接近的时候，那么我们会增加这个样本的weight。**换句话说，如果一个样本和validation set中的样本接近，且训练的目标一致，那么我们就应该更好地fit这个样本，因为它能直接帮助validation set降低loss。

   Ren, Mengye, et al. "Learning to reweight examples for robust deep learning." *ICML*(2018).

## loss function design

### GHM_Detection
论文：https://arvix.org/pdf/1811.05181.pdf
github：https://github.com/libuyu/GHM_Detection

本文是香港中文大学发表于 AAAI 2019 的工作，**文章从梯度的角度解决样本中常见的正负样本不均衡的问题。**从梯度的角度给计算 loss 的样本加权，相比与 OHEM 的硬截断，这种思路和 Focal Loss 一样属于软截断。

**文章设计的思路不仅可以用于分类 loss 改进，对回归 loss 也很容易进行嵌入。****不需要考虑 Focal Loss 的超参设计问题，同时文章提出的方法效果比 Focal Loss 更好。**创新点相当于 FL 的下一步方案，给出了解决 class-imbalance 的另一种思路，开了一条路，估计下一步会有很多这方面的 paper 出现。

### Focal Loss for Dense Object Detection

论文：

Focal Loss：https://arxiv.org/abs/1708.02002

RetinaNet：https://github.com/unsky/RetinaNet

github：https://github.com/unsky/focal-loss

本文通过重塑标准交叉熵损失来解决这一类不平衡问题。他们的想法是降低简单的负面样本所占的权重，所以他们提出的焦点损失（Focal Loss）方法将训练集中在一系列难点上，并且防止了大量的简单负面例子在训练过程中阻碍探测器学习。如上图，参数 γ 的值选择得越大，模型就会对已经得到了很好的分类的样本忽略得越多，越专注于难的样本的学习。这样的机制就让他们的检测器在密集对象检测这样的真实正面样本比例很低的情况下取得了很高的准确率。对于应对样本不平衡问题的关键方法“焦距损失”，作者们在论文中还提出了两种不同的表现形式，都起到了很好的效果.

### Dice Loss for Data-imbalanced NLP Tasks

<https://arxiv.org/pdf/1911.02855.pdf>

### Class-Balanced Loss Based on Effective Number of Samples

Class-Balanced Loss Based on Effective Number of Samples. Yin Cui, Menglin Jia, Tsung-Yi Lin, Yang Song, Serge Belongie CVPR 2019 [arxiv](<https://arxiv.org/abs/1901.05555>) [code](https://github.com/richardaecn/class-balanced-loss) 

### Learning Imbalanced Datasets with Label-Distribution-Aware Margin Loss

Learning Imbalanced Datasets with Label-Distribution-Aware Margin Loss. Kaidi Cao, Colin Wei, Adrien Gaidon, Nikos Arechiga, Tengyu Ma NeurIPS 2019 [arxiv](<https://arxiv.org/abs/1906.07413>) 





## other

Fan, Yang, et al. "Learning What Data to Learn." *arXiv preprint arXiv:1702.08635* (2017).







