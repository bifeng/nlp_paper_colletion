### Summary

+ decision list (Yarowsky 95)

+ distant supervision



### Application

1. Language models
2. Word sense disambiguation
3. Name entity recognition
4. Word classes







### paper

+ Unsupervised Data Augmentation, Qizhe Xie, Zihang Dai, Eduard Hovy, Minh-Thang Luong, Quoc V. Le, [arxiv](https://arxiv.org/abs/1904.12848) 

  data-level smoothness

  

  https://www.reddit.com/r/MachineLearning/comments/bixuz9/r_unsupervised_data_augmentation/?depth=2

  it is a good idea to try simple augmentations such as replacing words with random words though these augmentations are not the best ones. Randomly replacing words can lead to descent improvements in our experiments.

  It has also led to improvements in machine translation (see SwitchOut: an Efficient Data Augmentation Algorithm for Neural Machine Translation).

  

  We did try using synonyms using the synsets information in nltk and the nearest neighbor of word embeddings, but it provided limited improvements in our preliminary experiments. The problem is that the augmented sentences are not diverse enough.

  

  TF-IDF based word replacing works better for DBPedia where some local words are more important.

  

  Back translation work better for IMDb, Yelp-2, Yelp-5, Amazon-2, Amazon-5 where the global semantics is important. 

  

  https://www.reddit.com/r/MachineLearning/comments/bixuz9/r_unsupervised_data_augmentation/em76lev/

  [Mixture Models for Diverse Machine Translation: Tricks of the Trade (Shen et al., 2019)](https://arxiv.org/abs/1902.07816) 

  [Understanding Back-Translation at Scale](https://arxiv.org/pdf/1808.09381.pdf) 

+ There Are Many Consistent Explanations of Unlabeled Data: Why You Should Average, https://openreview.net/forum?id=rkgKBhA5Y7

  [Mean-Teacher](https://arxiv.org/pdf/1703.01780.pdf) 

  model-level smoothness



The Quiet Semi-Supervised Revolution

MixMatch: A Holistic Approach to Semi-Supervised Learning https://arxiv.org/pdf/1905.02249.pdf

