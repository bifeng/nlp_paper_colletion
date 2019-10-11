more refer:<br>http://cs224d.stanford.edu/lecture_notes/LectureNotes1.pdf<br>http://cs224d.stanford.edu/lecture_notes/LectureNotes2.pdf<br>http://web.stanford.edu/class/cs224n/lectures/lecture2.pdf<br>http://web.stanford.edu/class/cs224n/lectures/lecture3.pdf<br>

paper:<br>Efficient Estimation of Word Representations in Vector Space, 2013 [arxiv](https://arxiv.org/abs/1301.3781)
Distributed Representations of Words and Phrases and their Compositionality, 2013 [arxiv](https://arxiv.org/abs/1310.4546)
word2vec Explained: Deriving Mikolov et al.’s Negative-Sampling Word-Embedding Method, 2014 [arxiv](https://arxiv.org/abs/1402.3722)

reference:<br>动手学深度学习-[第十六课 词向量（word2vec）](https://discuss.gluon.ai/t/topic/4180)<br>http://zh.gluon.ai/chapter_natural-language-processing/word2vec.html<br>https://en.wikipedia.org/wiki/Word2vec

#### Keyphrases

+ objective function, network structure, training steps. 

#### 两个模型

跳字模型（skip-gram）:
假设基于某中心词来生成它在文本序列前后的背景词。
每个词语，既可能是中心词也可能是背景词，所以对应地有两个向量，在训练时，根据该词语的作用选择相应的向量。

连续词袋模型（continuous bag of words，简称 CBOW）:
假设基于某中心词在文本序列前后的背景词来生成该中心词。

##### Softmax
Softmax主要考虑背景词可能是词典中的任意词，所以分母包含所有可能情况，而且这种归一化可以得到合理的概率。
难点：计算量大

##### 近似训练方法
负采样（negative sampling）
负采样修改了目标函数，条件概率被近似表示为正样本与负样本的概率乘积，其中当前窗口的背景词和中心词同时出现作为正样本，随机选取的噪声词不出现在中心词的背景窗口作为负样本。

层序softmax（hierarchical softmax）
层序softmax也修改了目标函数，条件概率被近似表示为中心词的词向量与（二叉树）根节点到叶子结点（背景词）路径上的非叶子结点向量的乘积。

##### 参数
Context window: 
According to the authors' note, the recommended value is 10 for skip-gram and 5 for CBOW.
negative samples: 
For skip-gram models trained in medium size corpora, with 50 dimensions, a window size of 15 and 10 negative samples seems to be a good parameter setting.



#### Summary
1. wor2vec本质上是基于马尔科夫假设的bigram language model.

2. CBOW smoothes over a lot of the distributional information (by treating an entire context as one observation). For the most part, this turns out to be a useful thing for <u>smaller datasets</u>. However, skip-gram treats each context-target pair as a new observation, and this tends to do better when we have <u>larger datasets</u>.

3. for training the skip-gram model, negative sample results in faster training and better vector representations for frequent words, compared to more complex hierarchical softmax.

4. **Negative Sampling** is a simplified version of **Noise Contrastive Estimation**

   **NCE guarantees approximation to softmax, Negative Sampling doesn’t** 

   [Mnih and Teh (2012)](https://www.cs.toronto.edu/~amnih/papers/ncelm.pdf) reported that 25 noise samples are sufficient to match the performance of the regular softmax, with an expected speed-up factor of about 45.

   For more information, see: 

   Sebastian Rudder’s “On word embeddings - Part 2: Approximating the Softmax” 

   Chris Dyer’s “Notes on Noise Contrastive Estimation and Negative Sampling”

5. 









