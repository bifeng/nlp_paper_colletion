#### summary

+ Smooth Inverse Frequency weighting (remove common component of embedding by PCA/SVD)

+ The first dominating vector is **dataset-specific**, i.e., they first compute the sentence representation for the entire semantic textual similarity dataset, then extract the top direction from those sentence representations and finally project the sentence representation away from it. By doing so, the top direction will inherently encode the common information across the entire dataset, the top direction for the "headlines" dataset may encode common information about news articles while the top direction for "Twitter’15" may encode the common information about tweets.



#### motivation

We motivated by **the empirical observation** that most word embedding methods, since they seek to capture word co-occurrence probabilities using vector inner product, end up giving large vectors to frequent words, as well as giving unnecessarily large inner products to word pairs, simply to fit the empirical observation that words sometimes occur out of context in documents. These anomalies cause the average of word vectors to have huge components along semantically meaningless directions.



Result: This theoretically derived SIF does better (by a few percent points) than traditional TFIDF in our setting.

#### Algorithm

##### Improved Random Walk model

todo - not very understand!!!



The model is a simple modification for the RandomWalk on Discourses model for generating text in (Arora et al., 2016).

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/sif.png" width="800" height="300" alt="SIF"></img>
</div>
The weight of a word $w$ is $\frac{a}{a + p(w)}$ with a being a parameter and $p(w)$ the (estimated) word frequency; we call this smooth inverse frequency (SIF). $p(w)$ is the unigram probability (**in the entire corpus**) of word.





##### Connection to subsampling probabilities in word2vec

The sub-sampling technique used in Word2vec not only speeds up the training but also learns more regular word representations. Here we explain that this corresponds to an implicit reweighting of the word vectors in the model and therefore the statistical benefit should be of no surprise.













