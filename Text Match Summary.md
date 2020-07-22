more refer:

<https://en.wikipedia.org/wiki/Semantic_matching>

> The output of S-Match is a set of semantic correspondences called mappings attached with one of the following semantic relations: [disjointness](https://en.wikipedia.org/wiki/Disjointness) (⊥), [equivalence](https://en.wikipedia.org/wiki/Logical_equivalence) (≡), more specific (⊑) and less specific (⊒).

semantic equivalence identification





reference:<br>文本/语义 相似度计算 [site](https://zhuanlan.zhihu.com/p/43241696)

### Question

#### Short Text/Long Text

Short Text is sparse, noisy and ambiguous!

Example: 

short query in search

short answer in QA

Solution:

- short text

  word level encoding: Stack BiLSTM对token sequence进行encoding，将得到的hidden states做location-based attention，加权累加得到short text encoding

- long text

  sentence level encoding:对于多个句子，可以分层次做encoding。先用BiLSTM+attention做word level encoding、得到每个句子encoding的vector、按序组成sequence、再用BiLSTM+attention（这里的attention有很多花样可以玩）对这个sequence进行encoding、得到long text encoding

#### Symmetric in architecture

We always apply the concatenate operation when creating interactive features and this operation breaks symmetry.

How to grasp both symmetry ?

1) do it the concatenate operation twice. The first time is for [Sent1, Sent2] and the second time is for [Sent2, Sent1]. Finally, aggregate these two results.

2) double the training data, one for sentences pair <A, B> and the other for pair <B, A>. 

3) Alternatively, we can average the prediction of pair <A, B> and pair <B, A> in the testing phase.

refer:  [site](<https://towardsdatascience.com/simtext-2nd-solution-for-cikm-analyticup-2018-b3347e026e67>) | [code](<https://github.com/zake7749/CIKM-AnalytiCup-2018/blob/master/closer/model/sim_zoos.py>)



### Advantage and Disadvantage

- 实时计算

- 检索效率（召回）

  QA情景-从海量语料库中寻找最相似的Top-Q。

  - LSH（Locality-Sensitive Hashing）是一种不错的方法：

    基本思想：设计hash function对vector分桶、使原先 相邻/距离相近 的两个数据（vector）能够被hash到相同的桶内、具有相同的桶号。

    不同距离度量方式对应的hash function是不同的，比如常用的cosin distance对应的hash function是Random Hyperplanes，用随机的超平面进行编码，大概思路：随机取一个超平面（向量v），来用决定一个hash function：h(x) = 1 if v*x >0 else 0，如此、取三个超平面，就对应3个hash function、得到三个值，这三个值组成Bin index向量，就相当于把原来n维的数据降到三维，分别给它们一个序号如[0,0,0]=0、[0,0,1]=1、[0,1,1]=2...，这个序号就是桶号、就是hash 的值，其实就是个降维的过程。

    其他的：Jaccard距离对应min-hash、欧式距离对应P-stable hash，感兴趣的可以自己survey.

  - faiss

    https://github.com/facebookresearch/faiss

  - annoy

    https://github.com/spotify/annoy





### Application

搜索、问答



### Architecture

- 输入一对句子，然后输出一个0/1标签代表相似程度，也就是视为一个二分类问题

- 输入一个三元组“（句子A，跟A相似的句子，跟A不相似的句子）”，然后用triplet loss的做法解决

- 输入一个句子（该句子及其同义句为一个类别），即视为一个多分类问题，采用margin softmax loss训练

  more: <https://spaces.ac.cn/archives/5743/comment-page-1>



#### compare-aggregate

first exhaustively compares words from one sentence to another, then aggregates the comparison results to make final predictions. 

compare strategies :

multi-scale compare (at multiple levels of granularity)

...



aggregate strategies :

attentive 

max-pooling 

...




### Methods

#### Unsupervised

##### Lexical level (字面)

- **BOW + rewrite + distance computing**

1，改写：分词、清理停用词、保留主干词，对主干词做语义增强 -- 同义词/关联词补充，比如doc/sentence中有“美丽”、可以给它append上”漂亮“”俊秀“等词。

2，转为BOW，并根据业务先验和词性对token赋权。

3，计算两个词袋向量之间的距离，可以用cosin、jaccard等等。

- **topic model + distance computing**

1，使用topic model、如 LDA LSA PLSA 等对doc/sentence向量化

2，计算两个向量间的距离/相似度

- **average word vectors**

1，train 一个 word2vec

2，累加doc/sentence中各词的vector、求均值、作为文本的向量表示

3，计算两个向量间的距离/相似度

- **word2vec + Word Mover's Distance**

1，train 一个 word2vec

2，计算两个doc/sentence之间的WMD，可以简单理解成在相同语义空间下、doc1 travel 到 doc2 代价

##### Semantic level (语义)

- **language model + distance computing**

1，用相关语料train 一个 LM，可以是最简单的lstm的也可以是seq2seq with attention的，取lstm or encoder的最后一个time step的hidden state作为doc/sentence的向量表示

2，计算两个向量间的距离/相似度。能抓到词序间的关系、但最终效果好不好就...看命吧...

- **doc2vec**

1，对sentence/paragraph做embedding，gensim等工具中均有实现、原理也是街货了、不赘述了

2，计算两个向量间的距离/相似度。

- **其他方法**

如 基于句法的多成分细粒度分析 等等。

#### Supervised

##### Representation-based

###### representation

1. char/word vec

2. pre-trained vec



   + Seq2Seq

     doc1经过Seq2Seq获得不同decoder的候选结果，doc2经过encoder和attention的结果，计算两者的loss。

     `Seq2Seq模型本身是一个生成模型，但是我们把它用来计算句子之间的相似度，我们把它encoder和attention的结果和不同的候选做loss计算，把loss作为一种度量结果，loss越小代表输入和候选越接近。`

3. combined

4. ...



###### similarity

+ distance，即常用的距离度量，如cosin、dot 等等，但从我的经验来看这些方法效果都不理想，归因：从它们的公式来看、都是对应维相乘、并没有考虑不同维之间的交叉、也就是强制假设了各维之间是独立的、有局限，而且、各维相乘之后直接累加、即各维权重都是1、没有对不同维加权、也就是假设了各维重要性相同、也有些不妥。

+ metric learning

  a) 马氏距离、即学习一个矩阵M、使sim(v1, v2)=v1$*$M$*$v2 、它就优化了上述通用距离度量公式的不妥之处（M的对角线元素相当于给各维加权、非对角线元素相当于考虑了维度交叉）；

  b) 用DNN去学距离，相对于马氏距离DNN还多学习了非线性的距离关系，它的输入是[v1*v2, |v1-v2|...]，注意它的输入需要考虑“对称性”、因为输入的text是pair的、是无序的、此次输入[text1, text2]、下次就可能是[text2, text1]、所以v1-v2取了绝对值，输出范围就是0到1、典型的二分类。

+ 


##### Interaction-based









