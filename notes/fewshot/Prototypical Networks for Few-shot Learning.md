### Question

+ whether it makes sense to use multiple prototypes per class instead of just one.

  If the number of prototypes per class is fixed and greater than 1, then this would require a partitioning
  scheme to further cluster the support points within a class. This has been proposed in Mensink
  et al. [19] and Rippel et al. [25]; however both methods require a separate partitioning phase that is
  decoupled from the weight updates, while our approach is simple to learn with ordinary gradient
  descent methods.

+ 



### Assumption

Since data is severely limited, we work under the assumption that a classifier should have a very simple **inductive bias**.

### Architecture

Our approach, prototypical networks, is based on the idea that there exists an embedding in which points cluster around a single prototype representation for each class. In order to do this, we learn a non-linear mapping of the input into an embedding space using a neural network and take a class’s prototype to be the mean of its **support set** in the embedding space. Classification is then performed for an embedded **query point** by simply finding the nearest class prototype.



### Prototypical Networks as Mixture Density Estimation





### Hyperparameters

Chosen distance metric - <br>The choice of distance is vital, as Euclidean distance greatly outperforms the more commonly used cosine similarity.

Modifying the episodic learning procedure - <br>A straightforward way to construct episodes, used in Vinyals et al. [29] and Ravi and Larochelle [22], is to choose $N_c$ classes and $N_S$ support points per class in order to match the expected situation at test-time.<br>However, We have found that it can be extremely beneficial to train with a higher $N_c$, or “way”, than will be used at test-time.<br>And, we found that it is usually best to train and test with the same $N_S$ or “shot” number.



