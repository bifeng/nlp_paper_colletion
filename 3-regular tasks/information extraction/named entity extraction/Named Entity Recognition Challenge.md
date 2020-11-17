## chinese word segmentation



+ Zhang Y, Yang J. Chinese NER Using Lattice LSTM[J]. meeting of the association for computational linguistics, 2018: 1554-1564.

  不足之处：1）基于RNN的结构很难利用GPU的并行性，而且这个结构用了两套LSTM，一套用于建模字符的关系，一套用于建模字符与匹配的词的关系，所以速度更慢；2）很容易遇到潜在词语冲突的问题，RNN这种序列结构在处理到“南京市长”这四个字，还没未接触到“江大桥”这三个字时，就必须要对这个“长”字进行预测，它到底是属于“南京市长”还是“长江大桥”？

+ CNN-Based Chinese NER with Lexicon Rethinking
  1) 利用CNN结构解决GPU并行性的问题

  利用CNN结构来建模句子中的字符和字符可能匹配的词语，从而在避免分词错误问题的同时，很好地利用了GPU的性能。

  采用窗口为2的CNN建模整个句子，则CNN的第二层建模了整个句子Bigram的信息，第三层建模了整个句子Trigram的信息...

  2) 利用反思机制解决潜在词语的冲突问题

  基于整个句子的语义再去重新调整每个词对每个句子的贡献程度



### Summary

如何规避分词错误？

1. 字符级 

   

2. 



## parallel

more refer: [NER论文精读（三）：多任务学习框架与并行机制](https://mp.weixin.qq.com/s/4-eJHAsAsg0z2ZxrXcyeBg)



+ Strubell E, Verga P, Belanger D, et al. Fast and Accurate Entity Recognition with Iterated Dilated Convolutions[J]. empirical methods in natural language processing, 2017: 2670-2680.



## nested entities

refer: [NER论文精读（一）：池化上下文嵌入及嵌套实体识别](https://mp.weixin.qq.com/s/JoS52Z7n4PodBki7UsFA1g)



嵌套的实体类型，如一个实体类型的长词，包含另一个实体类型的短词。

### Question

+ 如何标注？

  使用BIO标注方法，参照detection order rule和non-duplication rule对“interleukin-2 receptoralpha gene”进行标记，得到两种标签序列：{O, B-Protein, O, O, O, O}和{O, B-DNA, I-DNA, I-DNA, I-DNA, O}，可以看到，每个单词的标签数量等于给定单词序列中实体的嵌套层级数量。:question:

+ 如何确定边界？



### Paper

+ Multi-Grained Named Entity Recognition
  Congying Xia, Chenwei Zhang, Tao Yang, Yaliang Li, Nan Du, Xian Wu, Wei Fan, Fenglong Ma, Philip Yu ACL 2019 [arxiv](<https://arxiv.org/abs/1906.08449>) 

+ A Unified MRC Framework for Named Entity Recognition. Xiaoya Li, Jingrong Feng, Jiwei Li. [arxiv](<https://arxiv.org/abs/1910.11476>)  | [blog](<https://zhuanlan.zhihu.com/p/89019478>) 

+ Sequence-to-Nuggets: Nested Entity Mention Detection via Anchor-Region Networks. Hongyu Lin, Yaojie Lu, Xianpei Han, Le Sun. ACL 2019 [code](<https://github.com/sanmusunrise/ARNs>) 

  > 假设-一个实体只有一个head word/anchor word，因此嵌套实体也可据此得以区分，其中head word/anchor word其实就是实体的指示词，有助于识别实体。
  >
  > 本文分两步识别：第一步anchor detector network，识别head word/anchor word, 第二步region recognizer network，识别实体的边界。

+ Ju M, Miwa M, Ananiadou S. A neural layered model for nested named entity recognition[C]//Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long Papers). 2018, 1: 1446-1459.

  基于扁平NER层进行开发，重视区域边界的单词/字符信息并在区域内注入了平均的思想

+ Sohrab M G, Miwa M. Deep Exhaustive Model for Nested Named Entity Recognition[C]//Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing. 2018: 2843-2849.

  基于扁平NER层进行开发，重视区域边界的单词/字符信息并在区域内注入了平均的思想

+ Wang B, Lu W, Wang Y, et al. A neural transition-based model for nested mention recognition[J]. arXiv preprint arXiv:1810.01808, 2018.

+ Nested Named Entity Recognition Revisited

+ Jenny Rose Finkel, and Christopher D. Manning. (2009). “Nested Named Entity Recognition.” In: Proceedings of the 2009 Conference on Empirical Methods on Natural Language Processing (EMNLP 2009). [paper](<https://nlp.stanford.edu/pubs/nested-ner.pdf>) 

+ Lu, Roth 2015

  Lu和Roth在2015年构建了超图，使用边连接多个节点来表示嵌套实体，但是无法编码表示实体之间的依赖关系。

+ Alex, Beatrice, Barry Haddow, and Claire Grover. "Recognising nested named entities in biomedical text." Proceedings of the Workshop on BioNLP 2007: Biological, Translational, and Clinical Language Processing. Association for Computational Linguistics, 2007.

  Alex等人在2007年提出了基于特征的方法来解决嵌套NER问题，他们的模型时间复杂度很高，是句子中单词数量的立方。

+ 刘非凡, 赵军, 徐波. 实体提及的多层嵌套识别方法研究[J]. 中文信息学报, 2007, 21(2):14-21.  被引量：3







## emerging/long tail entities

how to recognize long tail of less well-known entities ?



### Competition

- [互联网金融新实体发现](<https://www.datafountain.cn/competitions/361>)
- https://noisy-text.github.io/2017/emerging-rare-entities.html

### STOA

- <https://nlpprogress.com/english/named_entity_recognition.html>

  

### Datasets

- WNUT-17

### Evaluation

entity-level  F1

surface forms F1

### Paper

- *Pooled Contextualized Embeddings for Named Entity Recognition. Alan Akbik, Tanja Bergmann and Roland Vollgraf. 2019 Annual Conference of the North American Chapter of the Association for Computational Linguistics, **NAACL 2019**.*

  > pre-trained contextual string embeddings + BiLSTM-CRF
  >
  > 
  >
  > Since most entities appear only few times in this dataset, giving our approach little evidence to aggregate and pool, so there is no significant improvements on the WNUT-17 task.

- Early Discovery of Emerging Entities in Microblogs, Satoshi Akasaki, Naoki Yoshinaga, Masashi Toyoda, IJCAI 2019, [arxiv](<https://arxiv.org/abs/1907.03513>) 

  > Assumption/Intuition: people write about emerging entities with expressions suggesting their emergence when those entities are not well known to the public, considering that potential readers would be unfamiliar with them.
  >
  > 
  >
  > Time-sensitive Distant-supervision:  collects training data using an existing KB
  >
  > positive: collects early-stage posts in a massive amount of time-series text where non-homographic entities registered in a KB first emerge.
  >
  > negative: also collect adequately-later posts after the first appearance as negative examples to robustly discriminate them from emerging contexts (When a model is trained only with the collected emerging
  > contexts, it will be over-fitted to detect only mentions of the emerging entities used to collect the training data).

  > Definition of Emerging/Prevalent Entity:
  >
  > Emerging contexts - Contexts in which the writers assumed the readers do not know the existence of the entities.
  > Emerging entities - Entities in the state of being still observed in emerging contexts
  >
  > Prevalent contexts - Contexts in which the writers assumed the readers know the existence of the entities.
  > Prevalent entities - Entities in the state of being mainly observed in prevalent contexts.



### Method

topic model

keyword extraction



自动识别未登录词从而发现新词

兼容领域词库从而实现多领域自动适配 (cross-domain adaptation)



## Bootstrapping (Semi-supervised)





## large scale (Distant Supervision)

### paper

+ Raw-to-End Name Entity Recognition in Social Media, Liyuan Liu, Zihan Wang, Jingbo Shang, Dandong Yin, Heng Ji, Xiang Ren, Shaowen Wang, Jiawei Han, [arxiv](<https://arxiv.org/abs/1908.05344>) 

+ Better Modeling of Incomplete Annotation for Named Entity Recognition [code](<https://github.com/allanj/ner_incomplete_annotation>) 
+ <https://towardsdatascience.com/annotator-bias-and-incomplete-annotations-for-named-entity-recognition-ner-84819af730>



+ Distant Supervision

  (Problem: Limited Coverage, Noisy Data)

+ 引入新的标注方式降噪

  AutoNER

+ 引入共享层降噪

  语言模型方法 - 学习领域敏感特征 
  Liu L, Shang J, Ren X, et al. Empower sequence labeling with task-aware neural language model[C]//Thirty-Second AAAI Conference on Artificial Intelligence. 2018.

+ Shang J, Liu L, Ren X, et al. Learning Named Entity Tagger using Domain-Specific Dictionary[J]. arXiv preprint arXiv:1809.03599, 2018.

+ Anand, Ashish, and Amit Awekar. "Fine-grained entity type classification by jointly learning representations and label embeddings." *arXiv preprint arXiv:1702.06709* (2017).



### summary

如何识别大量的实体类型？

示例：文本中存在上百种类型的实体，如何识别？

1）训练多个单类型的实体识别器

对于同一个实体，如果其类型也相同，但实体所指不相同，则在训练该类型的实体识别器时，需要新增标签进行区分。

2）数据增广

新增弱标注数据，扩大训练集



## Hierarchical/Fine-Grained Entity Typing

细粒度实体分类论文综述：（二）[site](https://www.6aiq.com/article/1593879306665) 



+ 方法一：建模类型树 entity type tree embedding

  借鉴Jiawei Han的思想

  Hierarchical Topic Mining via Joint Spherical Tree and Text Embedding. Yu Meng, Yunyi Zhang, Jiaxin Huang, Yu Zhang, Chao Zhang, Jiawei Han
   [arxiv](https://arxiv.org/abs/2007.09536) 

  https://github.com/xiaojie2018/Hierarchical_label_model





+ Anand, Ashish, and Amit Awekar. "Fine-grained entity type classification by jointly learning representations and label embeddings." EACL 2017 [arxiv](<https://arxiv.org/abs/1702.06709>) 



## doc-level













