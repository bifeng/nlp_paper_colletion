### Question

+ what's the definition of feature function $g(Y_i,Z)$ ?

   $g(Y_i,Z)$ is 0 or 1 ? (connection the each word slot tags of current sentence with the intent classes)

  

+ p(z|x) or p(y|x) ? which variable is predict first ? or how to predict simultaneously ?

  



### Motivation

Triangular CRF (TriCRF) was proposed for this purpose: On top of the standard CRF, an additional random variable indicating the topic/intent assignment of the sentence is introduced, with dependency links established between the added variable and the hidden label sequence. It was shown empirically that exploiting such dependencies can lead to improved results for both of the modeling tasks.



### Architecture

$$
P(Y,Z|X) = \frac{e^{\sum_i(t(Y_{i-1},Y_i)+g(Y_i,Z)+\sum_j(\theta_j(Y_i)+\beta_j(Z))h_{ij})}}{Z(X)}
$$

The feature function $g(Y_i,Z)$ is used to model the interaction between intent and slot – it essentially acts as an intent dependent slot prior for the model.



