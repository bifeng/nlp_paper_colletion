## Challenges

It is an open and exciting question how much of the work of understanding can be done at the level of words.





### Polysemy (一词多义)

solution:

1. training a contextual word vectors, such as ELMo. Solved totally?
2. each word token’s type vector is passed into a function that transforms it based on the words in its nearby context, giving a new version of the word vector, now specific to the token in its particular context.



### Word vectors are biased

corpus-derived word vectors will reflect what's in the data, such as cultural biases.

Methods for detecting and correcting unwanted associations is an active area of research (Bolukbasi et al., 2016; Caliskan et al., 2017). The advent of contextual word vectors offers some possibility of new ways to avoid unwanted generalization from distributional patterns.



### Long tailed





### Multi-dimension features

How to embedding multi-dimension features ?

参考《embedding in recommendation》





## Summary

1. 本质上是降维技术（在低维空间捕获高维空间重要结构）

   PCA\matrix factorization\word2vec...

2. 将稀疏高维的特征空间（不具有可计算的性质？这是什么空间呢？）映射到低维向量空间，从而获得该空间中向量的性质，比如欧式空间的向量加减乘除、复空间的旋转等.

3. 网络结构的各种优化本质上也是对 embedding 运算的优化

   







## Methods (learn)

### Unsupervised embedding







### Supervised embedding

Paper:

TagSpace - Weston, J.; Chopra, S.; and Adams, K. 2014. # tagspace:Semantic embeddings from hashtags. In Proceedings of the 2014 Conference on Empirical Methods in Natural Language Processing (EMNLP), 1822–1827.

>  learning an embedding of word and tag!

fastText - Joulin, A.; Grave, E.; Bojanowski, P.; and Mikolov, T. 2016. Bag of tricks for efficient text classification. arXiv preprint arXiv:1607.01759.

> learning an embedding of word!







## Methods (calculate)

运算法则？



拼接

线性组合



### 点积

内积 - such as MF, FM, SVD++, IPNN

外积 - such as ONCF, OPNN

马哈达 - such as CIN, xdeepFM, NNCF

双线性 - such as FiBiNet



### 交叉

Bit-wise - such as WDL, DeepFM, DCN

Element-wise - such as CF, NFM

Vector-wise - such as FNN, PNN, CIN, xdeepFM

Gp-wise - such as Gwen.

























