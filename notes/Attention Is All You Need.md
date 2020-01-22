more refer:

<https://lilianweng.github.io/lil-log/2018/06/24/attention-attention.html>







motivation:

RNN - constraint of sequential computation

CNN - difficult to learn dependencies between distant positions (the number of operations grows in the distance between positions linearly or logarithmically)



Transformer -- allows for parallelization

​		     -- a constant number of operations, albeit at the cost of reduced effective resolution due to averaging attention-weighted positions, an effect we counteract with Multi-Head Attention.

Transformer relying entirely on an attention mechanism to draw global dependencies between input and output.





### contribution

+ 





### architecture

Transformer

+ encoder-decoder architecture

![transformer](https://github.com/bifeng/nlp_paper_notes/raw/master/image/transformer.png)

+ a stack of encoders

  The encoders are all identical in structure (yet they do not share weights), each one is broken down into two sub-layers: self-attention and feed-forward neural network.

  **Property**:

  the word in each **position** flows through its own path in the encoder. There are dependencies between these paths in the self-attention layer (self attention allows current word to look at other **positions** in the input sequence for clues that can help lead to a better encoding for this word). The feed-forward layer does not have those dependencies, however, and thus the various paths can be executed in parallel while flowing through the feed-forward layer.

+ a stack of decoders

  The decoders include: self-attention, encoder-decoder attention and feed forward neural network.


#### input representation

Word Embedding<br>In the embedding layers, we multiply those weights by $\sqrt{d_{model}}$. why ?

Positional Encoding<br>It determine the position of each word, or the distance between different words in the sequence. The intuition here is that adding these values to the embeddings provides meaningful distances between the embedding vectors once they’re projected into Q/K/V vectors and during dot-product attention.

There are many choices of positional encodings, learned or fixed (such as use sine and cosine functions of different frequencies). We chose the sinusoidal version because it may allow the model to extrapolate to sequence lengths longer than the ones encountered during training (for any fixed offset $k$, $PE_{pos+k}$ can be represented as a linear function of
$PE_{pos}$).
$$
PE_{(pos,2i)} = sin(pos/10000^{2i/d_{model}}) \\
PE_{(pos,2i+1)} = cos(pos/10000^{2i/d_{model}})
$$


#### self-attention

motivation:

One is the total computational complexity per layer. Another is the amount of computation that can be parallelized, as measured by the minimum number of sequential operations required. The third is the path length between long-range dependencies in the network. The shorter these paths between any combination of positions in the input and output sequences, the easier it is to learn long-range dependencies. As side benefit, self-attention could yield more interpretable models.



Self-attention, sometimes called intra-attention is an attention mechanism relating different positions of a single sequence in order to compute **a representation of the sequence**.
$$
Attention(Q,K,V) = softmax(\frac{QK^T}{\sqrt{d_k}})\cdot V
$$
First - Multiply embeddings matrix by the weight matrices ($W^Q,W^K,W^V$) is to get the Query, Key, and Value matrices ($Q,K,V$) .

Second - Dot product of the Query matrices with the Key matrices is to score each word of the input sentence against this word. The score determines how much focus to place on other parts of the input sentence as we encode a word at a certain position. 

Third  - Divide the scores by the square root of the dimension of the Key vectors. This leads to having more stable gradients (Without the scaling factor, for large values of $d_k$, the dot products grow large in magnitude, pushing the softmax function into regions where it hase xtremely small gradients). There could be other possible values here, but this is the default.

Fourth - Pass the result through a softmax operation. Softmax normalizes the scores so they’re all positive and add up to 1. This softmax score determines how much each word will be expressed at this position. Clearly the word at this position will have the highest softmax score, but sometimes it’s useful to attend to another word that is relevant to the current word.

Fifth - Multiply each Value matrices by the softmax score (in preparation to sum them up). The intuition here is to keep intact the values of the word(s) we want to focus on, and drown-out irrelevant words (by multiplying them by tiny numbers like 0.001, for example).

The resulting matrices is one we can send along to the feed-forward neural network.



The self attention layers in the decoder operate in a slightly different way than the one in the encoder:<br>In the decoder, the self-attention layer is only allowed to attend to earlier positions in the output sequence. This is done by masking future positions (setting them to `-inf`) before the softmax step in the self-attention calculation.

#### multi-headed attention

Multi-head attention allows the model to jointly attend to information from **different representation subspaces** at **different positions**.

This improves the performance of the attention layer in two ways:

1. It expands the model’s ability to focus on different positions. It would be useful if we’re translating a sentence like “The animal didn’t cross the street because it was too tired”, we would want to know which word “it” refers to.
2. It gives the attention layer multiple “representation subspaces”. With multi-headed attention we have not only one, but multiple sets of Query/Key/Value weight matrices (the Transformer uses eight attention heads, so we end up with eight sets for each encoder/decoder). Each of these sets is randomly initialized. Then, after training, each set is used to project the input embeddings (or vectors from lower encoders/decoders) into a different representation subspace.



With multi-headed attention, first concatenate all the attention heads (self-attention results), then multiply with a weight matrix ($W^O$) that was trained jointly with the mode, finally send the result matrices that captures information from all the attention heads forward to the feed-forward neural network. 



The Transformer uses multi-head attention in three different ways:

+ In "encoder-decoder attention" layers, the <u>queries</u> come from the previous decoder layer, and the memory <u>keys</u> and <u>values</u> come from the  output of the encoder. This allows every position in the decoder to attend over all positions in the input sequence. This mimics the typical encoder-decoder attention mechanisms in sequence-to-sequence models.
+ The encoder contains self-attention layers. In a self-attention layer all of the <u>keys</u>, <u>values</u> and <u>queries</u> come from the same place, in this case, the output of the previous layer in the encoder. Each position in the encoder can attend to all positions in the previous layer of the encoder.
+ Similarly, self-attention layers in the decoder allow each position in the decoder to attend to all positions in the decoder up to and including that position. We need to prevent leftward information flow in the decoder to preserve the auto-regressive property. We implement this inside of scaled dot-product attention by masking out (setting to $-\infin$) all values in the input of the softmax which correspond to illegal connections.



#### residual connection

Each sub-layer (self-attention, feed-forward neural network) in each encoder has a **residual connection** around it, and is followed by a **layer-normalization** step.

This goes for the sub-layers of the decoder as well.



#### decoder-encoder attention

The output of the top encoder is then transformed into a set of attention vectors K and V. These are to be used by each decoder in its “encoder-decoder attention” layer which helps the decoder focus on appropriate places in the input sequence



The “Encoder-Decoder Attention” layer works just like multi-headed self-attention, except it creates its Queries matrix from the layer below it, and takes the Keys and Values matrix from the output of the encoder stack.



### training

#### regularization

##### Residual Dropout

We apply dropout to the output of each sub-layer, before it is added to the sub-layer input and normalized. In addition, we apply dropout to the sums of the embeddings and the positional encodings in both the encoder and decoder stacks.

#### Label Smoothing

During training, we employed label smoothing of value $\epsilon_{ls} = 0.1$. [36]

motivation: regularize the classifier layer by estimating the marginalized effect of label-dropout during training.
$$
l = - \sum^K_{k=1} log(p(k)) q(k)
$$
If the logit corresponding to the ground-truth label is much great than all other logits. This, however, can cause two problems. First, it may result in over-fitting: if the model learns to assign full probability to the ground-truth label for each training example, it is not guaranteed to generalize. Second, it encourages the differences between the largest logit and all others to become large, and this, combined with the bounded gradient $\frac{∂ℓ}{∂z_k}$ ($z_k$ are the logits or unnormalized log-probabilities), reduces the ability of the model to adapt. Intuitively, this happens because the model becomes too confident about its predictions.

We propose a mechanism for encouraging the model to be less confident. While this may not be desired if the goal
is to maximize the log-likelihood of training labels, it does regularize the model and makes it more adaptable. We replace the label distribution $q(k|x)=\sigma_{k,y}$ with
$$
q(k|x) = (1-\epsilon) \sigma_{k,y} + \epsilon u(k)
$$
$u(k)$ is a distribution over labels, which is independent of the training example $x$. In practice, we used the uniform distribution $u(k)=1/K$, $K$ is the number of classes.

### results

#### Machine Translation

For the base models, we used a single model obtained by averaging the last 5 checkpoints, which were written at 10-minute intervals. For the big models, we averaged the last 20 checkpoints. We used beam search with a beam size of 4 and length penalty $ \alpha= 0.6$.



### Question

+ Why layer normalization always followed by residual connection?

  

+ How to understand this sentence "we share the same weight matrix between the two embedding layers and the pre-softmax linear transformation "?

  

+ Why the maximum path length of restricted self-attention is $O(n/r)$? How to analysis the maximum path length?



### paper

+ [36] Christian Szegedy, Vincent Vanhoucke, Sergey Ioffe, Jonathon Shlens, and Zbigniew Wojna. Rethinking the inception architecture for computer vision. CoRR, 2015. [arxiv](https://arxiv.org/abs/1512.00567) :star::star::star::star::star:
+ 

### reference

http://jalammar.github.io/illustrated-transformer/

http://nlp.seas.harvard.edu/2018/04/03/attention.html

