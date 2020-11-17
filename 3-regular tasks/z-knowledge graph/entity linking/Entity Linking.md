https://github.com/sebastianruder/NLP-progress/blob/master/english/entity_linking.md







## Challenge

+ for long tail and newly emerging <u>entities</u> that have few or no links associated with them.

+ how to decide/discriminate the unlinkable entity in sentence ?

  Unlinkable Mention Prediction of Entity Linking.

  method 1 - threshold (manual setting or as a parameter to learn in rank)

  method 2 - a filter classifier (binary)

  method 3 - combined (add Unlinkable as candidate in rank)

+ Short text entity linking vs. Long text entity linking



## Task

- *End-to-End*: processing a piece of text to extract the entities (i.e. Named Entity Recognition) and then disambiguate these extracted entities to the correct entry in a given knowledge base (e.g. Wikidata, DBpedia, YAGO).
- *Disambiguation-Only*: contrary to the first approach, this one directly takes gold standard named entities as input and only disambiguates them to the correct entry in a given knowledge base.



## Application





## Competition

+ the TAC-KBP track

  http://www.nist.gov/tac/about/index.html

  The Knowledge Base Population (KBP) track conducted as part of NIST Text Analysis Conference (TAC) is an international entity linking competition held every year since 2009. Entity linking is regarded as one of the two subtasks in this track.

+ Making Sense of Microposts 2016 - Named Entity rEcognition and Linking (NEEL) Challenge [site](http://microposts2016.seas.upenn.edu/challenge.html) 

  Overview of the EVALITA 2016 Named Entity rEcognition and Linking in Italian Tweets (NEEL-IT) Task [site](http://giusepperizzo.github.io/publications/Basile_Rizzo-2016neelit.pdf) 

+ NLP&CC 2013 - 中文微博实体链接 [site](http://tcci.ccf.org.cn/conference/2013/pages/page04_eva.html) 

+ CCKS 2019 百度实体链指技术比赛 [site](<https://ai.baidu.com/broad/leaderboard>) 

  [CCKS 2019 知识图谱评测竞赛总体报告](https://conference.bj.bcebos.com/ccks2019/eval/CCKS2019评测总体报告.pdf) 

  [CCKS 2019 知识图谱评测技术报告：实体、关系、事件及问答](<https://arxiv.org/ftp/arxiv/papers/2003/2003.03875.pdf>) 

  任务简介：

  传统的实体链指任务主要是针对长文档，长文档拥有在写的上下文信息能辅助实体的歧义消解并完成链指。

  针对中文短文本的实体链指存在很大的挑战，主要原因如下：
  （1）口语化严重，导致实体歧义消解困难；
  （2）短文本上下文语境不丰富，须对上下文语境进行精准理解；
  （3）相比英文，中文由于语言自身的特点，在短文本的链指问题上更有挑战。

  方法总结：

  主流做法是采用pipeline的方式，先进行NER再NED.

  NER主要实现方式有序列标注和半指针半标注两种，Bi-LSTM+CRF仍是序列标注采用最多的模型；比较创新的方式是通过半指针半标注的方式实现NER，即进行两次标注分别标注实体的开始位置和终止位置.

  NED则有rank和多分类两种实现方式，其中多分类是被采用最多的方法.

  开源代码：

  [1st](<https://github.com/1780041410/ccks_baidu_entity_link>) 

  > 实体识别 - 加入知识库的实体描述信息
  >
  > 1.利用知识库的实体名称和实体的别名信息构建实体名称字典。 2. 通过知识库的实体描述文本，利用 BERT 预训练模型，选取模型 CLS 位置的向量输出作为实体名称的 向量嵌入。 3. 通过字典匹配方式，得到短文本中候选实体。 4. 通过构建的BERT-ENE 模型对匹配的结果进行筛选。
  >
  > 实体消歧 - 
  >
  > 将其视为二分类问题，通过基于 BERT 的二分类模型对候选实体进行预测，然后对预测的概率进行排序，进而完成消歧任务。
  >
  > 

  [3th](<https://github.com/AlexYangLi/ccks2019_el>) 

  > 实体识别 - 加入 mention 库匹配信息
  >
  > 实体消歧 - 加入 mention 的位置信息

  [7th](<https://github.com/bojone/el-2019>) 

  

+ CCKS 2020 百度实体链指技术比赛 [site](<https://www.biendata.com/competition/ccks_2020_el/>) 

  任务简介：

  本评测任务在CCKS 2019面向中文短文本的实体链指任务的基础上进行了拓展与改进，主要改进包括以下几部分：
  （1）去掉实体识别，专注于中文短文本场景下的多歧义实体消歧技术；
  （2）增加对新实体（NIL实体）的上位概念类型判断；
  （3）对标注文本数据调整，增加多模任务场景下的文本源，同时调整了多歧义实体比例。





## Conference

+ [Entity Linking and Retrieval Tutorial](https://github.com/ejmeij/entity-linking-and-retrieval-tutorial) 2014
+ 



## STOA

+ <https://chinesenlp.xyz/#/zh/docs/entity_linking>
+ https://github.com/sebastianruder/NLP-progress/blob/master/chinese/chinese.md#entity-linking
+ https://github.com/sebastianruder/NLP-progress/blob/master/english/entity_linking.md
+ https://paperswithcode.com/task/entity-linking



## Scholars

+ 季姮 [heng ji](http://nlp.cs.rpi.edu/hengji.html) 

+ 

  

## Tools

- BLINK

  BLINK is a Python library for entity linking to a knowledge base (KB) that combines enterprise-search platform with state-of-the-art natural language understanding methods. In particular, BLINK contains three main components:

  named entity recognition (NER)
  candidate retrieval
  candidate ranking

  <https://github.com/facebookresearch/BLINK>

- YODIE: Yet another Open Data Information Extraction system [site](https://gate.ac.uk/applications/yodie.html)

- <https://github.com/clhisawolfman/chinese_entity_linking>



## Literature review

+ 知识图谱实体链接：一份“由浅入深”的综述 [site](https://mp.weixin.qq.com/s/vtj1HgDC2slsOw9DGoURCA) 



+ [Entity Discovery and Linking and Wikification Reading List](<http://nlp.cs.rpi.edu/kbp/2019/elreading.html>)
+ "Information Extraction and Knowledge Base Population", Invited course for the 10th Russian Summer School in Information Retrieval, 2016. [200 slides](http://nlp.cs.rpi.edu/ie2016.pptx) or [300 slides](http://nlp.cs.rpi.edu/ie2016_long.pptx).
+ Entity Linking with a Knowledge Base: Issues, Techniques, and Solutions, Wei Shen, Jianyong Wang, and Jiawei Han 2015, [paper](http://dbgroup.cs.tsinghua.edu.cn/wangjy/papers/TKDE14-entitylinking.pdf) :star::star::star:



## Paper

Paperlist:

http://blender.cs.illinois.edu/kbp/2020/elreading.html Heng Ji :star::star::star::star::star:

https://github.com/izuna385/Entity-Linking-Recent-Trends



### Bert

+ Investigating Entity Knowledge in BERT with Simple Neural End-To-End Entity Linking. [arxiv](<https://arxiv.org/abs/2003.05473>) 
+ 



+ *Zero-Shot Entity Linking by Reading Entity Descriptions*, ACL 2019, **Outstanding paper awards**, [paper](https://arxiv.org/abs/1906.07348) 



+ DeepType: Multilingual Entity Linking by Neural Type System Evolution, Jonathan Raiman, Olivier Raiman, AAAI 2018  [arxiv](https://arxiv.org/pdf/1802.01021.pdf) 

+ Neural Cross-Lingual Entity Linking, Avirup Sil, Gourab Kundu, Radu Florian, Wael Hamza, AAAI18, [arxiv](https://arxiv.org/abs/1712.01813) 

  细粒度上下文表示-只取mention所在句子的左边n个词和右边n个词

  句子级别上下文表示-取mention所在的整个句子

+ Analysis of Named Entity Recognition and Linking for Tweets, Leon Derczynski, Diana Maynard, Giuseppe Rizzo, Marieke van Erp, Genevieve Gorrell, Raphaël Troncy, Johann Petrak, Kalina Bontcheva, 2015, [arxiv](https://arxiv.org/abs/1410.7182) :star::star::star:

  

+ Joint Learning of the Embedding of Words and Entities for Named Entity Disambiguation, Ikuya Yamada, Hiroyuki Shindo, Hideaki Takeda, Yoshiyasu Takefuji, CoNLL 2016 [arxiv](https://arxiv.org/abs/1601.01343) :star:

  从词向量角度

+ Toward Socially-Infused Information Extraction: Embedding Authors, Mentions, and Entities, Yi Yang, Ming-Wei Chang, Jacob Eisenstein, EMNLP 2016, [arxiv](https://arxiv.org/abs/1609.08084v1) 

  For the task of entity linking in Twitter, Yang et al. (2016) employ the bilinear scoring function to learning the vector embedding of the entities, mentions, and context.

  

+ Collaborative Ranking: A Case Study on Entity Linking, Zheng Chen, Heng Ji, emnlp 2011 [arxiv](https://www.aclweb.org/anthology/D11-1071) 

  从文本排序角度



