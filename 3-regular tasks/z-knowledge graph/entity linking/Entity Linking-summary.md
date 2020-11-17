## Question

1. 无法一次性处理一个句子多个实体或关系的情形

   如果一个句子含有多个实体，则该句子必须与知识库的实体匹配多次

2. 



## methods

### end to end

将实体链指任务，放在实体识别上，即在实体识别中新增实体的类型标签。



An alternative approach is to compute the score for each entity candidate using distributed vector representations of the entities, mentions, and context. Each of the vector embeddings can be learned from an end-to-end objective, or pre-trained on unlabeled data.

+ Pretrained entity embeddings can be obtained from an existing knowledge base (Bordes et al., 2011, 2013), or by running a word embedding algorithm such as WORD2VEC on the text of Wikipedia, with hyperlinks substituted for the anchor text.
+ The embedding of the mention x can be computed by averaging the embeddings of the words in the mention (Yang et al., 2016), or by the compositional techniques described in section 14.8 (Distributed representations of multiword units - phrases, sentences, and paragraphs).
+ The embedding of the context c can also be computed from the embeddings of the words in the context.

refer: Natural Language Processing Jacob Eisenstein-10-15-2018



### two stage model

#### embedding

1）训练多义词实体向量，计算实体相似度

2）

#### text match

文本匹配：计算当前实体的文本与候选实体的文本匹配程度

#### text classify

文本分类：根据候选实体的类型及其文本训练分类模型，计算当前实体的文本所指类型。

#### text rank

文本排序

##### Non-collective approaches

Non-collective approaches, which resolve one mention at each time relying on prior popularity, context similarity, and other local features with supervised models.

##### Collective approaches

Collective approaches, which disambiguate a set of relevant mentions simultaneously by leveraging the global topical
coherence between entities through graph-based approaches.





##### features for ranking

![features_for_ranking](https://github.com/bifeng/daily_book_notes/raw/master/resource/features_for_ranking.png)

refer - "Information Extraction and Knowledge Base Population", Invited course for the 10th Russian Summer School in Information Retrieval, 2016. [200 slides](http://nlp.cs.rpi.edu/ie2016.pptx) or [300 slides](http://nlp.cs.rpi.edu/ie2016_long.pptx).



##### pairwise ranking loss function

Usunier et al. (2009) define a general ranking error function, ...

we want a high rank for the correct entity, and we want it to be separated from other entities by a substantial margin. We therefore define the margin-augmented rank, ...



For each instance, a hinge loss is computed from the ranking error associated with this margin-augmented rank, and the violation of the margin constraint, ...



WARP (Weston et al., 2011) approximate ranking loss...



refer: Natural Language Processing Jacob Eisenstein-10-15-2018





## ideas

+ sentences - entities matrix for negative sampling

  sentences看成items，entities看成users，根据训练集构建matrix

+ NMF for entity linking 

  利用上述sentences - entities matrix，学习Neural Matrix Factorization模型

+ 是否可以优先确定句子中最可能的实体，再加入该实体信息预测下一个实体

  实体依次链接到知识库





