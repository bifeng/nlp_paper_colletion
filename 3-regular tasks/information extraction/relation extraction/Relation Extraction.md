#### Contents

1. [Application](#Application)
2. [Task](#Task)
3. [Related-tasks](#Related-tasks)
4. [Literature-Review](#Literature-Review)
5. [Competition](#Competition)
6. [STOA](#STOA)
7. [Dataset](#Dataset)
8. [Tools](#Tools)
9. [Paperlist](#Paperlist)
10. [Blogs](#Blogs)
11. [Paper](#Paper)

---

#### Application





---

#### Task

Extracted relationships usually occur between two or more entities of a certain type (e.g. Person, Organisation, Location) and fall into a number of semantic categories (e.g. married to, employed by, lives in).



---

#### Related-tasks

- attributes extraction

  OpenTag: Open Attribute Value Extraction from Product Profiles, Guineng Zheng, Subhabrata Mukherjee, Xin Luna Dong, Feifei Li, KDD 2018, [arxiv](https://arxiv.org/abs/1806.01264v1) (BiLSTM-CRF with Attention)

  Unsupervised Extraction of Attributes and Their Values from Product Description

  http://www.stokastik.in/attribute-extraction-from-e-commerce-product-description/

  http://www.stokastik.in/bilstm-crf-sequence-tagging-for-e-commerce-attribute-extraction/



  Scaling Up Open Tagging from Tens to Thousands: Comprehension Empowered Attribute Value Extraction from Product Title. ACL2019

  A Multi-task Learning Approach for Improving Product Title Compression with User Search Log Data. AAAI2018

  Multi-Source Pointer Network for Product Title Summarization. CIKM2018

- open information extraction

---

#### Literature-Review

+ 人工智能的知识获取：实体关系抽取的现状与未来 - 刘知远老师团队 
+ 林衍凯、刘知远（清华大学）, 基于深度学习的关系抽取 2016 [PDF](http://qngw2014.bj.bcebos.com/zhuankan/3/20160912_003%E5%9F%BA%E4%BA%8E%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0%E7%9A%84%E5%85%B3%E7%B3%BB%E6%8A%BD%E5%8F%96%E6%8A%80%E6%9C%AF%E8%BF%9B%E5%B1%95_%E5%88%98%E7%9F%A5%E8%BF%9C_%E7%86%8A%E5%BE%B7%E6%84%8F.pdf) [blog](<http://www.cipsc.org.cn/qngw/?p=890>) 
+ A Review of Relation Extraction, Nguyen Bach, Sameer Badaskar, 2007 [paper](http://www.cs.cmu.edu/~nbach/papers/A-survey-on-Relation-Extraction.pdf) | [slide](http://www.cs.cmu.edu/~nbach/papers/A-survey-on-Relation-Extraction-Slides.pdf) :star::star::star:

---

#### Competition

+ 2020语言与智能技术竞赛 百度 关系抽取任务 [site](https://aistudio.baidu.com/aistudio/competition/detail/31?isFromCcf=true) 

  [baseline](https://kexue.fm/archives/7321) [15th](https://github.com/aker218/Baidu-2020-Language-and-Intelligent-Technology-Competition-Relation-Extraction-rank15) 
  
  2020语言与智能技术竞赛冠军团队分享
  http://mbd.baidu.com/webpage?type=live&action=liveshow&source=h5pre&room_id=4008201814
  
+ 2019语言与智能技术竞赛 百度 三元组抽取比赛 [site](<https://ai.baidu.com/broad/leaderboard>) 

  [baseline](<https://github.com/baidu/information-extraction>) [1th](Joint entity recognition and relation extraction as a multi-head selection problem) [pdf]([https://github.com/yuanxiaosc/Entity-Relation-Extraction/blob/master/Schema%E7%BA%A6%E6%9D%9F%E7%9A%84%E7%9F%A5%E8%AF%86%E6%8A%BD%E5%8F%96%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84%EF%BC%88%E2%80%9C%E4%BF%A1%E6%81%AF%E6%8A%BD%E5%8F%96%E2%80%9D%E4%BB%BB%E5%8A%A1%E5%86%A0%E5%86%9B%E9%98%9F%E4%BC%8D%E6%8A%A5%E5%91%8A%EF%BC%89.pdf](https://github.com/yuanxiaosc/Entity-Relation-Extraction/blob/master/Schema约束的知识抽取系统架构（"信息抽取"任务冠军队伍报告）.pdf)) [5th](<https://github.com/cdjasonj/CCF_IE>) [7th](<https://github.com/bojone/kg-2019>) [yuanxiaosc](<https://github.com/yuanxiaosc/Entity-Relation-Extraction>) 

---

#### STOA

+ https://nlpprogress.com/english/relationship_extraction.html

+ https://paperswithcode.com/task/relation-extraction

---

#### Dataset

+ <https://github.com/davidsbatista/Annotated-Semantic-Relationships-Datasets>



##### Distantly Supervised Datasets

(It mainly contain the multiple sentences share a pair of entities)

+ New York Times Corpus

   This dataset consists of 1.18M sentences sampled from 294k 1987-2007 New York Times news articles. There are 24 valid relations in total.

  Give one pair of entity which share by multiple or one sentence, decide the relationship of entity pair in each sentence. In the original testing data set, there are 74,857 entity pairs that correspond to only one sentence, nearly 3/4 over all entity pairs.

+ Wiki-KBP

  the number of relation type in the test set is more than that of the train set



##### Supervised Datasets

+ SemEval-2010 Task 8

  Given a sentence and two tagged nominals, to predict the relation between those nominals *and* the direction of the relation.

+ TACRED (TAC KBP)

+ BioInfer

  more than 50% of the data has overlapping relations

+ WebNLG

  It is originally created for Natural Language Generation (NLG) task. This dataset contains 246 valid relations. In this dataset, a instance including a group of triplets and several standard sentences (written by human). Every standard sentence contains all triplets of this instance.

  (Claire Gardent, Anastasia Shimorina, Shashi Narayan, and Laura Perez-Beltrachini. 2017. Creating training corpora for nlg micro-planners. In Proceedings of ACL.)


+ DocRED

  DocRED: A Large-Scale Document-Level Relation Extraction Dataset [arxiv](https://arxiv.org/abs/1906.06127) [code](https://github.com/thunlp/DocRED) 



##### Few-shot Datasets

+ FewRel

  FewRel 2.0: Towards More Challenging Few-Shot Relation Classification
  Tianyu Gao, Xu Han, Hao Zhu, Zhiyuan Liu, Peng Li, Maosong Sun, Jie Zhou EMNLP2019 [arxiv](<https://arxiv.org/abs/1910.07124>) 



---

#### Tools

+ https://github.com/thunlp/OpenNRE

+ Convolutional Neural Network for Relation Extraction:(ER-CNN, MLMI-CNN, MLMI-CONT)

  https://github.com/may-/cnn-re-tf

---

#### Paperlist

+ http://lietc.com/wiki/relation_extraction
+ https://github.com/roomylee/awesome-relation-extraction
+ <https://github.com/thunlp/NREPapers>
+ <https://github.com/WindChimeRan/NREPapers2019>
+ <https://github.com/WindChimeRan/NREPapers2018>

#### Blogs

+ https://zhuanlan.zhihu.com/p/44772023 summary

+ https://www.cnblogs.com/theodoric008/p/7874373.html summary

+ http://shomy.top/2018/02/28/relation-extraction/ paper notes
+ https://blog.csdn.net/Kaiyuan_sjtu/article/details/90071703 Awesome Relation Extraction Paper

+ https://mp.weixin.qq.com/s/qw9i24goTsVgdk1qW6ie9A 首先对关系抽取的各种主流技术进行概述，而后结合业务中的选择与应用，重点介绍了基于DeepDive的方法，并详述它在神马知识图谱数据构建工作中的应用进展。

#### Paper

+ Learning from Context or Names? An Empirical Study on Neural Relation Extraction
  https://arxiv.org/abs/2010.01923

  > 神经关系抽取，是从语境层面学习，还是从字符层面学习？



##### Unsupervised

+ Sebastian Riedel, Limin Yao, and Andrew McCallum. Modeling relations and their mentions without labeled text, 2010. In Proceedings of ECML PKDD. :star::star::star:

##### Semi-supervised

+ Matching the Blanks: Distributional Similarity for Relation Learning, Livio Baldini Soares, Nicholas FitzGerald, Jeffrey Ling, Tom Kwiatkowski, ACL 2019 [arxiv](<https://arxiv.org/abs/1906.03158>) [BERTem](<https://github.com/zhpmatrix/BERTem>) :star::star::star::star::star:

  > 



---

##### Bert-related

+ Improving Relation Extraction by Pre-trained Language Representations. Christoph Alt, Marc Hübner, Leonhard Hennig, AKBC 2019, [paper](https://openreview.net/pdf?id=BJgrxbqp67) | [code](https://github.com/DFKI-NLP/TRE) 
+ Simple BERT Models for Relation Extraction and Semantic Role Labeling

---

##### Reading Comprehension

https://github.com/bojone/kg-2019-baseline https://kexue.fm/archives/5409

+ Zero-Shot Relation Extraction via Reading Comprehension, Omer Levy, Minjoon Seo, Eunsol Choi, and Luke Zettlemoyer. CoNLL 2017. [arxiv](https://arxiv.org/abs/1706.04115) | [code](http://nlp.cs.washington.edu/zeroshot/) :star::star:

---

##### Question Answering

+ Entity-Relation Extraction as Multi-Turn Question Answering, Xiaoya Li, Fan Yin, Zijun Sun, Xiayu Li, Arianna Yuan, Duo Chai, Mingxin Zhou, Jiwei Li, ACL 2019, [arxiv](https://arxiv.org/abs/1905.05529v1) 

  we propose a new paradigm for the task of entity-relation extraction. We cast the task as a multi-turn question answering problem, i.e., the extraction of entities and relations is transformed to the task of identifying answer spans from the context.

+ Annotating Relation Inference in Context via Question Answering, Omer Levy and Ido Dagan, ACL 2016. [paper](https://aclweb.org/anthology/P16-2041) | [code](https://bitbucket.org/omerlevy/relation_inference_via_qa/src/default/) 

---


##### Multi-task Learning

+ A Hierarchical Multi-task Approach for Learning Embeddings from Semantic Tasks, Victor Sanh, Thomas Wolf, **Sebastian Ruder**, AAAI 2019, [arxiv](https://arxiv.org/abs/1811.06031) | [code](https://github.com/huggingface/hmtl) 

+ Multi-Task Transfer Learning for Weakly-Supervised Relation Extraction, Jing Jiang, 2009 [paper](https://www.aclweb.org/anthology/P09-1114) :star::star:

---

##### Joint Learning

+ TPLinker: Single-stage Joint Extraction of Entities and Relations Through Token Pair Linking https://arxiv.org/abs/2010.13415 https://github.com/131250208/TPlinker-joint-extraction

  [什么？！“路由器”也会做信息抽取了？](https://mp.weixin.qq.com/s/OpawRDM9YFlLLDB1lK0EbQ) [关系重叠？实体嵌套？曝光偏差？这个模型统统都搞得定！](https://mp.weixin.qq.com/s/T_bSjHz8XEeVQMBKVKOH0Q) 



Joint Extraction of Entities and Relations Based on a Novel Decomposition Strategy
Bowen Yu, Zhenyu Zhang, **Jianlin Su**, [arxiv](<https://arxiv.org/abs/1909.04273v1>) 



+ Giannis Bekoulis, Johannes Deleu, Thomas Demeester, Chris Develder. Joint entity recognition and relation extraction as a multi-head selection problem. Expert Systems with Applications, Volume 114, Pages 34-45, 2018

  Giannis Bekoulis, Johannes Deleu, Thomas Demeester, Chris Develder. Adversarial training for multi-context joint entity and relation extraction, In the Proceedings of the Conference on Empirical Methods in Natural Language Processing (EMNLP), 2018

  [code](https://github.com/bekou/multihead_joint_entity_relation_extraction) 



End-to-End Relation Extraction using LSTMs on Sequences and Tree Structures, Makoto Miwa, Mohit Bansal, ACL2016, [arxiv](https://arxiv.org/pdf/1601.00770v2.pdf) :star::star::star: - It utilizes more linguistic resources (e.g., POS tags, chunks, syntactic parsing trees).



Joint Entity and Relation Extraction Based on A Hybrid Neural Network



A neural joint model for entity and relation extraction from biomedical text



Going out on a limb: Joint Extraction of Entity Mentions and Relations without Dependency Trees



+ Joint Extraction of Entities and Relations Based on a Novel Tagging Scheme, Suncong Zheng, Feng Wang, Hongyun Bao, Yuexing Hao, Peng Zhou, Bo Xu, ACL2017 outstanding paper, [arxiv](https://arxiv.org/abs/1706.05075) | [code](https://github.com/zsctju/triplets-extraction) :star:

CoType: Joint Extraction of Typed Entities and Relations with Knowledge Bases, Xiang Ren, Zeqiu Wu, Wenqi He, Meng Qu, Clare R. Voss, Heng Ji, Tarek F. Abdelzaher, Jiawei Han, WWW 2017, [arxiv](https://arxiv.org/abs/1610.08763) | [code](https://github.com/INK-USC/DS-RelationExtraction) 

---

##### Two-stage

+ A Frustratingly Easy Approach for Joint Entity and Relation Extraction

  *https://arxiv.org/pdf/2010.12812.pdf*

  [陈丹琦“简单到令人沮丧”的屠榜之作：关系抽取新SOTA！](https://mp.weixin.qq.com/s/xwljKL3FjY-Nw-Zll4x3pQ) 



###### Rank

+ Classifying Relations by Ranking with Convolutional Neural Networks, C´ıcero Nogueira dos Santos, Bing Xiang, Bowen Zhou, ACL 2015, [paper](https://www.aclweb.org/anthology/P15-1061) | [arxiv](https://arxiv.org/abs/1504.06580) :star::star::star:
+ 

###### CNN

+ Relation Classification via Convolutional Deep Neural Network, Daojian Zeng, Kang Liu, Siwei Lai, Guangyou Zhou and Jun Zhao, 2014 :star::star::star:

+ Relation Extraction: Perspective from Convolutional Neural Networks, Thien Huu Nguyen, Ralph Grishman, NAACL 2015. [paper](http://www.cs.nyu.edu/~thien/pubs/vector15.pdf) :star::star::star:

+ Distant supervision for relation extraction via piecewise convolutional neural networks, Daojian Zeng, Kang Liu, Yubo Chen and Jun Zhao. EMNLP 2015 [paper](https://www.cs.cmu.edu/~ark/EMNLP-2015/proceedings/EMNLP/pdf/EMNLP203.pdf) :star::star::star:

  CNN + ONE, PCNN + ONE



###### Attention

It can be used for the distant supervision dataset. - 利用Attention模型对数据进行全方位的权重计算，从而得到全面而不失“选择”的训练数据.

Attention has two steps: (1) computing weights for the sentences and (2) aggregating the weighted sentences. 

Weights can be uniform, or computed using a sigmoid or softmax. Weighted sentences can be aggregated using average pooling or max pooling.



+ Distant Supervision Relation Extraction with Intra-Bag and Inter-Bag Attentions, Zhi-Xiu Ye, Zhen-Hua Ling,  NAACL 2019 [arxiv](https://arxiv.org/abs/1904.00143) | [code](https://github.com/ZhixiuYe/Intra-Bag-and-Inter-Bag-Attentions) :star:

+ Cross-relation Cross-bag Attention for Distantly-supervised Relation Extraction, Yujin Yuan, Liyuan Liu, Siliang Tang, Zhongfei Zhang, Yueting Zhuang, Shiliang Pu, Fei Wu, Xiang Ren, AAAI 2019 [arxiv](https://arxiv.org/abs/1812.10604) 

+ Attention-Based Bidirectional Long Short-Term Memory Networks for Relation Classification, ACL 2016, Peng Zhou, Wei Shi, Jun Tian, Zhenyu Qi, Bingchen Li, Hongwei Hao, Bo Xu. [paper](http://www.aclweb.org/anthology/P16-2034) :star::star::star:

+ Neural Relation Extraction with Selective Attention over Instances, Yankai Lin, Shiqi Shen, Zhiyuan Liu, Huanbo Luan, Maosong Sun, ACL 2016, [paper](http://nlp.csai.tsinghua.edu.cn/~lzy/publications/acl2016_nre.pdf) | [OpenNRE](https://github.com/thunlp/OpenNRE) :star::star::star:

  CNN + ATT, PCNN + ATT

  attention: query is the relation type

###### Knowledge Base

+ Connecting Language and Knowledge with Heterogeneous Representations for Neural Relation Extraction, Peng Xu, Denilson Barbosa, NAACL HLT 2019, [arxiv](<https://arxiv.org/abs/1903.10126>) 



###### Multi-instance

Mainly for the distant supervision dataset. - 从训练集中抽取取置信度高的训练样例训练模型.

- Multi-instance Single-label

  For multi-sentence share a pair of entities, it assume that only one sentence is active for this entity pair (should have only one relation type). Hence, it will lose a large amount of rich information containing in those neglected sentences.

Modeling relations and their mentions without labeled text, Sebastian Riedel, Limin Yao, and Andrew McCallum. 2010 ECML-PKDD, :star::star::star:

Distant supervision for relation extraction via piecewise convolutional neural networks, Daojian Zeng, Kang Liu, Yubo Chen, and Jun Zhao.. In Proceedings of EMNLP. 2015.:star::star::star:



- Multi-instance Multi-label

  multi-sentence share a pair of entities should have multiple relation type

Knowledge based weak supervision for information extraction of overlapping relations, Raphael Hoffmann, Congle Zhang, Xiao Ling, Luke Zettlemoyer, and Daniel S Weld. ACLHLT 2011, [paper](http://raphaelhoffmann.com/publications/acl2011.pdf) [Slides](http://raphaelhoffmann.com/publications/acl2011-slides.pptx) [Source Code](http://www.cs.washington.edu/ai/raphaelh/mr). :star::star::star:

Multi-instance Multi-label Learning for Relation Extraction, Mihai Surdeanu, Julie Tibshirani, Ramesh Nallapati, **Christopher D. Manning**, EMNLP-CoNLL 2012 [paper](http://aclweb.org/anthology-new/D/D12/D12-1042.pdf) | [code](https://nlp.stanford.edu/software/mimlre.shtml):star::star::star:



###### Dependency Trees

Shortest dependency path (SDP) between entity pairs of dependency parse trees

RelEx—Relation extraction using dependency parse trees, Katrin Fundel  Robert Küffner  Ralf Zimmer, Bioinformatics 2007. :star::star::star:

Classifying relations via long short term memory networks along shortest dependency paths, Y. Xu, L. Mou, G. Li, Y. Chen, H. Peng, and Z. Jin, EMNLP 2015. 

Improved relation classification by deep recurrent neural networks with data augmentation, Y. Xu, R. Jia, L. Mou, G. Li, Y. Chen, Y. Lu, and Z. Jin, arXiv preprint arXiv:1601.03651, (2016).

Graph Convolution over Pruned Dependency Trees Improves Relation Extraction, Yuhao Zhang, Peng Qi, **Christopher D. Manning**, EMNLP 2018 [arxiv](https://arxiv.org/abs/1809.10185) | [code](https://github.com/qipeng/gcn-over-pruned-trees) 



###### Reinforcement Learning

Mainly for the distant supervision dataset.

Reinforcement Learning for Relation Classification from Noisy Data, Jun Feng, Minlie Huang, Li Zhao, Yang Yang, Xiaoyan Zhu, AAAI2018. [arxiv](https://arxiv.org/abs/1808.08013v1) | [code](https://github.com/unreliableXu/TensorFlow_RLRE) 

Robust Distant Supervision Relation Extraction via Deep Reinforcement Learning, Pengda Qin, Weiran Xu, William Yang Wang, [arxiv](https://arxiv.org/abs/1805.09927v1) - Unlike the removal operation in the previous studies, we redistribute them into the negative examples.



###### Adversarial Training

DSGAN: Generative Adversarial Training for Distant Supervision Relation Extraction, Pengda Qin, Weiran Xu, William Yang Wang, ACL 2018 [arxiv](https://arxiv.org/abs/1805.09929) 



###### Distant Supervision Approaches

+ Distant supervision for relation extraction without labeled data, Mike Mintz, Steven Bills, Rion Snow, **Dan Jurafsky**, 2009 ACL, [paper](http://stanford.edu/~jurafsky/mintz.pdf) :star::star::star::star:

  <details><summary>Assumption</summary>
      The intuition of distant supervision is that any sentence that contains a pair of entities that participate in a known Freebase relation is likely to express that relation in some way.
  </details>
  

- training strategy with noisy data

  multi-instance learning

  attention

  reinforcement learning



+ learning from CV

  [Learning with Noisy Labels - University of Texas at Austin](http://www.cs.utexas.edu/users/inderjit/public_papers/noisylabels_nips13.pdf)

  [Cost-Sensitive Learning with Noisy Labels](http://www.cs.utexas.edu/~inderjit/public_papers/cost_sensitive_noisy_jmlr18.pdf) 

  [Masking: A New Perspective of Noisy Supervision](https://arxiv.org/abs/1805.08193) 

  [Co-teaching: Robust Training of Deep Neural Networks with Extremely Noisy Labels](https://arxiv.org/abs/1804.06872)

  ...



+ training/testing

training:

1. 使用NET（named entity tagger）标注。
2. 对在freebase中出现的实体对提取特征（从所有出现该实体对的句子中），构造训练数据。
3. Multi-class logistic regression classifier

论文中采用的NET标注工具为斯坦福的NRT标注器，再生成训练集的过程中，我们首先对大量文本句子进行命名实体标注，如果一个句子中含有两个实体，且这两个实体在Freebase（KB）中是一个关系对，那么从句子中提取特征，将关系作为类别，直到该类别中不再有新的句子加入，我们从该类别中的所有句子提取特征向量并且合并成一个更大的特征向量，从而训练出Multiclass logistic regression classifier。

testing:

1. 使用NET（named entity tagger）标注。
2. 在句子中出现的每对实体都被考虑做为一个潜在的关系实例，作为测试数据。
3. 使用训练好的模型对实体对进行分类。

 在测试阶段，先对句子中的命名实体进行标注，抽取其中的命名实体对和特征。如果多个句子的命名实体对一样，则将它们的特征合并在同一个特征向量中。然后利用逻辑回归分类器，对关系名称进行识别。这种方法的好处是可以综合文本中的多处，对一个实体对进行关系判断。

例如：<Steven Spielberg, Saving Private Ryan >---film-director

我们单看以下的第一个句子和第二个句子，都不能判断出Steven Spielberg和Saving Private Ryan之间存在film-director关系，但是把两个句子结合起来我们就能做到了。

 [Steven Spielberg]’s film [Saving Private Ryan] is loosely based on the brothers’ story.

 Allison co-produced the Academy Award winning [Saving Private Ryan], directed by [Steven Spielberg]... 




