refer: Contextual Word Representations: A Contextual Introduction, Noah A. Smith, February 2019, [arxiv](https://arxiv.org/pdf/1902.06006.pdf) 





## Question

1. The connection between word embedding and matrix factorization ?

   Paper:

   Neural word embedding as implicit matrix factorization. O Levy, Y Goldberg



## Application

refer:

<https://developers.google.com/machine-learning/crash-course/embeddings/categorical-input-data>



1. 具有稀疏特征的场景

   比如某个文本对应的词语，该词语相对于词库是稀疏的

   （label是中心词或背景词）

   比如某个用户对应的物品，该物品相对于物料是稀疏的

   比如某个用户对应的产品类别，该类别相对于产品总数是稀疏的

   （label是用户对应的label）

   比如某个用户对应的产品列表，该产品列表相对于产品总数是稀疏的

   （label是用户对应的label）





## Challenges

It is an open and exciting question how much of the work of understanding can be done at the level of words.





### Polysemy (一词多义)

solution:

1. training a contextual word vectors, such as ELMo. Solved totally?
2. each word token’s type vector is passed into a function that transforms it based on the words in its nearby context, giving a new version of the word vector, now specific to the token in its particular context.



### Word vectors are biased

corpus-derived word vectors will reflect what's in the data, such as cultural biases.

Methods for detecting and correcting unwanted associations is an active area of research (Bolukbasi et al., 2016; Caliskan et al., 2017). The advent of contextual word vectors offers some possibility of new ways to avoid unwanted generalization from distributional patterns.

## Literature Review

+ Pre-trained Models for Natural Language Processing: A Survey

  [blog](<https://mp.weixin.qq.com/s/85sEuJpGa0iegPNCoF-SRQ>) 

+ 《Embeddings in Natural Language Processing Theory and Advances in Vector Representation of Meaning》

  > In general, it has been shown that word embeddings are
  > not actually recovering general relations, but rather some specific ones for which
  > similarity or proximity in the vector space plays an important role [Levy et al.,
  > 2014, Linzen, 2016, Rogers et al., 2017, Nissim et al., 2019]. For instance,
  > Bouraoui et al. [2018] shows how word embeddings can capture relations such
  > us superlative or capital of but then other relations cannot be retrieve by simple
  > arithmetic operations from word embeddings. For a more detailed overview of
  > the properties of word analogies, we would recommend the work of Allen and
  > Hospedales [2019].
  >
  > Analogies Explained: Towards Understanding Word Embeddings. Carl Allen, Timothy Hospedales

  

## Paper

paperlist:

<http://hyperbolicdeeplearning.com/papers/>

+ Theory
  
+ word2vec, node2vec, graph2vec, X2vec: Towards a Theory of Vector Embeddings of Structured Data. Martin Grohe 
  
  https://sigmod2020.org/pods_keynote.shtml :star::star::star::star::star:





+ Encoding word order in complex embeddings. Benyou Wang, Donghao Zhao, Christina Lioma, Qiuchi Li, Peng Zhang, Jakob Grue Simonsen ICLR 2020 spotlight paper
  https://openreview.net/forum?id=Hke-WTVtwr
+ Poincare Embedding for Learning Hierarchical Representations. Maximilian Nickel, Douwe Kiela. 



+ Representation Tradeoffs for Hyperbolic Embeddings
  Christopher De Sa, Albert Gu, Christopher Ré, Frederic Sala [arxiv](<https://arxiv.org/abs/1804.03329>) [code](<https://github.com/HazyResearch/hyperbolics>) 

> Hyperbolic embeddings offer excellent quality with few dimensions when embedding hierarchical data structures like synonym or type hierarchies.

+ Learning Mixed-Curvature Representations in Product Spaces [paper](https://openreview.net/pdf?id=HJxeWnCcF7) 

> The quality of the representations achieved by embeddings is determined by how well the geometry of the embedding space matches the structure of the data. Euclidean space has been the workhorse for embeddings; recently hyperbolic and spherical spaces have gained popularity due to their ability to better embed new types of structured data—such as hierarchical data—but most data is not structured so uniformly. 

+ Analogies Explained: Towards Understanding Word Embeddings. Carl Allen, Timothy Hospedales



+ word2vec Explained: deriving Mikolov et al.'s negative-sampling word-embedding method. Y Goldberg, O Levy



## Blog

+ Linear algebraic structure of word meanings

  <http://www.offconvex.org/2016/07/10/embeddingspolysemy/>

+ Word Embeddings: Explaining their properties

  <https://www.offconvex.org/2016/02/14/word-embeddings-2/>



## Tools

+ https://github.com/MaxwellRebo/awesome-2vec

+ StarSpace 

  <https://github.com/facebookresearch/StarSpace>

  Learning embeddings for classification, retrieval and ranking.

+ word2vec

+ doc2vec

+ item2vec







