https://tensorflow.google.cn/extras/candidate_sampling.pdf

Say we have a multiclass or multi­label problem where each training example $(x_i , T_i)$ consists of a context $x_i$ a small (multi) set of target classes $T_i$ out of a large universe $L$ of possible classes. For example, the problem might be to predicting the next word (or the set of future words) in a sentence given the previous words.

We wish to learn a compatibility function $F(x, y)$ which says something about the compatibility of a class $y$ with a context $x$ . For example, the probability of the class given the context.

## Candidate Sampling Algorithms

### Noise Contrastive Estimation (NCE)

### Negative Sampling

### Sampled Logistic

### Full Logistic

### Full Softmax

### Sampled Softmax

