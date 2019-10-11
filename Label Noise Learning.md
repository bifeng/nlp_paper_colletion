<https://github.com/subeeshvasu/Awesome-Learning-with-Label-Noise>





+ Learning to Reweight Examples for Robust Deep Learning, Mengye Ren, Wenyuan Zeng, Bin Yang, Raquel Urtasun, ICML 2018 [arxiv](<https://arxiv.org/abs/1803.09050>) 

  we propose a novel meta-learning algorithm that learns to assign weights to training examples based on their gradient directions. 

  To determine the example weights, our method performs a meta gradient descent step on the current mini-batch example weights (which are initialized from zero) to minimize the loss on a clean unbiased validation set. 

  Our proposed method can be easily implemented on any type of deep network, does not require any additional hyperparameter tuning, and achieves impressive performance on **class imbalance** and **corrupted label problems** where only a small amount of clean validation data is available.

+ Making Deep Neural Networks Robust to Label Noise: a Loss Correction Approach, Giorgio Patrini, Alessandro Rozza, Aditya Menon, Richard Nock, Lizhen Qu, CVPR 2017 [arxiv](<https://arxiv.org/abs/1609.03683>) 

  **noise estimation**

  We propose two procedures for loss correction that are agnostic to both application domain and network architecture. 

  They simply amount to at most a matrix inversion and multiplication, provided that we know the probability of each class being corrupted into another. 

  We further show how one can estimate these probabilities, adapting a recent technique for noise estimation to the multi-class setting, and thus providing an end-to-end framework.

+ Deep Learning is Robust to Massive Label Noise, David Rolnick, Andreas Veit, Serge Belongie, Nir Shavit [arxiv](<https://arxiv.org/abs/1705.10694>) 

  deep neural networks are capable of generalizing from training data for which true labels are massively **outnumbered** by incorrect labels.

  

  