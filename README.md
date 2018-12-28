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

Uncovering Divergent Linguistic Information in Word Embeddings with Lessons for Intrinsic and Extrinsic Evaluation, CoNLL 2018, Best Paper Award, [arxiv](https://arxiv.org/abs/1809.02094) | [code](https://github.com/artetxem/uncovec) <br>摘要：随着词嵌入最近取得成功，有人认为根本不存在词的理想表征，因为不同的模型倾向于捕捉不同且往往互不兼容的方面，如语义/句法和相似性/相关性。本论文展示了每个词嵌入模型捕获的信息多于直接显现的信息。线性转换无需任何外部资源就能调整模型的相似度阶，因此能够调整模型以在这些方面获得更好的结果，这为词嵌入编码不同的语言信息提供了新的视角。此外，我们还探索了内、外部评估的关系，我们在下游任务中的变换效果在无监督系统中的效果优于监督系统。

The ACL 2018 paper "Sharp Nearby, Fuzzy Far Away: How Neural Language Models Use Context", [code](https://github.com/urvashik/lm-context-analysis)

Does sentence embedding learned from RNNs captrue the syntactic information?

MSc project: Inferring Sentence Features from Sentence Embeddings, [code](https://github.com/jonvet/thesis)

[哈工大车万翔：自然语言处理中的深度学习模型是否依赖于树结构？-2015-10-15](https://mp.weixin.qq.com/s?__biz=MzIxMjAzNDY5Mg==&mid=209300177&idx=1&sn=4d24467ee27da15ae05effaa0ded9332&scene=2&srcid=1015LyJAMxAtArMzdyKyIRHh&from=timeline&isappinstalled=0#rd)

### Lexical and Neural Networks Combined

+ Semantically Conditioned LSTM-based Natural Language Generation for Spoken Dialogue Systems, EMNLP 2015 [arxiv](https://arxiv.org/abs/1508.01745) | [code](https://github.com/hit-computer/SC-LSTM)

  - [x] semantically
  - [x] natural language generation

  ???

+ Linguistically Regularized LSTM for Sentiment Classification, ACL 2017 [paper](http://www.aclweb.org/anthology/P17-1154) | [code](http://coai.cs.tsinghua.edu.cn/publications/) | [Review](https://github.com/pochih/SA-papers/blob/master/reviews/Linguistically-Regularized-LSTM-for-Sentiment-Classification.md)

  ???

+ Linguistically-Informed Self-Attention for Semantic Role Labeling,Google, EMNLP 2018 - Best long paper 1/2. [arxiv](https://arxiv.org/abs/1804.08199v1) | [code](https://github.com/strubell/LISA)

  摘要：当前最先进的语义角色标记（SRL）使用深度神经网络而没有明确的语言特征。但是，之前的工作表明，语法树可以显着改善SRL解码，这表明通过显式语法建模可以提高准确性。在这项工作中，我们提出了基于语言学的self-attention（LISA）：一种神经网络模型，它将multi-head self-attention与多任务学习相结合，包括依赖解析，词性标注，谓词检测和语义角色标记。与先前需要大量预处理来准备语言特征的模型不同，LISA可以仅使用原始的token，对序列进行一次编码，来同时执行多个预测任务。语法信息被用来训练一个attention head来关注每个token语法上的父节点。如果已经有高质量的语法分析，则可以在测试时进行有益的注入，而无需重新训练我们的SRL模型。在CoNLL-2005 SRL数据集上，LISA在谓词预测、word embedding任务上比当前最好的算法在F1值上高出了2.5（新闻专线数据）和3.5以上（其他领域数据），减少了约10%的错误。在ConLL-2012英文角色标记任务上，我们的方法也获得了2.5 F1值得提升。LISA同时也比当前最好的基于上下文的词表示学习方法（ELMo）高出了1.0的F1（新闻专线数据）和多于2.0的F1（其他领域数据）。

+ Gaussian Mixture Latent Vector Grammars, ACL 2018 [arxiv](https://arxiv.org/abs/1805.04688) | ([Supplementary material](http://sist.shanghaitech.edu.cn/faculty/tukw/acl18-sup.pdf))([Slides](http://sist.shanghaitech.edu.cn/faculty/tukw/acl18-slides.pdf))([Code](https://github.com/zhaoyanpeng/lveg))

  该论文将传统的上下文无关文法与深度学习中的符号向量化思想相结合，提出了一种全新的“隐向量文法”.



## Literature Review

- Recent Trends in Deep Learning Based Natural Language Processing, last revised 25 Nov 2018. [arxiv](https://arxiv.org/abs/1708.02709)

  ???

- Analysis Methods in Neural Language Processing: A Survey, 2019 TACL. [arxiv](https://arxiv.org/abs/1812.08951) | [code](https://github.com/boknilev/nlp-analysis-methods)

  - [x] Lexical and Neural Networks Combined
  - [x] Adversarial Learning

- Adversarial Examples: Attacks and Defenses for Deep Learning, 2018 [arxiv](https://arxiv.org/abs/1712.07107v1)

  - [x] Adversarial Learning

  ???

- Methods for Sentence Compression Emily Pitler 2010-11-5 [paper](https://repository.upenn.edu/cgi/viewcontent.cgi?referer=https://cn.bing.com/&httpsredir=1&article=1975&context=cis_reports)

  - [x] sentence compression

  ???

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

