refer:<br>[扯扯 Semi-hard Negative Samples](http://www.shuang0420.com/2018/03/17/%E6%89%AF%E6%89%AF%20Semi-hard%20Negative%20Samples/)

### error analysis

These bad case or error maybe the evidence to the negative sample problem in the training datasets.



### methods



#### semi-hard negative sampling 

For the network to learn well, it is useful to not feed random wrong answers to it, but those that are "hard". That means answers that are wrong, but close to question in the cosine distance. But if you feed only the hardest questions to the network, it fails to converge, it is just "too hard". Instead people have found that using "semi-hard negative samples" - answers, which are further than the right answer, but still within the margin - works best. 

https://github.com/tambetm/allenAI

### application

word2vec

ranking models

computer vision

#### papers

+ FaceNet: A Unified Embedding for Face Recognition and Clustering, CVPR 2015 [arxiv](https://arxiv.org/abs/1503.03832)

  Triplet Loss

+ 