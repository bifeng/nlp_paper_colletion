### Challenge

+ document level



### Related Task

+ 人脸识别、图像检索、重识别（相似度）

  首先训练分类模型，再将分类层丢弃，仅使用模型提取特征，然后通过特征之间的距离判断样本的相似度。

+ 机器翻译的评价系统

  Meteor Universal: Language Specific Translation Evaluation for Any Target Language, [paper](<https://www.aclweb.org/anthology/W14-3348>) 

  BLEU



### Competition

+ Kaggle - Quora Question Pairs

+ ### [LCQMC:A Large-scale Chinese Question Matching Corpus](https://www.aclweb.org/anthology/C18-1166/) 

+ ### [ATEC学习赛：NLP之问题相似度计算](https://dc.cloud.alipay.com/index#/topic/intro?id=8) 

+ ### [CCKS 2018 微众银行智能客服问句匹配大赛](https://biendata.com/competition/CCKS2018_3/leaderboard/) 

+ CIKM AnalytiCup 2018 - a task for determining short text similarities

  https://tianchi.aliyun.com/competition/entrance/231661/information

  [2th](https://github.com/zake7749/CIKM-AnalytiCup-2018) 

+ CHIP2019任务二 平安医疗科技疾病问答迁移学习比赛

  

  

### Datasets

+ PAWS: Paraphrase Adversaries from Word Scrambling

  This dataset contains 108,463 human-labeled and 656k noisily labeled pairs that feature the importance of modeling structure, context, and word order information for the problem of paraphrase identification.

  <https://github.com/google-research-datasets/paws>

+ https://nlp.stanford.edu/projects/snli/

+ <https://github.com/pkucoli/PKU-Paraphrase-Bank>

+ 





### STOA

https://github.com/sebastianruder/NLP-progress/blob/master/english/semantic_textual_similarity.md

https://aclweb.org/aclwiki/Paraphrase_Identification_(State_of_the_art)

https://paperswithcode.com/task/paraphrase-identification/latest

https://paperswithcode.com/task/text-matching



### Literature Review

+ 文本匹配相关方向打卡点总结 - 夕小瑶

  



### Paper

- Simple and Effective Text Matching with Richer Alignment Features, ACL 2019 [code](<https://github.com/alibaba-edu/simple-effective-text-matching>) 

  

- ESIM

  Enhanced LSTM for Natural Language Inference, Qian Chen, Xiaodan Zhu, Zhenhua Ling, Si Wei, Hui Jiang, Diana Inkpen, ACL 2017 [arxiv](https://arxiv.org/abs/1609.06038) 

  Sequential Attention-based Network for Noetic End-to-End Response Selection, Chen Qian and Wang Wen, CoRR 2019, [arxiv](http://arxiv.org/abs/1901.02609) [code](<https://github.com/alibaba/esim-response-selection>) 

  

- Bilateral Multi-Perspective Matching for Natural Language Sentences, Zhiguo Wang, Wael Hamza, Radu Florian, IJCAI 2017 [arxiv](https://arxiv.org/abs/1702.03814) 



- A Compare-Aggregate Model for Matching Text Sequences, Shuohang Wang, Jing Jiang [arxiv](<https://arxiv.org/abs/1611.01747>) :star::star:

  

- Ji, Y. and Eisenstein, J. (2013) [Discriminative Improvements to Distributional Sentence Similarity](http://www.aclweb.org/anthology/D/D13/D13-1090.pdf), *Proceedings of Empirical Methods in Natural Language Processing (EMNLP 2013)*, Seattle, Washington, USA, pp. 891--896

- 



#### keyword

+ Keyword-Attentive Deep Semantic Matching [github](<https://github.com/DataTerminatorX/Keyword-BERT>) 

  blog: 远离送命题: 问答系统中语义匹配的『杀手锏』[site](https://mp.weixin.qq.com/s/_QY2EhB-TiBcb5q0379McQ) Keyword-BERT
  (原创 穆文MuWen 数据挖掘机养成记)



#### based on graph

+ Random Walks for Text Semantic Similarity, Daniel Ramage, Anna N. Rafferty, and Christopher D. Manning [paper](<https://nlp.stanford.edu/pubs/wordwalk-textgraphs09.pdf>) 

  



#### document level

+ Matching Article Pairs with Graphical Decomposition and Convolutions, ACL 2019 [code](<https://github.com/BangLiu/ArticlePairMatching>) 

  



### Tools

- <https://github.com/ChenglongChen/tensorflow-DSMM>

- <https://github.com/pengming617/text_matching> 

- <https://github.com/WenRichard/compare-aggregate>

  

- 

