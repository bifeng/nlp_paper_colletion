## Joint

https://paperswithcode.com/task/joint-entity-and-relation-extraction



+ How to recognize entities which have no relationship ?

+ 如何输出实体、关系及实体类型？

  方法：

  1. 半指针半标注 - 实体及实体类型的预测，其指针使用实体类型指针
  2. 半指针半标注 - 实体loss + 实体类型loss + 关系及尾实体loss





+ Two are Better than One: Joint Entity and Relation Extraction with Table-Sequence Encoders
+ A Frustratingly Easy Approach for Joint Entity and Relation Extraction





## Multiple 

- Extracting Multiple-Relations in One-Pass with Pre-Trained Transformers, Haoyu Wang, Ming Tan, Mo Yu, Shiyu Chang, Dakuo Wang, Kun Xu, Xiaoxiao Guo, Saloni Potdar, [arxiv](<https://arxiv.org/abs/1902.01030>) | [code](<https://github.com/yuanxiaosc/Multiple-Relations-Extraction-Only-Look-Once>) 



## Overlapping

Multiple pair entities correspond to only one sentence (overlapping relation extraction)



#### papers

1. A Novel Cascade Binary Tagging Framework for Relational Triple Extraction
   Zhepei Wei, Jianlin Su, Yue Wang, Yuan Tian, Yi Chang ACL 2020. [arxiv](<https://arxiv.org/abs/1909.03227>) 

   

2. Joint Extraction of Entities and Overlapping Relations Using Position-Attentive Sequence Labeling

   Baidu. AAAI-2019 [pdf](https://www.aaai.org/ojs/index.php/AAAI/article/view/4591/4469) 

3. Knowledge based weak supervision for information extraction of overlapping relations, Raphael Hoffmann, Congle Zhang, Xiao Ling, Luke Zettlemoyer, and Daniel S Weld. ACLHLT 2011, [paper](http://raphaelhoffmann.com/publications/acl2011.pdf) [Slides](http://raphaelhoffmann.com/publications/acl2011-slides.pptx) [Source Code](http://www.cs.washington.edu/ai/raphaelh/mr). :star::star::star:

4. A Walk-based Model on Entity Graphs for Relation Extraction, Fenia Christopoulou, Makoto Miwa, Sophia Ananiadou, ACL 2018, [arxiv](https://arxiv.org/abs/1902.07023v1) 

   treats multiple pairs in a sentence simultaneously and considers interactions among them...

5. Extracting Relational Facts by an End-to-End Neural Model with Copy Mechanism, Xiangrong Zeng, Daojian Zeng, Shizhu He, Kang Liu, Jun Zhao, ACL 2018 [code](https://github.com/xiangrongzeng/copy_re) 

   Classify overlapping entity with three triplet overlap degree, including Normal, EntityPairOverlap and SingleEntiyOverlap.

   seq2seq learning with copy mechanism - one entity is allowed to be copied several times when it needs to participate in different triplets.

   Joint learning - the entities and relations could be jointly extracted

   Dataset: New York Times Corpus/WebNLG

   缺点：没有针对各类overlapping type进行ablation analysis！！！This method strongly relies on the training data, and cannot extract multi-word entity mentions.

6. A Hierarchical Framework for Relation Extraction with Reinforcement Learning, Ryuichi Takanobu, Tianyang Zhang, Jiexi Liu, Minlie Huang,  AAAI 19 [arxiv](https://arxiv.org/abs/1811.03925) | [code](https://github.com/truthless11/HRL-RE) 

   classify overlapping relations into two types: Type I: two triples share only one entity within a sentence, Type II: two triples share two entities (both head and tail entities) within a sentence.

   a hierarchical reinforcement learning (HRL) framework - 1) a high-level RL process that detects a relation indicator in a sentence; 2) a low-level RL process that identifies the associated entities for the corresponding relation.

   joint extraction - a “relation”-first, “argument”-second approach. <u>we first detect a relation indicator and then extract the corresponding entities as the argument of a relation</u>. 

     ​	**relation indicator**, is the position in a sentence when sufficient information has been mentioned to identify
     a semantic relation. Different from relation trigger (i.e., explicit relation mention), relation indicators can be verbs
   (e.g. die of), nouns (e.g. his father), or even prepositions (e.g. from/by), other symbols such as comma and period.

   ​	**relation triggers**, which refer to a phrase that explicitly expresses the occurrence of a relation in a sentence, and then determine their arguments to reduce the task complexity. But there are many cases where no relation trigger appears in a sentence so that such relations cannot be captured.

   Dataset: New York Times Corpus

   缺点：没有分析该模型的不足之处 (bad cases analysis).

7. Supervised Open Information Extraction, NAACL-2018, [pdf](https://www.aclweb.org/anthology/N18-1081) | [code](https://allennlp.org/models#open-information-extraction) 

   formulate of Open IE as a sequence tagging problem, addressing challenges such as encoding multiple extractions for a predicate

   introduce a novel approach that can extract multiple, overlapping tuples for each sentence 



**Knowledge-Based Weak Supervision for Information Extraction of Overlapping Relations.** *Raphael Hoffmann, Congle Zhang, Xiao Ling, Luke Zettlemoyer, Daniel S. Weld.* ACL-HLT 2011. [paper](http://www.aclweb.org/anthology/P11-1055)

> This paper presents a novel approach for multi-instance learning with overlapping re- lations that combines a sentence-level extrac- tion model with a simple, corpus-level compo- nent for aggregating the individual facts.



#### Summary

solution:

1. one sentence just focus one pair of entities, so if the sentence contain multiple relation, then you need replicate the sentence. Besides, for unrelated entities, you can using special annotation (such as 'O_B'/'O_I'/'O_E'). (one sentence one label) 

Downside - 

First, it will introduce the sentence independent hypotheses, which is not true!

Second, for multiple relation share the common entity, you will lose the information for this entity connection with other entities.

Third, for prediction new sentence, you should provide lots of entity pairs of this sentence, which is redundancy.

Last but not least, create lots of training example which contain some redundancy.

2. change it to an <u>attribute extraction or open information extraction</u> problem
3. multi-label learning (one sentence multi-label)
4. multi-instance learning (for multi-relation of one sentence, using each pair of entity (such as position encoding+word embedding) to represent the sentence, so one sentence can be express by many sentences (sentences bag).)
5. hierarchical



## Long tail (Few Shot)

<u>It must consider the domain of relation type (data distribution unbalance problem).</u>



#### papers

- 论文浅尝 | 解决知识图谱补全中的长尾关系和不常见实体问题
  链接：https://www.aclweb.org/anthology/P19-1024.pdf

- Long-tail Relation Extraction via Knowledge Graph Embeddings and Graph Convolution Networks,  NAACL 2019 

- **Hierarchical Relation Extraction with Coarse-to-Fine Grained Attention** *Xu Han, Pengfei Yu, Zhiyuan Liu, Maosong Sun, Peng Li.* EMNLP 2018. [paper](http://www.aclweb.org/anthology/D18-1247)

  > We aim to incorporate the hierarchical information of relations for distantly supervised relation extraction and propose a novel hierarchical attention scheme. The multiple layers of our hierarchical attention scheme provide coarse-to-fine granularity to better identify valid instances, which is especially effective for extracting those long-tail relations.



+ Tianyu Gao, Xu Han, Zhiyuan Liu, Maosong Sun. Hybrid Attention-based Prototypical Networks for Noisy Few-Shot Relation Classification. The 33th AAAI Conference on Artificial Intelligence (AAAI 2019).
+ Zhi-Xiu Ye, Zhen-Hua Ling. Multi-Level Matching and Aggregation Network for Few-Shot Relation Classification. The 57th Annual Meeting of the Association for Computational Linguistics (ACL 2019).
+ Livio Baldini Soares, Nicholas FitzGerald, Jeffrey Ling, Tom Kwiatkowski. Matching the Blanks: Distributional Similarity for Relation Learning. The 57th Annual Meeting of the Association for Computational Linguistics (ACL 2019).



#### Summary







## Bootstrapping (Semi-supervised)





## large scale (Distant Supervision)

noisy label problem

limited coverage problem



#### papers

+ Large Scaled Relation Extraction with Reinforcement Learning [site](<http://www.nlpr.ia.ac.cn/cip/~liukang/liukangPageFile/zeng_aaai2018.pdf>) 

+ Distantly-supervised Relation Extraction with Knowledge Bases [code](<https://github.com/INK-USC/DS-RelationExtraction>) 
+ Looking Beyond Label Noise: Shifted Label Distribution Matters in Distantly Supervised Relation Extraction, EMNLP 2019 [arxiv](<https://arxiv.org/abs/1904.09331>) [code](<https://github.com/INK-USC/shifted-label-distribution>) 
+ A Soft-label Method for Noise-tolerant Distantly Supervised Relation Extraction. *Tianyu Liu, Kexiang Wang, Baobao Chang, Zhifang Sui.* EMNLP 2017. [paper](http://www.aclweb.org/anthology/D17-1189)

> We introduce an entity-pair level denoise method which exploits semantic information from correctly labeled entity pairs to correct wrong labels dynamically during training.

+ ARNOR: Attention Regularization based Noise Reduction for Distant Supervision Relation Classification, ACL 2019. [site](<https://github.com/PaddlePaddle/models/tree/develop/PaddleNLP/Research/ACL2019-ARNOR>) 

> 



+ Daojian Zeng, Kang Liu, Yubo Chen, Jun Zhao. Distant Supervision for Relation Extraction via Piecewise Convolutional Neural Networks. The 2015 Conference on Empirical Methods in Natural Language Processing (EMNLP 2015).
+ Yankai Lin, Shiqi Shen, Zhiyuan Liu, Huanbo Luan, Maosong Sun. Neural Relation Extraction with Selective Attention over Instances. The 54th Annual Meeting of the Association for Computational Linguistics (ACL 2016).
+ Yi Wu, David Bamman, Stuart Russell. Adversarial Training for Relation Extraction. The 2017 Conference on Empirical Methods in Natural Language Processing (EMNLP 2017).
+ Jun Feng, Minlie Huang, Li Zhao, Yang Yang, Xiaoyan Zhu. Reinforcement Learning for Relation Classification from Noisy Data. The 32th AAAI Conference on Artificial Intelligence (AAAI 2018).



#### Summary

Solution:

Multi-instance learning - 从训练集中抽取取置信度高的训练样例训练模型

Sentence level Attention - 利用Attention模型对数据进行全方位的权重计算，从而得到全面而不失“选择”的训练数据

Adversarial training - 

Reinforcement learning - 

...



select correct sample form the noisy data 

separate the correct sample from noisy data, and use the noisy data as negative example

...



俄亥俄州立大学 Prof. Alan Ritter认为将Structured方法和Neural方法结合获得更好结果.

Neural方法擅长于表示学习以及依赖于隐层表示所获得的多任务学习能力；而Structured方法则更擅长于学习时的推断、建模丢失的数据以及有重叠的关系。

Prof. Alan Ritter根据Distant Supervision方法的历史发展过程划分为Structured方法和Neural方法:

| structured               |                                                             | neural                      |                                     |
| ------------------------ | ----------------------------------------------------------- | --------------------------- | ----------------------------------- |
| Mintz et.al. ACL 2009    | KB (Freebase) as Distant Supervision                        | Zeng et.al. ACL 2015        | Piecewise CNN                       |
| Riedel et.al. ECML 2010  | NYT/Freebase Dataset + MIL                                  | Toutanova et.al. EMNLP 2015 | Dependency Path CNN                 |
| Hoffmann et.al. ACL 2011 | Structured Perceptron + Determ. Or Mention-level Evaluation | Lin et.al. ACL 2016         | Piecewise CNN + Selective Attention |
| Ritter et.al. TACL 2013  | Missing Data (Mention-level Evaluation)                     |                             |                                     |
|                          |                                                             |                             |                                     |
|                          |                                                             |                             |                                     |
|                          |                                                             |                             |                                     |



## Explanation





## Low Resource

Neural Rule Grounding for Low-Resource Relation Extraction, [code](<https://github.com/INK-USC/REGD>) 

## Evolving 

如何抽取随时间变化的关系?



## Doc-level

[文档级实体关系抽取——知识获取的新挑战](https://zhuanlan.zhihu.com/p/93318977)

+ Yao, Limin, Sebastian Riedel, and Andrew McCallum. "Collective cross-document relation extraction without labelled data." *Proceedings of the 2010 Conference on Empirical Methods in Natural Language Processing*. Association for Computational Linguistics, 2010.





## Cross-Domain

+ Improving Cross-Domain Performance for Relation Extraction via Dependency Prediction and Information Flow Control
  Amir Pouran Ben Veyseh, Thien Huu Nguyen, Dejing Dou. [arxiv](<https://arxiv.org/abs/1907.03230>) 



## Cross-Sentence & Multiple

跨句多元关系抽取



## unclassifiable 

how to decide/discriminate the no-relation in sentence ? (the classifier will also need to be able to label an example as no-relation)



### Summary

Similar to Unlinkable Mention Prediction of Entity Linking/Unanswerable Question in Reading Comprehension.

method 1 - threshold (manual setting or as a parameter to learn in rank)

method 2 - a filter classifier (binary/multi-class classifier, you need add a `no-relation` label)

method 3 - combined (add no-relation as candidate relation in rank)

method 4 - make the prob of `no-relaiton` is `1/num_class`, and without add a `no-relation` label. So, you can label an example as no-relation if it's prob identical to `1/num_class`. (similar to label smoothing regularization)









