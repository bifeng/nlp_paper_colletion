### Awesome

https://github.com/Jiakui/awesome-bert





#### reg

http://fancyerii.github.io/2019/03/20/bert-reg/

https://github.com/google-research/bert/issues/74



#### rank

https://github.com/nyu-dl/dl4marco-bert

#### multi-task



#### Visualization

A Multiscale Visualization of Attention in the Transformer Model
Jesse Vig

<https://github.com/jessevig/bertviz>



### Literature Review

#### A Primer in BERTology: What we know about how BERT works

A Primer in BERTology: What we know about how BERT works. Anna Rogers, Olga Kovaleva, Anna Rumshisky. 2020.02 [arxiv](https://arxiv.org/abs/2002.12327) 







### Paperlist

+ Bert Evolution

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/bert_evolution.jpg" width="600" height="400" alt="bert_evolution"></img>
</div>


+ 8篇论文梳理BERT相关模型进展与反思 [site](<https://www.msra.cn/zh-cn/news/features/bert>) 



### paper

+ Yoav Goldberg. Assessing BERT’s syntactic abilities, 2019. arXiv:1901.05287.

+ BERT has a Mouth, and It Must Speak: BERT as a Markov Random Field Language Model, Alex Wang, Kyunghyun Cho, 2019 [arxiv](https://arxiv.org/abs/1902.04094) | [code](https://github.com/nyu-dl/bert-gen)  

+ To Tune or Not to Tune? Adapting Pretrained Representations to Diverse Tasks, Matthew Peters, Sebastian Ruder, Noah A. Smith, 2019 [arxiv](https://arxiv.org/abs/1903.05987) 

+ Linguistic Knowledge and Transferability of Contextual Representations-1903.08855

+ Distilling Task-Specific Knowledge from BERT into Simple Neural Networks, Raphael Tang, Yao Lu, Linqing Liu, Lili Mou, Olga Vechtomova, Jimmy Lin, [arxiv](https://arxiv.org/abs/1903.12136) 

  

+ How to Fine-Tune BERT for Text Classification?-1905.05583 [arxiv](https://arxiv.org/pdf/1905.05583.pdf)

+ Simple BERT Models for Relation Extraction and Semantic Role Labeling-1904.05255 [arxiv](https://arxiv.org/pdf/1904.05255.pdf) 

+ Pretraining-Based Natural Language Generation for Text Summarization-1902.09243

+ Toward Fast and Accurate Neural Chinese Word Segmentation with Multi-Criteria Learning [arxiv](https://arxiv.org/pdf/1903.04190.pdf) 

  BERT + model compression + multi-criterial learing 

#### Interpretability

<http://web.stanford.edu/class/cs224n/slides/cs224n-2020-lecture20-interpretability.pdf>



##### A structural probe for finding syntax in word representations

John Hewitt and Christopher D Manning. A structural probe for finding syntax in word representations. Association for Computational Linguistics, 2019.



A structural probe for finding syntax in word representations

<https://nlp.stanford.edu/~johnhew/structural-probe.html>



|      | syntactic                               | semantic | bert              | method                                                  |
| ---- | --------------------------------------- | -------- | ----------------- | ------------------------------------------------------- |
|      | d​e​p​en​d​e​n​c​y​ p​ar​s​e​ ​t​r​ee:heavy_check_mark: |          | context embedding | structural probe(a single global linear transformation) |
|      |                                         |          |                   |                                                         |



dependency parse tree

**the square of the distance** between context embeddings is roughly proportional to tree distance in the dependency parse. 





##### Visualizing and Measuring the Geometry of BERT

Visualizing and Measuring the Geometry of BERT. Andy Coenen, Emily Reif, Ann Yuan, Been Kim, Adam Pearce, Fernanda Viégas, Martin Wattenberg 2019.06 [arxiv](https://arxiv.org/abs/1906.02715) 





|      | syntactic                               | semantic    | bert               | method                                                      |
| ---- | --------------------------------------- | ----------- | ------------------ | ----------------------------------------------------------- |
|      | dependency parse tree:heavy_check_mark: |             | context embedding  | structural probe + PCA                                      |
|      |                                         |             |                    |                                                             |
|      | d​e​pe​n​d​e​n​cy​ ​re​l​a​tio​n:heavy_check_mark:   |             | attention matrices | attention probe (binary classifier + multiclass classifier) |
|      |                                         |             |                    |                                                             |
|      |                                         | word senses | context embedding  | word sense disambiguation probe + UMAP                      |



An attention probe:

It is a task for a pair of tokens, ($token_i$ , $token_j$ ) where the input is a model-wide attention vector formed by concatenating the entries $a_{ij}$ in every attention matrix from every attention head in every layer. The goal is to classify a given relation between the two tokens.



Word sense disambiguation probe: a probe following Hewitt and Manning’s methodology

Loss is, roughly, defined as the difference between the average cosine similarity between embeddings of words with different senses, and that between embeddings of the same sense. However, we clamped the cosine similarity terms to within ±0.1 of the pre-training averages for same and different senses.



word-sense disambiguation:

nearest-neighbor classifier





结论：

1. 为什么这些syntactic/semantic可以存在于一个表示之中？

   可能对于不同的成分，存在不同的子空间 —— 一个子空间表示syntactic，另一个子空间表示semantic

   a vector encodes both syntax and semantics, but in separate complementary subspaces (see Appendix 6.7 for details). —— 分析两个子空间的奇异值表明，Semantic and syntactic are orthogonal to each other。

2. 为什么存在不同的子空间？

   作者推测——the internal geometry of BERT may be broken into multiple linear subspaces, with separate spaces for different syntactic and semantic information.

3. 还存在哪些有意义的子空间？

4. 如何转换到相应的子空间？

   squared Euclidean distance ——> dependecy parse tree

   ? ——> word senses

5. geometry of parse tree embedding

   从数学上解释了为什么需要squared Euclidean distance。

   由于Euclidean space - 无法编码tree，作者提出Pythagorean embedding

   The simplicity of Pythagorean tree embeddings, as well as the fact that they may be approximated by a simple random model, suggests they may be a generally useful alternative to approaches to tree embeddings that require hyperbolic geometry.

6. attention将所有邻居都考虑进去了，而不考虑语义的边界

   Our results show how a token’s embedding in a sentence may systematically differ from the embedding for the same token in the same sentence concatenated with a non-sequitur（非词义修饰词，如连词and）. This points to a potential failure mode for attention-based models: tokens do not necessarily respect semantic boundaries when attending to neighboring tokens, but rather indiscriminately absorb meaning from all neighbors

   



##### others

+ Revealing the Dark Secrets of BERT [paper](<https://www.aclweb.org/anthology/D19-1445.pdf>) [blog](<https://text-machine-lab.github.io/blog/2020/bert-secrets/>) 
  
+ BERT Rediscovers the Classical NLP Pipeline
  Ian Tenney, Dipanjan Das, Ellie Pavlick.  ACL 2019 [arxiv](<https://arxiv.org/abs/1905.05950>) 

+ What do you learn from context? Probing for sentence structure in contextualized word representations.

  Ian Tenney, Patrick Xia, Berlin Chen, Alex Wang, Adam Poliak, R. Thomas McCoy, Najoung Kim, Benjamin Van Durme, Samuel R. Bowman, Dipanjan Das, and Ellie Pavlick. ICLR 2019. https://openreview.net/forum?id=SJzSgnRcKX 
  
  > edge probing



+ Asking without Telling: Exploring Latent Ontologies in Contextual Representations



### blogs

+ <http://jalammar.github.io/illustrated-bert/>
+ [8篇论文梳理BERT相关模型进展与反思](<https://www.msra.cn/zh-cn/news/features/bert>) 
+ 从语言模型看Bert的善变与GPT的坚守 [site](https://mp.weixin.qq.com/s/zqlWx3e4LOJ3_Zy2DEbCjw) 
  穆文MuWen 数据挖掘机养成记 2019-05-20

### code

https://github.com/google-research/bert

https://github.com/huggingface/pytorch-pretrained-BERT



multi-label classification:<br>https://github.com/yuanxiaosc/Entity-Relation-Extraction







### datasets

[multilingual](https://github.com/google-research/bert/blob/master/multilingual.md) Chinese

The entire Wikipedia dump for each language (excluding user and talk pages) was taken as the training data for each language.

we performed <u>exponentially smoothed weighting</u> of the data during pre-training data creation (and WordPiece vocab creation). So, high-resource languages like English will be under-sampled, and low-resource languages like Icelandic will be over-sampled.



### excise

- bert for ranking
- bert for text generation
- 