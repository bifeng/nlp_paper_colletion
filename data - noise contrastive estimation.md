<https://datascience.stackexchange.com/questions/13216/intuitive-explanation-of-noise-contrastive-estimation-nce-loss>



Noise-contrastive estimation: A new estimation principle for unnormalized statistical models, [paper](<http://proceedings.mlr.press/v9/gutmann10a/gutmann10a.pdf>) 



### Paper

+ Noise-Contrastive Estimation for Answer Selection with Deep Neural Networks

  > 1. Random Sampling. We randomly select a number of negative samples for each positive answer.
  > 2. Max Sampling. We select the most difficult negative samples. In each epoch, we compute the similarities between all (p+, p−) pairs using the trained model from the previous training epoch. Then we select the negative answers by maximizing their similarities to the positive answer.
  > 3. Mix Sampling. We take advantages of both random sampling and max sampling by selecting half of the samples from each strategy.