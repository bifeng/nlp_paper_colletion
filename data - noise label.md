





### learning with noisy label

- https://github.com/subeeshvasu/Awesome-Learning-with-Label-Noise

- Learning from Noisy Labels with Deep Neural Networks: A Survey. H Song, M Kim, D Park, J Lee [Korea Advanced Institute of Science and Technology] (2020) 

  
  
- Finding label errors in datasets and learning with noisy labels. https://pypi.org/project/cleanlab/

  

- Learning to Reweight Examples for Robust Deep Learning, Mengye Ren, Wenyuan Zeng, Bin Yang, Raquel Urtasun, ICML 2018 [arxiv](<https://arxiv.org/abs/1803.09050>) 

  we propose a novel meta-learning algorithm that learns to assign weights to training examples based on their gradient directions. 

  To determine the example weights, our method performs a meta gradient descent step on the current mini-batch example weights (which are initialized from zero) to minimize the loss on a clean unbiased validation set. 

  Our proposed method can be easily implemented on any type of deep network, does not require any additional hyperparameter tuning, and achieves impressive performance on **class imbalance** and **corrupted label problems** where only a small amount of clean validation data is available.

- Making Deep Neural Networks Robust to Label Noise: a Loss Correction Approach, Giorgio Patrini, Alessandro Rozza, Aditya Menon, Richard Nock, Lizhen Qu, CVPR 2017 [arxiv](<https://arxiv.org/abs/1609.03683>) 

  **noise estimation**

  We propose two procedures for loss correction that are agnostic to both application domain and network architecture. 

  They simply amount to at most a matrix inversion and multiplication, provided that we know the probability of each class being corrupted into another. 

  We further show how one can estimate these probabilities, adapting a recent technique for noise estimation to the multi-class setting, and thus providing an end-to-end framework.

- Deep Learning is Robust to Massive Label Noise, David Rolnick, Andreas Veit, Serge Belongie, Nir Shavit [arxiv](<https://arxiv.org/abs/1705.10694>) 

  deep neural networks are capable of generalizing from training data for which true labels are massively **outnumbered** by incorrect labels.

  

#### tools

+ https://github.com/cgnorthcutt/cleanlab

  Find label errors in datasets, weak supervision, and learning with noisy labels.



### data noising as smoothing

- Data Noising as Smoothing in Neural Network Language Models. ICLR2017





### loss function

#### NCE loss

noise contrastive estimation



<https://datascience.stackexchange.com/questions/13216/intuitive-explanation-of-noise-contrastive-estimation-nce-loss>



- Noise-contrastive estimation: A new estimation principle for unnormalized statistical models, [paper](<http://proceedings.mlr.press/v9/gutmann10a/gutmann10a.pdf>) 

  

- Noise-Contrastive Estimation for Answer Selection with Deep Neural Networks

  > 1. Random Sampling. We randomly select a number of negative samples for each positive answer.
  > 2. Max Sampling. We select the most difficult negative samples. In each epoch, we compute the similarities between all (p+, p−) pairs using the trained model from the previous training epoch. Then we select the negative answers by maximizing their similarities to the positive answer.
  > 3. Mix Sampling. We take advantages of both random sampling and max sampling by selecting half of the samples from each strategy.





#### Noise-robust loss

- $\mathcal{L}_{DMI}$: An Information-theoretic Noise-robust Loss Function, NeurIPS 2019 [arxiv](https://arxiv.org/abs/1909.03388) [code](<https://github.com/Newbeeer/L_DMI>) 





