<https://github.com/huggingface/pytorch-transformers/tree/master/examples/distillation>

<https://medium.com/huggingface/distilbert-8cf3380435b5>



The most common tools include **quantization** (approximating the weights of a network with a smaller precision) and **weights pruning** (removing some connections in the network). 

### quantization

https://blog.rasa.com/compressing-bert-for-faster-prediction-2/



### weights pruning



### Knowledge distillation

*Knowledge distillation* (sometimes also referred to as *teacher-student learning*) is a **compression technique in which a small model is trained to reproduce the behavior of a larger model** (or an ensemble of models). 

It was introduced by [Bucila et al.](https://www.cs.cornell.edu/~caruana/compression.kdd06.pdf) and generalized by [Hinton et al.](https://arxiv.org/abs/1503.02531) a few years later.



#### How to understand distillation ?

it prevents the model to be too sure about its prediction (similarly to label smoothing).

#### How can we copy this dark knowledge?

In the **teacher-student training**, we train a student network to mimic the **full output distribution** of the teacher network (its knowledge).

> We are training the student to generalize the same way as the teacher by matching the output distribution.

Rather than training with a cross-entropy over the hard targets (one-hot encoding of the gold class), we transfer the knowledge from the teacher to the student with a cross-entropy over the soft targets (probabilities of the teacher).

To further expose the mass of the distribution over the classes, Hinton et al. introduce a **softmax-temperature**.





### Question

+ **dark knowledge** in Knowledge distillation ?
+ 



