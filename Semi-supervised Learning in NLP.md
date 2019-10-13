more refer:

An overview of proxy-label approaches for semi-supervised learning [site](<http://ruder.io/semi-supervised/>) 

Semi-Supervised Learning for Natural Language, Percy Liang [thesis](<https://cs.stanford.edu/~pliang/papers/meng-thesis.pdf>) 

https://aclweb.org/aclwiki/Semi-supervised_Learning_in_NLP

基于分歧的方法  机器学习,周志华





#### Method

co-training

multi-view training

cross-view training

adversarial training/filtering

distant supervision

weak supervision







#### Paper

Semi-Supervised Sequence Modeling with Cross-View Training
Kevin Clark, Minh-Thang Luong, Christopher D. Manning, Quoc V. Le EMNLP 2018 [arxiv](<https://arxiv.org/abs/1809.08370>) 

Adversarial Training Methods for Semi-Supervised Text Classification
Takeru Miyato, Andrew M. Dai, Ian Goodfellow ICLR 2017 [arxiv](<https://arxiv.org/abs/1605.07725>)

Semi-supervised Convolutional Neural Networks for Text Categorization via Region Embedding
Rie Johnson, Tong Zhang NIPS 2005 [arxiv](<https://arxiv.org/abs/1504.01255>)



semi supervised guided topic model with custom guidedLDA

<https://github.com/vi3k6i5/GuidedLDA>





#### Snorkel

+ [snorkel](https://github.com/HazyResearch/snorkel)

+ [metal](<https://github.com/HazyResearch/metal>)

  Snorkel MeTaL: A framework for training models with multi-task weak supervision

+ 





##### scholar

- [Alex Ratner](https://ajratner.github.io/) 

##### paperlist

https://zhpmatrix.github.io/2019/06/05/snorkel/

- [paperlist on snorkel](<https://hazyresearch.github.io/snorkel/>)

- Snorkel: Rapid Training Data Creation with Weak Supervision

- Snorkel: Fast Training Set Generation for Information Extraction

- Snorkel Fast Training Set Generation with Weak Supervision

- Data Programming: Creating Large Training Sets, Quickly. Alexander Ratner, Christopher De Sa, Sen Wu, Daniel Selsam, Christopher Ré, 2016 NIPS, [arxiv](https://arxiv.org/abs/1605.07723) 

  We therefore propose a paradigm for the programmatic creation of training sets called data programming in which users express weak supervision strategies or domain heuristics as labeling functions, which are programs that label subsets of the data, but that are noisy and may conflict.

##### snorkel vs. co-training

1. snorkel consider the correlation between the sources, but co-training assume the independence of sources.
2. snorkel - the label is weighted, but co-training - the label is come from the most confidence one.

##### summary

1. weak supervision sources

   the sources can be generated from correlated labeling functions. These functions capture a range of common forms of weak supervision, for example:

   **Pattern-based**

   **Distant supervision**

   **Weak classiers**

   **Labeling function generators**

   ...

2. generative model

   sources will overlap and conflict, and to resolve their conflicts we need to estimate their accuracies and correlation structure, without access to ground truth. 

   Snorkel learns the accuracies of weak supervision sources using a generative model (the true label is the latent variable)

   challenge:

   It's hard for generative model to model the correlation between the sources.

   Snorkel automatically selecting which dependencies to model without access to ground truth[^1].

3. discriminative model

   we need to pass on critical lineage information about label quality to the end model being trained.

   While the generative model is essentially a re-weighted combination of the user-provided labeling functions - which tend to be precise but low-coverage - modern discriminative models can retain this precision while learning to generalize beyond the labeling functions, increasing coverage and robustness on unseen data.

[^1]: Learning the Structure of Generative Models without Labeled Data, Stephen H. Bach, Bryan He, Alexander Ratner, Christopher Ré [arxiv](<https://arxiv.org/abs/1703.00854>) [blog](<https://hazyresearch.github.io/snorkel/blog/structure_learning.html>) 


