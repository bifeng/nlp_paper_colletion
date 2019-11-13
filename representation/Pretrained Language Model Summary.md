refer:

[The State of Transfer Learning in NLP](<http://ruder.io/state-of-transfer-learning-in-nlp/>)



### challenge

For more pointers, have a look at [the slides](https://docs.google.com/presentation/d/1fIhGikFPnb7G5kr58OvYC3GN4io7MznnM0aAgadvJfc/edit#slide=id.g569f436ced_0_34).

Pretrained language models are still bad at the following tasks:

+ fine-grained linguistic tasks ([Liu et al., 2019](https://arxiv.org/abs/1903.08855))

+ hierarchical syntactic reasoning ([Kuncoro et al., 2019](https://www.aclweb.org/anthology/P19-1337))

+ common sense (when you actually make it difficult; [Zellers et al., 2019](https://arxiv.org/abs/1905.07830))

+ natural language generation, in particular maintaining long-term dependencies, relations, and coherence.

  

Particularly large models that are fine-tuned on small amounts of data are difficult to optimize and suffer from **high variance**. Current pretrained language models are also very large. Distillation and pruning are two ways to deal with this.



Pretrained language modelling objective has its weaknesses, language modelling encourages a focus on syntax and word co-occurrences and only provides a weak signal for capturing semantics and long-term context.

We can take inspiration from other forms of self-supervision. In addition, we can design specialized pretraining tasks that explicitly learn certain relationships ([Joshi et al., 2019](https://arxiv.org/abs/1907.10529), [Sun et al., 2019](http://127.0.0.1:2368/state-of-transfer-learning-in-nlp/ERNIE 2.0: A Continual Pre-training Framework for Language Understanding)). On the whole, it is difficult to learn certain types of information from raw text. Recent approaches incorporate structured knowledge ([Zhang et al., 2019](http://arxiv.org/abs/1905.07129); [Logan IV et al., 2019](https://www.aclweb.org/anthology/P19-1598)) or leverage multiple modalities ([Sun et al., 2019](https://arxiv.org/abs/1904.01766); [Lu et al., 2019](https://arxiv.org/abs/1908.02265)) as two potential ways to mitigate this problem.



### what is in a  representation ?

Network architectures generally determine what is in a representation. For instance, BERT has been observed to capture syntax ([Tenney et al., 2019](https://arxiv.org/abs/1905.05950); [Goldberg, 2019](https://arxiv.org/abs/1901.05287)). Different architectures show different layer-wise trends in terms of what information they capture ([Liu et al., 2019](https://www.aclweb.org/anthology/N19-1112)).

The information that a model captures also depends how you look at it: Visualizing activations or attention weights provides a bird's eye view of the model's knowledge, but focuses on a few samples; probes that train a classifier on top of learned representations in order to predict certain properties (as can be seen above) discover corpus-wide specific characteristics, but may introduce their own biases; finally, network ablations are great for improving the model, but may be task-specific.

#### Syntax

representations still learn some notion of syntax, even when syntax is not explicitly encoded ([Williams et al. 2018](https://www.mitpressjournals.org/doi/pdfplus/10.1162/tacl_a_00019))

knowledge of syntax can be distilled efficiently into state-of-the-art models ([Kuncoro et al., 2019](https://www.aclweb.org/anthology/P19-1337))



### how to adaptation ?

#### architectural modifications

**a) Keep the pretrained model internals unchanged**



**b) Modify the pretrained model internal architecture**

adapters - [Houlsby et al., 2019](https://arxiv.org/abs/1902.00751); [Stickland and Murray, 2019](https://arxiv.org/abs/1902.02671)



#### optimization schemes 

In terms of optimizing the model, we can choose which weights we should update and how and when to update those weights.

1. Which weights to update

**a) Do not change the pretrained weights (feature extraction)**

[Peters et al., 2018](https://arxiv.org/abs/1802.05365), [Ruder et al., 2019](https://arxiv.org/abs/1705.08142)

**b) Change the pretrained weights (fine-tuning)** 



2. How and when to update the weights

motivation: we want to avoid overwriting useful pretrained information and maximize positive transfer. Related to this is the concept of catastrophic forgetting ([McCloskey & Cohen, 1989](https://www.sciencedirect.com/science/article/pii/S0079742108605368); [French, 1999](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.480.7627&rep=rep1&type=pdf)), which occurs if a model forgets the task it was originally trained on.

A guiding principle for updating the parameters of our model is to update them progressively from top-to-bottom in time, in intensity, or compared to a pretrained model:

**a) Progressively in time (freezing)**

intuition: training all layers at the same time on data of a different distribution and task may lead to instability and poor solutions. Instead, we train layers individually to give them time to adapt to the new task and data.

This goes back to layer-wise training of early deep neural networks ([Hinton et al., 2006](https://www.cs.toronto.edu/~hinton/absps/fastnc.pdf); [Bengio et al., 2007](https://papers.nips.cc/paper/3048-greedy-layer-wise-training-of-deep-networks.pdf)). Recent approaches ([Felbo et al., 2017](https://www.aclweb.org/anthology/D17-1169); [Howard and Ruder, 2018](https://arxiv.org/abs/1801.06146); [Chronopoulou et al., 2019](https://arxiv.org/abs/1902.10547)) mostly vary in the combinations of layers that are trained together; all train all parameters jointly in the end. 

**b) Progressively in intensity (lower learning rates)**

motivation: We want to use lower learning rates to avoid overwriting useful information. Lower learning rates are particularly important in lower layers (as they capture more general information), early in training (as the model still needs to adapt to the target distribution), and late in training (when the model is close to convergence). 



decays the learning rate for each layer:

discriminative fine-tuning ([Howard and Ruder, 2018](https://aclweb.org/anthology/P18-1031)), which decays the learning rate for each layer. 



a triangular learning rate schedule/warm-up:

In order to maintain lower learning rates early in training, a triangular learning rate schedule can be used, which is also known as learning rate warm-up in Transformers. [Liu et al. (2019)](https://arxiv.org/abs/1908.03265) recently suggest that warm-up reduces variance in the early stage of training.



**c) Progressively vs. a pretrained model (regularization)**

One way to minimize catastrophic forgetting is to encourage target model parameters to stay close to the parameters of the pretrained model using a regularization term ([Wiese et al., CoNLL 2017](https://www.aclweb.org/anthology/K17-1029), [Kirkpatrick et al., PNAS 2017](https://www.pnas.org/content/114/13/3521)).





#### whether to obtain more signal

We can often improve the performance of transfer learning by combining a diverse set of signals:

**Sequential adaptation**  If related tasks are available, we can fine-tune our model first on a related task with more data before fine-tuning it on the target task. This
helps particularly for tasks with limited data and similar tasks ([Phang et al., 2018](https://arxiv.org/abs/1811.01088v2)) and improves sample efficiency on the target task ([Yogatama et al., 2019](https://arxiv.org/abs/1901.11373)).

**Multi-task fine-tuning**  Alternatively, we can also fine-tune the model jointly on related tasks together with the target task. The related task can also be an unsupervised auxiliary task. Language modelling is a good choice for this and has been shown to help even without pretraining ([Rei et al., 2017](https://arxiv.org/abs/1704.07156)). The task ratio can optionally be annealed to de-emphasize the auxiliary task towards the end of training ([Chronopoulou et al., NAACL 2019](https://arxiv.org/abs/1902.10547)). Language model fine-tuning is used as a separate step in ULMFiT ([Howard and Ruder, 2018](https://aclweb.org/anthology/P18-1031)). Recently, multi-task fine-tuning has led to improvements even with many target tasks ([Liu et al., 2019](http://127.0.0.1:2368/state-of-transfer-learning-in-nlp/(Liu et al., 2019)), [Wang et al., 2019](https://www.aclweb.org/anthology/P19-1439)).

**Dataset slicing**  Rather than fine-tuning with auxiliary tasks, we can use [auxiliary heads that are trained only on particular subsets of the data](https://dawn.cs.stanford.edu/2019/03/22/glue/). To this end, we would first analyze the errors of the model, use heuristics to automatically identify challenging subsets of the training data, and then train auxiliary heads jointly with main head.

**Semi-supervised learning**  We can also use semi-supervised learning methods to make our model's predictions more consistent by perturbing unlabelled examples. The perturbation can be noise, masking ([Clark et al., 2018](https://arxiv.org/abs/1809.08370)), or data augmentation, e.g. back-translation ([Xie et al., 2019](https://arxiv.org/abs/1904.12848)).

**Ensembling**  To improve performance the predictions of models fine-tuned with different hyper-parameters, fine-tuned with different pretrained models, or trained on different target tasks or dataset splits may be combined.

**Distilling**  Finally, large models or ensembles of models may be distilled into a single, smaller model. The model can also be a lot simpler (Tang et al., 2019) or have a different inductive bias ([Kuncoro et al., 2019](https://www.aclweb.org/anthology/P19-1337)). Multi-task fine-tuning can also be combined with distillation ([Clark et al., 2019](https://arxiv.org/abs/1907.04829)).

### Trade-offs and practical considerations

[Peters et al., 2019](https://arxiv.org/abs/1903.05987)



















