## Topics

### Reading Comprehension

### Zero Pronoun Resolution

### Sentimental Analysis



## Challenges

### Data Scarcity

### Transfer Learning (Domain)

### Natural Language Inference

### Multi-Task Learning

==Notes==: The NLP progress largely contribute by amounts of data, which benefits in two forms. <br>First, limited of labeled data for supervised learning, but mainly in written (standard) language (not spoken language), can not transfer to other scenes.<br>Second, amounts of unlabeled data for word embedding used as pre-training models, such as word2vec, fasttext, elmo, bert and so on, transfer the general knowledge to other scenes. <br>But, even for that, the progress in vertical field still difficult to move forward.  

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

CoNLL 2018 Shared Task: Multilingual Parsing from Raw Text to Universal Dependencies<br> [result](https://lindat.mff.cuni.cz/repository/xmlui/handle/11234/1-2885) | [paper]()



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

+ 

---

### 2017

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
+ 