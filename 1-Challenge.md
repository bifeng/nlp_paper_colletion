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



### Lexical is necessary ?



A Structural Probe for Finding Syntax in Word Representations. NAACL 2019 [paper](https://nlp.stanford.edu/pubs/hewitt2019structural.pdf) | [code](<https://github.com/john-hewitt/structural-probes/>) 

Jumelet, Zuidema & Hupkes (2019): *Analysing Neural Language Models: Contextual Decomposition Reveals Default Reasoning in Number and Gender Assignment* [code](<https://github.com/i-machine-think/diagnnose>) 

**Linguistic Knowledge and Transferability of Contextual Representations**. [Nelson F. Liu](https://homes.cs.washington.edu/~nfliu/), [Matt Gardner](https://allenai.org/team/mattg/), [Yonatan Belinkov](http://people.csail.mit.edu/belinkov/), Matthew E. Peters, and [Noah A. Smith](http://www.cs.cmu.edu/~nasmith). In *Proceedings of the Conference of the North American Chapter of the Association for Computational Linguistics* (**NAACL 2019**), June 2019.

Dissecting Contextual Word Embeddings: Architecture and Representation, Matthew E. Peters, Mark Neumann, Luke Zettlemoyer, Wen-tau Yih, EMNLP 2018 [arxiv](https://arxiv.org/abs/1808.08949v1) 

From Word to Sense Embeddings: A Survey on Vector Representations of Meaning, Jose Camacho-Collados, Mohammad Taher Pilehvar, JAIR 2018 [arxiv](https://arxiv.org/abs/1805.04032) 

词向量的效果取决于训练任务（语料）：在泛语料中训练的词向量，可能无法区分词语的反义关系（否定和肯定、积极与消极等）、上下位关系等。但在垂直领域或特定任务中可以使词向量表达更准确，如通过情感分类任务训练的词向量，可以区分“讨厌”和“喜欢”。

Uncovering Divergent Linguistic Information in Word Embeddings with Lessons for Intrinsic and Extrinsic Evaluation, Mikel Artetxe, Gorka Labaka, Iñigo Lopez-Gazpio, Eneko Agirre, CoNLL 2018, Best Paper Award, [arxiv](https://arxiv.org/abs/1809.02094) | [code](https://github.com/artetxem/uncovec) <br>摘要：随着词嵌入最近取得成功，有人认为根本不存在词的理想表征，因为不同的模型倾向于捕捉不同且往往互不兼容的方面，如语义/句法和相似性/相关性。本论文展示了每个词嵌入模型捕获的信息多于直接显现的信息。线性转换无需任何外部资源就能调整模型的相似度阶，因此能够调整模型以在这些方面获得更好的结果，这为词嵌入编码不同的语言信息提供了新的视角。此外，我们还探索了内、外部评估的关系，我们在下游任务中的变换效果在无监督系统中的效果优于监督系统。

Sharp Nearby, Fuzzy Far Away: How Neural Language Models Use Context, Urvashi Khandelwal, He He, Peng Qi, Dan Jurafsky, ACL 2018, [arxiv](https://arxiv.org/abs/1805.04623) | [code](https://github.com/urvashik/lm-context-analysis) 

LSTMs Exploit Linguistic Attributes of Data, ACL 2018, [code](https://github.com/nelson-liu/LSTMs-exploit-linguistic-attributes) 

Does sentence embedding learned from RNNs captrue the syntactic information?

MSc project: Inferring Sentence Features from Sentence Embeddings, [code](https://github.com/jonvet/thesis) 

When Are Tree Structures Necessary for Deep Learning of Representations?
Jiwei Li, Minh-Thang Luong, Dan Jurafsky, Eudard Hovy [arxiv](<https://arxiv.org/abs/1503.00185>) :star: :star::star: ​ 

[哈工大车万翔：自然语言处理中的深度学习模型是否依赖于树结构？-2015-10-15](https://mp.weixin.qq.com/s?__biz=MzIxMjAzNDY5Mg==&mid=209300177&idx=1&sn=4d24467ee27da15ae05effaa0ded9332&scene=2&srcid=1015LyJAMxAtArMzdyKyIRHh&from=timeline&isappinstalled=0#rd) 



Deep Biaffine Attention for Neural Dependency Parsing. ICLR 2017



#### Lexical and Neural Networks Combined

- Semantically Conditioned LSTM-based Natural Language Generation for Spoken Dialogue Systems, Tsung-Hsien Wen, Milica Gasic, Nikola Mrksic, Pei-Hao Su, David Vandyke, Steve Young, EMNLP 2015 [arxiv](https://arxiv.org/abs/1508.01745) | [code](https://github.com/hit-computer/SC-LSTM)

  - [x] semantically
  - [x] natural language generation

- Linguistically Regularized LSTM for Sentiment Classification, Qiao Qian, Minlie Huang, Jinhao Lei, Xiaoyan Zhu, ACL 2017 [paper](http://www.aclweb.org/anthology/P17-1154) | [code](http://coai.cs.tsinghua.edu.cn/publications/) | [Review](https://github.com/pochih/SA-papers/blob/master/reviews/Linguistically-Regularized-LSTM-for-Sentiment-Classification.md) 

- Linguistically-Informed Self-Attention for Semantic Role Labeling, Emma Strubell, Patrick Verga, Daniel Andor, David Weiss, Andrew McCallum, Google, EMNLP 2018 - Best long paper 1/2. [arxiv](https://arxiv.org/abs/1804.08199v1) | [code](https://github.com/strubell/LISA)

  摘要：当前最先进的语义角色标记（SRL）使用深度神经网络而没有明确的语言特征。但是，之前的工作表明，语法树可以显着改善SRL解码，这表明通过显式语法建模可以提高准确性。在这项工作中，我们提出了基于语言学的self-attention（LISA）：一种神经网络模型，它将multi-head self-attention与多任务学习相结合，包括依赖解析，词性标注，谓词检测和语义角色标记。与先前需要大量预处理来准备语言特征的模型不同，LISA可以仅使用原始的token，对序列进行一次编码，来同时执行多个预测任务。语法信息被用来训练一个attention head来关注每个token语法上的父节点。如果已经有高质量的语法分析，则可以在测试时进行有益的注入，而无需重新训练我们的SRL模型。在CoNLL-2005 SRL数据集上，LISA在谓词预测、word embedding任务上比当前最好的算法在F1值上高出了2.5（新闻专线数据）和3.5以上（其他领域数据），减少了约10%的错误。在ConLL-2012英文角色标记任务上，我们的方法也获得了2.5 F1值得提升。LISA同时也比当前最好的基于上下文的词表示学习方法（ELMo）高出了1.0的F1（新闻专线数据）和多于2.0的F1（其他领域数据）。





