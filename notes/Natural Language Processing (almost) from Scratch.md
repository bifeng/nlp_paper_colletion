http://ronan.collobert.com/senna/

https://github.com/jawahar273/practNLPTools-lite



a unified neural network architecture for tasks including: part-of-speech tagging, chunking, named entity recognition, and semantic role labeling.

### Question

+ How to combine word and sentence task in language model training ?

  



### Summary

+ Using language modeling, learning general word representations, leverages large unlabeld datasets.

+ Using multi-task learning, fine-tuning word embedding to get intermediate representations for multi-task, avoiding task-specific engineering 

  

### Architecture

#### 



#### language model task

loss function







### Multi-Task Learning

Consider related tasks as parallel (joint training or joint decoding).

Method:

1. Joint training: The models are jointly trained with an additional linkage between their trainable parameters, this linkage can take the form of a regularization term in the joint cost function that biases the models towards common representations. A much simpler approach consists in having the models share certain parameters defined a priori. 

   However, the joint labeling requirement is a limitation because such data is not often available. The joint labeling requirement problem was weakened using a predictor to fill in the missing annotations.

2. Joint decoding: Considering additional probabilistic dependency paths between the models. Therefore it defines an implicit supermodel that describes all the tasks in the same probabilistic framework. Without joint training, the additional dependency paths cannot directly involve unobserved variables. Therefore, the natural idea of discovering common internal representations across tasks requires joint training.





### Further Improvements

+ Word representations

  word representations are perhaps more commonly infered from n-gram language modelling rather than smoothed language models. 

  One popular approach is the Brown clustering algorithm (Brown et al., 1992a), which builds hierachical word clusters
  by maximizing the bigram's mutual information.

  Other related approaches exist, like phrase clustering (Lin and Wu, 2009).

  Finally, Huang and Yates (2009) have recently proposed a smoothed language modeling approach based on a Hidden Markov Model.

+ Incorporate task-specific engineering

  Suffix Features for POS, Gazetteers (dictionary) for NER, Parsing for SRL.

+ Cascading

  Consider related tasks as pipeline (consecutive training).

+ Ensemble

