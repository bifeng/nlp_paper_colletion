refer:<br>[面向新闻媒体的命名实体识别技术](https://mp.weixin.qq.com/s/onAU0jJpFMXY80aRGB6vIA) 



### STOA

- https://nlpprogress.com/english/named_entity_recognition.html
- <https://www.paperswithcode.com/task/named-entity-recognition-ner/latest>
- <https://github.com/lingluodlut/BioNER-Progress>



### Competition

- NLPCC-2020 Shared Task on AutoIE

  https://github.com/ZhuiyiTechnology/AutoIE

  [1st](https://bbs.hankcs.com/t/topic/2793) 

- MUC (Message Understanding Conference)

  MUC-6

  ​	MET (Multilingual Entity Task) 

  ​	主要是基于规则的系统参与评测

  MUC-7

  ​	MET (Multilingual Entity Task)

- ACE (Automatic Content Extraction)

  EDT (Entity Detection and Tracking)

- TAC-KBP (Text Analysis Conference Knowledge Base Population)



Chinese

- SigHAN (the special interest group for chinese information processing of the association for computational linguistics)

  2006

  2008



### Datasets

- <https://github.com/juand-r/entity-recognition-datasets>
- <https://github.com/davidsbatista/NER-datasets>



### Application

bio ner
medical ner



### Tools

- NeuroNER

  Named-entity recognition using neural networks. Easy-to-use and state-of-the-art results. [http://neuroner.com](http://neuroner.com/)

  <https://github.com/Franck-Dernoncourt/NeuroNER>

- AutoNER (distant supervision)

  Learning Named Entity Tagger from Domain-Specific Dictionary [https://shangjingbo1226.github.io/Aut…](https://shangjingbo1226.github.io/AutoNER/)

  <https://github.com/shangjingbo1226/AutoNER>

- Simple and Efficient Tensorflow implementations of NER models with tf.estimator and tf.data

  https://github.com/guillaumegenthial/tf_ner

- Kashgari

  Simple, Keras-powered multilingual NLP framework, allows you to build your models in 5 minutes for named entity recognition (NER), part-of-speech tagging (PoS) and text classification tasks. Includes BERT, GPT-2 and word2vec embedding.

  https://github.com/BrikerMan/Kashgari

- anago

  Bidirectional LSTM-CRF and ELMo for Named-Entity Recognition, Part-of-Speech Tagging and so on. <https://anago.herokuapp.com/>

  <https://github.com/Hironsan/anago>

- http://alchemy.cs.washington.edu/

  

- ProbCog: A Toolbox for Statistical Relational Learning and Reasoning [code](https://github.com/opcode81/ProbCog) 

  

+ KnowItAll - 华盛顿大学

  无监督的细粒度实体抽取系统

  Oren Etzioni, ..., Web-scale information extraction in knowitall: (preliminary results). WWW 2004.

  Oren Etzioni, ..., Unsupervised named-entity extraction from the web: An experimental study. AI 2005.

  Oren Etzioni, ..., Open information extraction: The second generation. IJCAI 2011.

  ...



### literature review

+ Named Entity Recognition -- Is there a glass ceiling?
  Tomasz Stanislawek, Anna Wróblewska, Alicja Wójcicka, Daniel Ziembicki, Przemyslaw Biecek CoNLL 2019 [arxiv](<https://arxiv.org/abs/1910.02403>) 

+ A Survey on Deep Learning for Named Entity Recognition, Jing Li, Aixin Sun, Jianglei Han, Chenliang Li, 2018.12, [arxiv](https://arxiv.org/abs/1812.09449) :star:
+ A Survey on Recent Advances in Named Entity Recognition from Deep Learning models, Vikas Yadav, Steven Bethard, COLING 2018, [paper](https://www.aclweb.org/anthology/C18-1182) 
+ A survey of named entity recognition and classification, David Nadeau, Satoshi Sekine, 2007, [paper](https://nlp.cs.nyu.edu/sekine/papers/li07.pdf)  :star::star::star::star:



### Paperlist

+ https://github.com/pfliu-nlp/Named-Entity-Recognition-NER-Papers



### Paper



#### Supervised

##### Transformer/Bert

+ Entities as Experts: Sparse Memory Access with Entity Supervision Thibault Févry, Livio Baldini Soares, Nicholas FitzGerald, Eunsol Choi, Tom Kwiatkowski [arxiv](<https://arxiv.org/abs/2004.07202>) 
+ TENER: Adapting Transformer Encoder for Named Entity Recognition [arxiv](<https://arxiv.org/abs/1911.04474>) 



##### Contextualized Embeddings

语境向量-动态聚合某单词的上下文嵌入（即上下文向量），即在数据集中获取某单词的所有上下文嵌入实例，对其进行池化操作，将得到的向量结合当前位置的上下文信息形成新的词嵌入。不仅可以解决一词多义问题，还可以处理罕见词、拼写错误的问题。

+ Akbik, Alan, Tanja Bergmann, and Roland Vollgraf. "Pooled contextualized embeddings for named entity recognition." Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long and Short Papers). 2019.
+ Akbik, Alan, Duncan Blythe, and Roland Vollgraf. "Contextual string embeddings for sequence labeling." Proceedings of the 27th International Conference on Computational Linguistics. 2018.

##### Language Model

+ Sun, Jian, et al. "Chinese named entity identification using class-based language model." *Proceedings of the 19th international conference on Computational linguistics-Volume 1*. Association for Computational Linguistics, 2002.

  



##### Dependency

"Dependency-Guided LSTM-CRF for Named Entity Recognition" in EMNLP 2019. [code](<https://github.com/allanj/ner_with_dependency>) 



##### HMM

Daniel M Bikel, Scott Miller, ..., et al. Nymble: a high-performance learning name-finder, ACL 1997



##### CRF decode

+ Neural architectures for named entity recognition, Guillaume Lample, Miguel Ballesteros, Sandeep Subramanian, Kazuya Kawakami, and Chris Dyer. NAACL 2016. [arxiv](https://arxiv.org/abs/1603.01360) :star::star::star::star:

  a CRF layers to decode the tag sequence

+ Z.-X. Ye and Z.-H. Ling, “Hybrid semi-markov crf for neural sequence labeling,” in Proc. ACL, 2018, pp. 235–240.

  This approach adopts segments instead of words as the basic units for feature extraction and transition modeling. Word-level labels are utilized in deriving segment scores. Thus, this approach is able to leverage both word- and segment-level information for segment score calculation.

###### LSTM encode

- Bidirectional LSTM-CRF Models for Sequence Tagging, Zhiheng Huang, Wei Xu, Kai Yu, 2015, [arxiv](https://arxiv.org/abs/1508.01991) :star::star::star:

  a CRF layers to decode the tag sequence.

- End-to-end Sequence Labeling via Bi-directional LSTM-CNNs-CRF. Xuezhe Ma and Eduard Hovy. ACL 2016, pages 1064-1074. [PDF](http://www.cs.cmu.edu/~xuezhem/publications/P16-1101.pdf) [arXiv](http://arxiv.org/abs/1603.01354) [Bib](http://www.cs.cmu.edu/~xuezhem/bibs/P16-1101.bib) [code](https://github.com/XuezheMax/LasagneNLP) :star::star::star:

  a CRF layers to decode the tag sequence.

###### CNN encode



##### LSTM decode

+ Ashish Vaswani, Yonatan Bisk, Kenji Sagae, and Ryan Musa. 2016. Supertagging with lstms. In Proceedings of the NAACL international conference. pages 232–237.

  a LSTM layers to decode the tag sequence

+ Arzoo Katiyar and Claire Cardie. 2016. Investigating lstms for joint extraction of opinion entities and relations. In Proceedings of the 54th ACL international conference.

  a LSTM layers to decode the tag sequence



##### LAN (**L**abel **A**ttention **N**etwork) decode

+ Leyang Cui and Yue Zhang. 2019. Hierarchically-refined label attention network for sequence labeling. EMNLP-IJCNLP 2019. [code](<https://github.com/Nealcly/BiLSTM-LAN>) 



##### Pointer Networks (Reading Comprehension)

+ A Unified MRC Framework for Named Entity Recognition. Xiaoya Li, Jingrong Feng, Jiwei Li. [arxiv](<https://arxiv.org/abs/1910.11476>)  | [blog](<https://zhuanlan.zhihu.com/p/89019478>) 
+ F. Zhai, S. Potdar, B. Xiang, and B. Zhou, “Neural models for sequence chunking.” in Proc. AAAI, 2017, pp. 3365–3371.



#### Semi-supervised

+ David Nadeau. Semi-supervised named entity recognition: learning to recognize 100 entity types with little supervision [D]. 2007



#### Unsupervised



+ Etzioni, O., Cafarella, M., Downey, D., Popescu, A. M., Shaked, T., Soderland, S., ... & Yates, A. (2005). Unsupervised named-entity extraction from the web: An experimental study. *Artificial intelligence*, *165*(1), 91-134. :star::star::star::star:



##### DL-CoTrain/CoBoost

DL-Cotrain considers the entity mentions separately as unlabeled examples and predicts a type independently for each.



Michael Collins, Yoram Singer. Unsupervised models for named entity classification. EMNLP 1999

Michael Collins, Ranking algorithms for named-entity extraction: Boosting and the voted perceptron. ACL 2002



##### LabeledLDA

LabeledLDA groups together words across all mentions of an entity string, and infers a distribution over its possible types.



LabeledLDA models each entity string as a mixture of types rather than using a single hidden variable to represent the type of each mention. This allows information about an entity’s distribution over types to be shared across mentions, naturally handling ambiguous entity strings whose mentions could refer to different types.



+ Ritter, Alan, Sam Clark, and Oren Etzioni. "Named entity recognition in tweets: an experimental study." *Proceedings of the conference on empirical methods in natural language processing*. Association for Computational Linguistics, 2011. [paper](<https://homes.cs.washington.edu/~mausam/papers/emnlp11.pdf>) | [slide](<https://github.com/aritter/aritter.github.io/blob/master/twitter_ner.pptx>) | [code](<https://github.com/aritter/twitter_nlp>) :star::star::star::star:

  > we propose a distantly supervised approach which applies LabeledLDA (Ramage et al., 2009) to leverage large amounts of unlabeled data in addition to large dictionaries of entities gathered from Freebase, and combines information about an entity’s context across its mentions.
  >
  > 
  >
  > paper:
  >
  > Daniel Ramage, David Hall, Ramesh Nallapati, and Christopher D. Manning. 2009. Labeled lda: a supervised topic model for credit attribution in multi-labeled corpora. In Proceedings of the 2009 Conference on Empirical Methods in Natural Language Processing: Volume 1 - Volume 1, EMNLP ’09, pages 248–256, Morristown, NJ, USA. Association for Computational Linguistics.

  

+ Distantly Supervised Named Entity Recognition using Positive-Unlabeled Learning [code](<https://github.com/v-mipeng/LexiconNER>) 

+ 



+ 孙茂松, ... 中文姓名的自动辨识, 中文信息学报, 1995









