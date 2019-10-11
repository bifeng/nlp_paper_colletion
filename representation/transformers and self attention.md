## transformers and self attention



motivation:

sequential computation inhibits parallelization

no explicit modeling of long and short range dependencies

the architecture doesn't have a very clear explicit way to model hierarchy



**self attention does have the ability models and inductive biases**



<u>Does it allow for better gradient transfer ?</u>



advantage:

constant 'path length' between any two positions

unbounded memory

trivial to parallelize (per layer)

models self-similarity

relative attention provides expressive timing, equivariance, and extends naturally to graphs









### application

(task completion)

#### image generation

image transformer



#### music generation

music transformer

the regular attention mechanism - a weighted average of the past history

backwards:<br>all the past becomes kind of a bag of wards, like there is no structure of which came before or after, so there is the positional sinusoids.

convolution - different linear transformations by relative position (translation equivariance)

relative attention - attention + convolution


$$
softmax(QK^T + Qf(E_{rel}))
$$
Self-Attention With Relative Position Representations (Shaw et al., 2018)
$$
softmax(QK^T + skew(QE^T_{rel}))
$$
Music Transformer, Cheng-Zhi Anna Huang, Ashish Vaswani, Jakob Uszkoreit, Noam Shazeer, Ian Simon, Curtis Hawthorne, Andrew M. Dai, Matthew D. Hoffman, Monica Dinculescu, Douglas Eck, ICLR 2019 [arxiv](https://arxiv.org/abs/1809.04281) 



#### graphs





### paper









