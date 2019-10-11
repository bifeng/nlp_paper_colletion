### Question

+ 如何统一建模常见样本、长尾样本？

  

+ 如何预测一个样本是否长尾样本？

  solution:

  1. 训练一个长尾样本分类器，即新增一个类别，该类别属于长尾样本

+ 


### Refer
https://bair.berkeley.edu/blog/2019/05/13/oltr/
https://arxiv.org/pdf/1904.05160.pdf
https://github.com/zhmiao/OpenLongTailRecognition-OLTR
https://liuziwei7.github.io/projects/LongTail.html


### Problem Definition
一个有用的系统应该能够区分很少几类常见的物体、同时也能区分很多类不常见的实例，从很少量的已知样本归纳出某一类的通用概念，从未见过的分类中识别出实例的新颖性。

为了反映真实世界的状况，研究人员提出了开放长尾识别问题（Open Long-Tailed Recognition，OLTR）,从长尾和开放分布的数据中学习，并在包含头部、尾部和开发分类的平衡测试集中评测分类精度。

### Relate Task
非平衡分类问题(imbalanced classification)

少样本学习(few-shot learning)

开放集识别(open-set recognition)问题

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/open_long_tailed_recognition.jpg" width="800" height="300" alt="open_long_tailed_recognition"></img>
</div>

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/OLTR.jpg" width="800" height="300" alt="OLTR"></img>
</div>




### Summary

1. 先验知识

   带有大量先验知识的预训练模型，如Bert等

2. 外部知识

   知识图谱

   1）直接编码特征

   2）扩充训练数据（伪标签上训练模型，真实标签上fine-tuning模型）

   weakly supervision、distant supervision等

   如 - Matching the Blanks: Distributional Similarity for Relation Learning、Early Discovery of Emerging Entities in Microblogs...











