refer:<br>[扯扯 Semi-hard Negative Samples](http://www.shuang0420.com/2018/03/17/%E6%89%AF%E6%89%AF%20Semi-hard%20Negative%20Samples/) <br>[如何解决数据不平衡问题？](https://mp.weixin.qq.com/s/orf_UaDFCKIaYjslbItcfQ) - 目标检测中的不平衡问题的进展



### error analysis

These bad case or error maybe the evidence to the negative sample problem in the training datasets.



### methods



#### semi-hard negative sampling 

For the network to learn well, it is useful to not feed random wrong answers to it, but those that are "hard". That means answers that are wrong, but close to question in the cosine distance. But if you feed only the hardest questions to the network, it fails to converge, it is just "too hard". Instead people have found that using "semi-hard negative samples" - answers, which are further than the right answer, but still within the margin - works best. 

https://github.com/tambetm/allenAI



#### online hard example mining (OHEM)

在线困难样例挖掘：目标检测的另一个问题是类别不平衡，图像中大部分的区域是不包含目标的，而只有小部分区域包含目标。此外，不同目标的检测难度也有很大差异，绝大部分的目标很容易被检测到，而有一小部分目标却十分困难。OHEM和Boosting的思路类似，其根据损失值将所有候选区域进行排序，并选择损失值最高的一部分候选区域进行优化，使网络更关注于图像中更困难的目标。此外，为了避免选到相互重叠很大的候选区域，OHEM对候选区域根据损失值进行NMS。



### application

word2vec

ranking models

computer vision

#### papers

+ FaceNet: A Unified Embedding for Face Recognition and Clustering, CVPR 2015 [arxiv](https://arxiv.org/abs/1503.03832)

  Triplet Loss



+ Distributed representations of words and phrases and their compositionality, NIPS, 2013

  Popularity-based sampling by CBOW can ensure more connections between positive and negative words, since popular words may appear frequently to build connections with lots of positive words.

+ Wordrank: Learning word embeddings via robust ranking. CoRR, 2015

+ Improving negative sampling for word representation using self-embedded features, CORR 2017.

  An adaptive sampler was proposed to strategically select those negative words that have larger inner products with contextual words than positive words.

+ Approximating Word Ranking and Negative Sampling for Word Embedding, IJCAI 2018, [paper](https://www.ijcai.org/proceedings/2018/0569.pdf) | [code](https://github.com/ouououououou/OptRank)

  A ranking model with the optimization in both positive word ranking and negative word sampling.


+ The Impact of Negative Samples on Learning to Rank, 2017 [paper](http://ceur-ws.org/Vol-2007/LEARNER2017_short_1.pdf)

  i) train a ranking model on the full dataset and we use it to rank the query-document pairs of the same dataset;

  ii) select a given fraction of the top-ranked negative samples, i.e., label = 0, together with all the positive ones, i.e., label > 0.

  iii) varying the fraction of negatives sampling, such as {5%, 10%, 20%, 40%}. For the similarity distribution between pairs of documents in the negative class, the model will be effective in discriminating among the negative examples.

+ Strategy of the Negative Sampling for Training Retrieval-Based Dialogue Systems, 2018 [arxiv](https://arxiv.org/abs/1811.09785)

  Change the responses distribution and to choose responses for negative samples
  from the transformed distribution.
