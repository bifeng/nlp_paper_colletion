## Topics

### Reading Comprehension

### Sentence Summarization

#### sentence compression(句子压缩)

(Application: 商品标题压缩，资讯标题改写，PUSH消息改写...)

### Zero Pronoun Resolution

### Sentimental Analysis

情感推理、偏见/观点差异检测

[VADER Sentiment Analysis](https://github.com/cjhutto/vaderSentiment). VADER (Valence Aware Dictionary and sEntiment Reasoner) is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media, and works well on texts from other domains.

[Bias Statement Detector (BSD)](https://github.com/cjhutto/bsd) computationally detects and quantifies the degree of bias in sentence-level text of news stories.

### Adversarial Learning

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

### Transfer Learning (Domain)

### Natural Language Inference (Reasoning)

### Multi-Task Learning

==Notes==: The NLP progress largely contribute by amounts of data, which benefits in two forms. <br>First, limited of labeled data for supervised learning, but mainly in written (standard) language (not spoken language), can not transfer to other scenes.<br>Second, amounts of unlabeled data for word embedding used as pre-training models, such as word2vec, fasttext, elmo, bert and so on, transfer the general knowledge to other scenes. <br>But, even for that, the progress in vertical field still difficult to move forward.  

## Methods

### Graph based

### Transition based

### Representation Learning

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

The ACL 2018 paper "Sharp Nearby, Fuzzy Far Away: How Neural Language Models Use Context"<br>https://github.com/urvashik/lm-context-analysis

Does sentence embedding learned from RNNs captrue the syntactic information?

MSc project: Inferring Sentence Features from Sentence Embeddings<br>https://github.com/jonvet/thesis

[哈工大车万翔：自然语言处理中的深度学习模型是否依赖于树结构？-2015-10-15](https://mp.weixin.qq.com/s?__biz=MzIxMjAzNDY5Mg==&mid=209300177&idx=1&sn=4d24467ee27da15ae05effaa0ded9332&scene=2&srcid=1015LyJAMxAtArMzdyKyIRHh&from=timeline&isappinstalled=0#rd)

### Lexical and Neural Networks Combined

+ Linguistically Regularized LSTM for Sentiment Classification, ACL 2017 [paper](http://www.aclweb.org/anthology/P17-1154) | [code](http://coai.cs.tsinghua.edu.cn/publications/)

+ Semantically Conditioned LSTM-based Natural Language Generation for Spoken Dialogue Systems, EMNLP 2015 [arxiv](https://arxiv.org/abs/1508.01745)
  + [x] semantically
  + [x] natural language generation

  ???



## Literature Review

- Recent Trends in Deep Learning Based Natural Language Processing, last revised 25 Nov 2018. [arxiv](https://arxiv.org/abs/1708.02709)

  ???

- Methods for Sentence Compression Emily Pitler 2010-11-5 [paper](https://repository.upenn.edu/cgi/viewcontent.cgi?referer=https://cn.bing.com/&httpsredir=1&article=1975&context=cis_reports)

  - [x] sentence compression

  ???

- 

## Paper

[Papers with Code](https://paperswithcode.com/)

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

### 2018

+ Contextual Augmentation: Data Augmentation by Words with Paradigmatic Relations. NAACL-HLT, 2018. [arxiv](https://arxiv.org/pdf/1805.06201.pdf) | [code](https://github.com/pfnet-research/contextual_augmentation)

  - [x] Context-aware

  ???

+ Neural Relation Extraction via Inner-Sentence Noise Reduction and Transfer Learning EMNLP 2018 [arxiv](https://arxiv.org/abs/1808.06738)

  - [x] Relation Extraction
  - [x] Transfer Learning

  ???

+ Graph Convolution over Pruned Dependency Trees Improves Relation Extraction EMNLP 2018 [arxiv](https://arxiv.org/abs/1809.10185) | [code](https://github.com/qipeng/gcn-over-pruned-trees)

  - [x] Relation Extraction

  ???

+ Neural natural language inference models enhanced with external knowledge, ACL 2018

  - [x] natural language inference
  - [x] knowledge 

  ???

+ Improving language understanding with unsupervised learning, OpenAI 2018

  - [x] language model

  ???

+ BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding, Google 2018

  - [x] language model

  ???



---

### 2017

+ Adversarial Examples for Evaluating Reading Comprehension Systems, EMNLP 2017 - Outstanding Paper Award. [arxiv](https://arxiv.org/abs/1707.07328) | [code](https://github.com/robinjia/adversarial-squad) | [Robin Jia](http://stanford.edu/~robinjia/)

  - [x] Reading Comprehension

  - [x] Adversarial Learning

    ???

+ Attention-over-Attention Neural Networks for Reading Comprehension ACL 2017 [arxiv](https://arxiv.org/abs/1607.04423)

  - [x] Reading Comprehension

    https://stanfordnlp.github.io/coqa/

    https://rajpurkar.github.io/SQuAD-explorer/

  ???

+ Generating and Exploiting Large-scale Pseudo Training Data for Zero Pronoun Resolution, Ting Liu, Yiming Cui, et al. , ACL2017 [arxiv](https://arxiv.org/abs/1606.01603) | [slides](http://ymcui.github.io/pdf/ACL2017_ZP_slides.pdf) | [Yiming Cui](http://ymcui.github.io)

  - [x] zero pronoun resolution
  - [x] data scarcity
  - [x] transfer learning

+ Using millions of emoji occurrences to learn any-domain representations for detecting sentiment, emotion and sarcasm, Bjarke Felbo, et al., EMNLP 2017 [arxiv](https://arxiv.org/abs/1708.00524) | [code](https://github.com/bfelbo/DeepMoji)

  - [x] sentimental analysis
  - [x] data scarcity
  - [x] transfer learning

+ 

---

### 2015

+ Teaching Machines to Read and Comprehend, Karl Moritz Hermann, et al. , NIPS 2015 [nips](http://papers.nips.cc/paper/5945-teaching-machines-to-read-and-comprehend)
  - [x] reading comprehension
  - [x] data scarcity
+ A Neural Attention Model for Abstractive Sentence Summarization, Rush Facebook [code](https://github.com/facebookarchive/NAMAS) 
  - [x] sentence summarization



---

### 2012

+ Sentence Compression with Semantic Role Constraints, ACL 2012 [paper](http://aclweb.org/anthology//P/P12/P12-2068.pdf)

  - [x] sentence compression

  ???





---



### 2008

- Global Inference for Sentence Compression: An Integer Linear Programming Approach [code](https://github.com/cnap/sentence-compression)

  - [x] sentence compression

  ???



### 2000

- Sentence Reduction for Automatic Text Summarization [paper](https://www.aclweb.org/anthology/A/A00/A00-1043.pdf)

  - [x] sentence compression

  ???

