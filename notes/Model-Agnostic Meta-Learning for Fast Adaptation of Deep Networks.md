more refer:

https://danieltakeshi.github.io/2018/04/01/maml/

explain why it works - On First-Order Meta-Learning Algorithms, OpenAI, Alex Nichol and Joshua Achiam and John Schulman, [paper](https://arxiv.org/pdf/1803.02999.pdf) 





### Question

+ why it works ?

  



### Idea

The key idea underlying our method is to train **the model’s initial parameters** such that the model has maximal performance on a new task after the parameters have been updated through one or more gradient steps computed with
a small amount of data from that new task.

The process of training a model’s parameters such that a few gradient steps, or even a single gradient step, can produce
good results on a new task can be viewed from <u>a feature learning standpoint</u> as **building an internal representation** that is broadly suitable for many tasks.

From <u>a dynamical systems standpoint</u>, our learning process can be viewed as **maximizing the sensitivity of the loss functions of new tasks with respect to the parameters**: when the sensitivity is high, small local changes to the parameters can lead to large improvements in the task loss.

### Contribution

+ model-agnostic  -  it is compatible with any model trained with gradient descent

+ task-agnostic - It is applicable to a variety of different learning problems, including classification, regression, and reinforcement learning.

+ Unlike previous methods - 

  the MAML learner’s weights are updated using the gradient, rather than a learned update. (?)

  It does not introduce additional parameters for meta-learning nor require a particular learner architecture.



### Architecture



<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/MAML.png" width="800" height="300" alt="MAML"></img>
</div>



The MAML meta-gradient update involves a gradient through a gradient. Computationally, this requires an additional
backward pass through $f$ to compute Hessian-vector products, or droppingt his backward pass and using a first-order approximation. 











