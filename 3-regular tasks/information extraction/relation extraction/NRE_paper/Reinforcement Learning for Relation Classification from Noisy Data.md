### Question

+ 如何处理非平衡样本？

+ For bag-level training/prediction, what if the bags with all noisy sentences which do not describe a relation at all ?

  (our investigation on a widely used [dataset](http://iesl.cs.umass.edu/riedel/ecml/) shows that 53% out of 100 sample bags have no sentences that describe the relation.)
  
+ What's the reward ?

+ When it's end up iterating ?

  



### Contribution

+ our method directly filters out noisy sentences. 

  Unlike reducing the weights of noisy sentences (Lin et al. 2016) or retaining one sentence in a bag (Zeng et al. 2014), our method is better at dealing with noisy data.

  



### Limitation

+ sentence level - relation classifier need to be pretraining !

  partition the bag to sentence and training relation classifier ? data unbalance problem ? 

+ 



### Architecture

we decompose the task of relation classification into two sub-problems in this paper: instance selection and
relation classification.

we are able to first select high quality sentences from <u>a sentence bag</u>, and then predict a relation at the sentence level by the relation classifier.

The major challenge here is how to train the two modules jointly, particularly when the instance selector has no explicit knowledge about which sentences are labeled incorrectly.

We address this challenge by casting the instance selection task as a reinforcement learning problem (Sutton and
Barto 1998). Intuitively, although we do not have an explicit supervision for the instance selector, we can measure
the utility of the selected sentences as a whole. Thus, the instance selection process has the following two properties:
first, trial-and-error-search, meaning that the instance selector attempts to choose some sentences and obtain feedback (or **reward**) on the quality of the selected sentences from the relation classifier; second, the feedback from the relation classifier can be obtained only when we finish the instance selection process, which is typically delayed. These
two properties naturally inspire us to utilize reinforcement learning techniques.

image???

### model training

To optimize the policy network in the instance selector, we use a Monto-Carlo based policy gradient method (Williams 1992), which favors actions with high sampled reward. 

To optimize the CNN component, we use a gradient descent method to minimize the objective function (i.e., Eq. 7). 

<u>We pretrain the model before the joint training process starts.</u> We first pretrain the CNN in the relation classifier, and then pretrain the policy function by computing the reward with the pretrained CNN, while the parameters of the CNN model are frozen. 

At last, we jointly train the instance selector and the relation classifier. 

We found such a pre-training strategy is quite crucial for our method, which is also widely recommended by many other reinforcement learning studies(Bahdanau et al. 2016).







### sentence level



### bag level





task

-完成数据预处理

-

