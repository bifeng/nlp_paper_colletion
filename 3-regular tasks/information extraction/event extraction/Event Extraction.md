### Task

事件抽取(event extraction)旨在从不同领 域、语言、体裁、形态的非结构化异构数据类型中出抽取结构化的事件信息。

季姮教授认为事件抽取领域有两个非常有研究价值的方向：

1. 增强质量（enhance quality）主要是通过优化模型和优化数据来提高数据抽取的准确率。在优化模型方面，采用联合抽取实体和关系、模仿学习（imitation learning）等方法，可以达到比pipeline更好的效果。在优化数据方面，结合多媒体数据，帮助发现事件中的共指关系，可以提高抽取的准确率。

2. 增强可移植性（enhance portability）是指提升在原有事件类型中训练的模型应用到新事件中的移植效果。

   传统的事件抽取通常是通过人工选取特征的方式，使用机器学习的分类算法（SVM等），抽取出事件中的触发词（event trigger）、参数（event argument）、角色(event role)等信息。该方法需要大量的人工标注数据以及领域专家的特征设计，对新事件的可移植性较差。

   季姮教授提出了一种可移植的事件抽取框架，该框架使用AMR(abstract Meaning Representations)作为句子语义的表示方式，把句子转化为一个单根无向图，将图的矩阵表示形式输入卷积神经网络（CNN），得到该事件的向量表示形式，最后在已有的目标语义空间中，找到与该向量最相似的类型。该方法可以通过对已有数据的训练，得到事件与目标事件集的映射关系，该映射同样适用于未见过的时间类型，因此具有较好的移植性。



### Challenge

多语言

事件中的暗含关系



### Competition

+ CCKS2020

  

  事件要素抽取 

  

+ CCKS2019

  事件主体抽取

  [面向金融领域的事件主体抽取](https://biendata.com/competition/ccks_2019_4/) 

  <https://github.com/bojone/ee-2019-baseline> [5th](https://github.com/hecongqing/CCKS2019_EventEntityExtraction_Rank5) 

  

+ 



### Scholars

+ 季姮  [heng ji](http://nlp.cs.rpi.edu/hengji.html) 



### Paperlist

+ <http://nlp.cs.rpi.edu/kbp/2019/eventreading.html>
+ 



### Projects

+ Distant Supervision for Event Extraction

  <https://nlp.stanford.edu/projects/dist-sup-event-extraction.shtml>
  
+ Turku Event Extraction System

  <https://github.com/jbjorne/TEES>



### Summary

supervised learning, bootstrapping, distant supervision, Open IE/Zero-shot, Schema/Discovery







