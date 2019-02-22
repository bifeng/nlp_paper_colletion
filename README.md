**论文入选要求：<br>1. 好的方法 - 开创性或突破性方法<br>2. 好的应用 - 提供解决问题的全新视角<br>**

[google scholar](https://scholar.google.com/schhp?hl=zh-CN) 

## Topics

### Sentence Summarization

#### sentence compression(句子压缩)

(Application: 商品标题压缩，资讯标题改写，PUSH消息改写...)

### Zero Pronoun Resolution

### Sentimental Analysis

情感推理、偏见/观点差异检测

[VADER Sentiment Analysis](https://github.com/cjhutto/vaderSentiment). VADER (Valence Aware Dictionary and sEntiment Reasoner) is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media, and works well on texts from other domains.

[Bias Statement Detector (BSD)](https://github.com/cjhutto/bsd) computationally detects and quantifies the degree of bias in sentence-level text of news stories.

### Relation Extraction

## Challenges

### Context-aware(Prior) and World Knowledge 

#### Grammar

##### Linguistically/Semantically

WordNet

#### Language Model

Word Embedding

#### Knowledge Graph

### Data Scarcity

### Representation Learning

#### Transfer Learning

### Natural Language Inference (Reasoning)

### Natural Language Generation

Machine Translation

Fluency and Coherency

## Methods

### Graph based

### Transition based

### Deep Reinforcement Learning

Deep Reinforcement Learning for NLP ACL 2018 [ppt](http://www.cs.ucsb.edu/~william/DRL4NLP.html) 

## Trends

2017 - ...<br>2018 - 神经网络、注意机制、表示学习、语义和知识...

+ 表示学习

  1. 词汇表示学习

     融合多种信息的、任务或领域特异的、跨语言、消歧的词汇表示学习

  2. 句子表示学习

## Progress

The progress in Natural Language Processing (NLP), including the datasets and the current state-of-the-art for the most common NLP tasks.<br>https://github.com/sebastianruder/NLP-progress<br>https://github.com/Kyubyong/nlp_tasks

## Competition

CoNLL

CoNLL 评测主要是学术界主导，所以内容多偏向自然语言处理的基础研究问题。

http://universaldependencies.org/conll17/<br><http://universaldependencies.org/conll18/>

CoNLL 2017 Shared Task: Multilingual Parsing from Raw Text to Universal Dependencies<br>[result](https://lindat.mff.cuni.cz/repository/xmlui/handle/11234/1-2424) | [paper](http://www.petrovi.de/data/conll17.pdf)

---

CoNLL 2018 Shared Task: Multilingual Parsing from Raw Text to Universal Dependencies<br> [result](https://lindat.mff.cuni.cz/repository/xmlui/handle/11234/1-2885) | [paper](http://universaldependencies.org/conll18/proceedings/pdf/K18-2001.pdf)

[HIT-SCIR (Harbin)  - Towards Better UD Parsing: Deep Contextualized Word Embeddings, Ensemble, and Treebank Concatenation](http://aclweb.org/anthology/K18-2005)

[Uppsala (Uppsala) - Universal Word Segmentation: Implementation and Interpretation](https://transacl.org/ojs/index.php/tacl/article/viewFile/1446/315) [code](https://github.com/yanshao9798/segmenter)

---



## Personally Interest

1. What's the bottleneck of deep learning in NLP ? (deep parsing ?)

2. How to explain the good generalization of deep learning in NLP ?

3. Is there implicit or explicit way to incorporate linguistic knowledge in deep learning ?

   (Deep Learning is task oriented, and there is no need to explicit represent linguistic knowledge ?)

4. What's linguistics hypothesis of deep learning ? (generative linguistics(formal linguistics), functional linguistics and cognitive linguistics)

5. What's the different between deep learning and statistical based method ? (shallow parsing ?)

6. Deep learning pro end-to-end, Linguistics pro-representation, do we have to choose ? Better together?


1. Do corpus-based lexicography methods scale up?
2. Are they too manually intensive?
3. If so, could we use machine learning methods
   - to speed up manual methods?
4. Just as statistical parsers learn syntactic rules: S -> NP VP
   - Can we learn valency?
   - Collocations (搭配) ?
   - Typical predicate argument relations (谓词论元关系)?
5. 

refer: [Minsky, Chomsky & Deep Nets](https://stu.cs.tsinghua.edu.cn/wiki/images/4/45/2018-10-21_CCL2018_Ken.pdf)

### Question

From Word to Sense Embeddings: A Survey on Vector Representations of Meaning, Jose Camacho-Collados, Mohammad Taher Pilehvar, JAIR 2018 [arxiv](https://arxiv.org/abs/1805.04032) 

词向量的效果取决于训练任务（语料）：在泛语料中训练的词向量，可能无法区分词语的反义关系（否定和肯定、积极与消极等）、上下位关系等。但在垂直领域或特定任务中可以使词向量表达更准确，如通过情感分类任务训练的词向量，可以区分“讨厌”和“喜欢”。

Uncovering Divergent Linguistic Information in Word Embeddings with Lessons for Intrinsic and Extrinsic Evaluation, Mikel Artetxe, Gorka Labaka, Iñigo Lopez-Gazpio, Eneko Agirre, CoNLL 2018, Best Paper Award, [arxiv](https://arxiv.org/abs/1809.02094) | [code](https://github.com/artetxem/uncovec) <br>摘要：随着词嵌入最近取得成功，有人认为根本不存在词的理想表征，因为不同的模型倾向于捕捉不同且往往互不兼容的方面，如语义/句法和相似性/相关性。本论文展示了每个词嵌入模型捕获的信息多于直接显现的信息。线性转换无需任何外部资源就能调整模型的相似度阶，因此能够调整模型以在这些方面获得更好的结果，这为词嵌入编码不同的语言信息提供了新的视角。此外，我们还探索了内、外部评估的关系，我们在下游任务中的变换效果在无监督系统中的效果优于监督系统。

Sharp Nearby, Fuzzy Far Away: How Neural Language Models Use Context, Urvashi Khandelwal, He He, Peng Qi, Dan Jurafsky, ACL 2018, [arxiv](https://arxiv.org/abs/1805.04623) | [code](https://github.com/urvashik/lm-context-analysis)

Does sentence embedding learned from RNNs captrue the syntactic information?

MSc project: Inferring Sentence Features from Sentence Embeddings, [code](https://github.com/jonvet/thesis)

[哈工大车万翔：自然语言处理中的深度学习模型是否依赖于树结构？-2015-10-15](https://mp.weixin.qq.com/s?__biz=MzIxMjAzNDY5Mg==&mid=209300177&idx=1&sn=4d24467ee27da15ae05effaa0ded9332&scene=2&srcid=1015LyJAMxAtArMzdyKyIRHh&from=timeline&isappinstalled=0#rd)

### Lexical and Neural Networks Combined

+ Semantically Conditioned LSTM-based Natural Language Generation for Spoken Dialogue Systems, Tsung-Hsien Wen, Milica Gasic, Nikola Mrksic, Pei-Hao Su, David Vandyke, Steve Young, EMNLP 2015 [arxiv](https://arxiv.org/abs/1508.01745) | [code](https://github.com/hit-computer/SC-LSTM)

  - [x] semantically
  - [x] natural language generation

+ Linguistically Regularized LSTM for Sentiment Classification, Qiao Qian, Minlie Huang, Jinhao Lei, Xiaoyan Zhu, ACL 2017 [paper](http://www.aclweb.org/anthology/P17-1154) | [code](http://coai.cs.tsinghua.edu.cn/publications/) | [Review](https://github.com/pochih/SA-papers/blob/master/reviews/Linguistically-Regularized-LSTM-for-Sentiment-Classification.md) 

+ Linguistically-Informed Self-Attention for Semantic Role Labeling, Emma Strubell, Patrick Verga, Daniel Andor, David Weiss, Andrew McCallum, Google, EMNLP 2018 - Best long paper 1/2. [arxiv](https://arxiv.org/abs/1804.08199v1) | [code](https://github.com/strubell/LISA)

  摘要：当前最先进的语义角色标记（SRL）使用深度神经网络而没有明确的语言特征。但是，之前的工作表明，语法树可以显着改善SRL解码，这表明通过显式语法建模可以提高准确性。在这项工作中，我们提出了基于语言学的self-attention（LISA）：一种神经网络模型，它将multi-head self-attention与多任务学习相结合，包括依赖解析，词性标注，谓词检测和语义角色标记。与先前需要大量预处理来准备语言特征的模型不同，LISA可以仅使用原始的token，对序列进行一次编码，来同时执行多个预测任务。语法信息被用来训练一个attention head来关注每个token语法上的父节点。如果已经有高质量的语法分析，则可以在测试时进行有益的注入，而无需重新训练我们的SRL模型。在CoNLL-2005 SRL数据集上，LISA在谓词预测、word embedding任务上比当前最好的算法在F1值上高出了2.5（新闻专线数据）和3.5以上（其他领域数据），减少了约10%的错误。在ConLL-2012英文角色标记任务上，我们的方法也获得了2.5 F1值得提升。LISA同时也比当前最好的基于上下文的词表示学习方法（ELMo）高出了1.0的F1（新闻专线数据）和多于2.0的F1（其他领域数据）。




## Literature Review

- Recent Trends in Deep Learning Based Natural Language Processing, Tom Young, Devamanyu Hazarika, Soujanya Poria, Erik Cambria, last revised 25 Nov 2018. [arxiv](https://arxiv.org/abs/1708.02709) 

- Analysis Methods in Neural Language Processing: A Survey, Yonatan Belinkov, James Glass, 2019 TACL. [arxiv](https://arxiv.org/abs/1812.08951) | [code](https://github.com/boknilev/nlp-analysis-methods) 

  - [x] Lexical and Neural Networks Combined
  - [x] Adversarial Learning

  


## Paper notes

[NLP Tasks](https://github.com/Kyubyong/nlp_tasks) 

[丕子 paperlist](https://github.com/lipiji/App-DL) 

[papernote](https://github.com/xwzhong/papernote) 

[NLP-Papers](https://github.com/llhthinker/NLP-Papers) 



[定期论文阅读](https://github.com/dantezhao/paper-notes) 

[问题讨论](https://github.com/dantezhao/data-group) 

[nlp-reading-group](https://github.com/clulab/nlp-reading-group) 



[Papers with Code](https://paperswithcode.com/) 



## Paper

COLING - 欧洲 - 关注语言规律、模型分析（可解释性研究）

[ACL](https://aclweb.org/aclwiki/Main_Page) - 北美

NAACL - 北美

EMNLP - 

---

2018 - Highlights

+ [COLING2018见闻](http://ws.nju.edu.cn/blog/2018/09/coling2018%E8%A7%81%E9%97%BB/)

  [tutorial](http://coling2018.org/wp-content/uploads/2018/08/coling18-tutorial.pdf)

  Why are you telling me this? Relevance & informativity in language processing.  [slides](http://coling2018.org/wp-content/uploads/2018/08/rohde-coling.pdf)

  Practical Parsing for Downstream Applications. [tutorial](http://coling2018.org/wp-content/uploads/2018/08/coling18-tutorial.pdf)

+ ACL 2018 [Highlights](http://ruder.io/acl-2018-highlights/)

+ NAACL-HLT 2018 [Highlights](http://ruder.io/highlights-naacl-2018/)

+ EMNLP 2018 [Highlights](http://ruder.io/emnlp-2018-highlights/)

---

### chinese

- Shallow Semantic Parsing of Chinese, HLT-NAACL, 2004, Sun, Honglin，Jurafsky, Daniel [paper](http://www.aclweb.org/anthology/N04-1032) 
- Chinese Word Segmentation: Another Decade Review (2007-2017), [arxiv](http://export.arxiv.org/abs/1901.06079) 
- Analogical Reasoning on Chinese Morphological and Semantic Relations, ACL 2018. [paper](http://aclweb.org/anthology/P18-2023) | [code](https://github.com/Embedding/Chinese-Word-Vectors) 
- 

### data augmentation

+ Conditional BERT Contextual Augmentation, Xing Wu, Shangwen Lv, Liangjun Zang, Jizhong Han, Songlin Hu, 201812, [arxiv](https://arxiv.org/abs/1812.06705) 
+ Contextual Augmentation: Data Augmentation by Words with Paradigmatic Relations. Sosuke Kobayashi, NAACL-HLT, 2018. [arxiv](https://arxiv.org/pdf/1805.06201.pdf) | [code](https://github.com/pfnet-research/contextual_augmentation) 


### pre-training word embedding

- Improving language understanding with unsupervised learning, OpenAI 2018
  - [x] language model

- BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding, Jacob Devlin, Ming-Wei Chang, Kenton Lee, Kristina Toutanova, Google 2018
  - [x] language model
- 

### pronoun resolution

+ Generating and Exploiting Large-scale Pseudo Training Data for Zero Pronoun Resolution, Ting Liu, Yiming Cui, et al. , ACL2017 [arxiv](https://arxiv.org/abs/1606.01603) | [slides](http://ymcui.github.io/pdf/ACL2017_ZP_slides.pdf) | [Yiming Cui](http://ymcui.github.io) 

  - [x] data scarcity
  - [x] transfer learning 


### relation extraction

- Graph Convolution over Pruned Dependency Trees Improves Relation Extraction, Yuhao Zhang, Peng Qi, Christopher D. Manning, EMNLP 2018 [arxiv](https://arxiv.org/abs/1809.10185) | [code](https://github.com/qipeng/gcn-over-pruned-trees) 



### sentence compression

- Language as a Latent Variable: Discrete Generative Models for Sentence Compression, Yishu Miao, Phil Blunsom, EMNLP 2016 [arxiv](https://arxiv.org/abs/1609.07317) 
- Sentence Compression as Tree Transduction, Trevor Anthony Cohn, Mirella Lapata, 2009 [arxiv](https://arxiv.org/abs/1401.5693) 

- Global Inference for Sentence Compression: An Integer Linear Programming Approach James Clarke，Mirella Lapata 2008 [code](https://github.com/cnap/sentence-compression) 

- Sentence Reduction for Automatic Text Summarization, Hongyan Jing 2000 [paper](https://www.aclweb.org/anthology/A/A00/A00-1043.pdf) 
- 
- A Multi-task Learning Approach for Improving Product Title Compression with User Search Log Data, Jingang Wang, Junfeng Tian, Long Qiu, Sheng Li, Jun Lang, Luo Si, Man Lan, AAAI 2018 [arxiv](https://arxiv.org/abs/1801.01725) 

### sentence summarization

- A Neural Attention Model for Abstractive Sentence Summarization, Alexander M. Rush, Sumit Chopra, Jason Weston, Facebook, EMNLP 2015 [code](https://github.com/facebookarchive/NAMAS) 

### sentimental analysis

+ Using millions of emoji occurrences to learn any-domain representations for detecting sentiment, emotion and sarcasm, Bjarke Felbo, et al., EMNLP 2017 [arxiv](https://arxiv.org/abs/1708.00524) | [code](https://github.com/bfelbo/DeepMoji) 

  - [x] data scarcity
  - [x] transfer learning
+ VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media, CJ Hutto & [Eric Gilbert's](http://eegilbert.org/) [social media](http://comp.social.gatech.edu/) (ICWSM-14). Ann Arbor, MI, June 2014. <br>supplement: [data set](http://comp.social.gatech.edu/papers/hutto_ICWSM_2014.tar.gz) [code (github)](https://github.com/cjhutto/vaderSentiment) [python package](https://pypi.python.org/pypi/vaderSentiment) 

### natural language inference

#### text match/paraphrase identification/text entailment

- Enhanced LSTM for Natural Language Inference, [Qian Chen](http://home.ustc.edu.cn/~cq1231/index.html), Xiaodan Zhu, Zhenhua Ling, Si Wei, Hui Jiang, Diana Inkpen. *ACL (2017)* [arxiv](https://arxiv.org/abs/1609.06038) | [code](https://github.com/lukecq1231/nli) 

+ A Decomposable Attention Model for Natural Language Inference, Ankur P. Parikh, Oscar Täckström, Dipanjan Das, Jakob Uszkoreit, EMNLP 2016 [arxiv](https://arxiv.org/abs/1606.01933) 
+ Learning Natural Language Inference with LSTM, Shuohang Wang, Jing Jiang, 2016, [arxiv](https://arxiv.org/abs/1512.08849) | [code](https://github.com/shuohangwang/SeqMatchSeq)  
+ Convolutional neural network architectures for matching natural language sentences, B Hu, Z Lu, H Li, Q Chen - Advances in neural information processing systems, 2014 [paper](http://papers.nips.cc/paper/5550-convolutional-neural-network-architectures-for-matching-natural-language-sentences) 
+ 



### Stance detection

https://github.com/sebastianruder/NLP-progress/blob/master/english/stance_detection.md

- Combating Fake News: A Survey on Identification and Mitigation Techniques, Karishma Sharma, Feng Qian, He Jiang, Natali Ruchansky, Ming Zhang, Yan Liu, ACM 2019, [arxiv](https://arxiv.org/abs/1901.06437) 
- DeClarE: Debunking Fake News and False Claims using Evidence-Aware Deep Learning, Kashyap Popat, Subhabrata Mukherjee, Andrew Yates, Gerhard Weikum, EMNLP 2018 [arxiv](https://arxiv.org/abs/1809.06416) 
- Hutto, C.J. (2015). Computationally Detecting and Quantifying the Degree of Bias in Sentence-Level Text of News Stories. Second International Conference on Human and Social Analytics (HUSO-15). Barcelona, Spain 2015. [code](https://github.com/cjhutto/bsd) 
- 