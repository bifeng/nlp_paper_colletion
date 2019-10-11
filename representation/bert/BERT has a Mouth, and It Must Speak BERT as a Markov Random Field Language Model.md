Machine Translation:

Guillaume Lample and Alexis Conneau. 2019. Crosslingual LanguageModel Pretraining. arXiv e-prints, page arXiv:1901.07291.



Yoav Goldberg. 2019. Assessing bert’s syntactic abilities. [arxiv](https://arxiv.org/abs/1901.05287) 



BERT is a combination of a Markov random field language model with pseudo log-likelihood training and that it learns a distribution over sentences (of some given length.) This suggests that we can use BERT not only as parameter initialization for finetuning but as a generative model of sentences to either score a sentence or sample a sentence.



Ranking



Sampling

Gibbs sampling which fits naturally with (stochastic) pseudo log-likelihood learning.

Gibbs sampling, as well as any MCMC sampler with a local proposal distribution, tends to get stuck in a mode of the distribution, we advise running multiple chains of Gibbs sampling.



Sequential Sampling

















