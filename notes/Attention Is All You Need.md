### contribution

+ 





### architecture

Transformer

+ encoder-decoder architecture

  + a stack of encoders

    The encoders are all identical in structure (yet they do not share weights), each one is broken down into two sub-layers: self-attention and feed-forward neural network.



    **Property**:

    the word in each **position** flows through its own path in the encoder. There are dependencies between these paths in the self-attention layer (self attention allows current word to look at other **positions** in the input sequence for clues that can help lead to a better encoding for this word). The feed-forward layer does not have those dependencies, however, and thus the various paths can be executed in parallel while flowing through the feed-forward layer.

  + a stack of decoders

    The decoders include: self-attention, encoder-decoder attention and feed forward neural network.


#### input representation

Word Embedding

Positional Encoding<br>It determine the position of each word, or the distance between different words in the sequence. The intuition here is that adding these values to the embeddings provides meaningful distances between the embedding vectors once they’re projected into Q/K/V vectors and during dot-product attention.



#### self-attention

First - Multiply embeddings matrix by the weight matrices ($W^Q,W^K,W^V$) is to get the Query, Key, and Value matrices ($Q,K,V$) .

Second - Dot product of the Query matrices with the Key matrices is to score each word of the input sentence against this word. The score determines how much focus to place on other parts of the input sentence as we encode a word at a certain position. 

Third  - Divide the scores by the square root of the dimension of the Key vectors. This leads to having more stable gradients. There could be other possible values here, but this is the default.

Fourth - Pass the result through a softmax operation. Softmax normalizes the scores so they’re all positive and add up to 1. This softmax score determines how much each word will be expressed at this position. Clearly the word at this position will have the highest softmax score, but sometimes it’s useful to attend to another word that is relevant to the current word.

Fifth - Multiply each Value matrices by the softmax score (in preparation to sum them up). The intuition here is to keep intact the values of the word(s) we want to focus on, and drown-out irrelevant words (by multiplying them by tiny numbers like 0.001, for example).

The resulting matrices is one we can send along to the feed-forward neural network.



The self attention layers in the decoder operate in a slightly different way than the one in the encoder:<br>In the decoder, the self-attention layer is only allowed to attend to earlier positions in the output sequence. This is done by masking future positions (setting them to `-inf`) before the softmax step in the self-attention calculation.

#### multi-headed attention

This improves the performance of the attention layer in two ways:

1. It expands the model’s ability to focus on different positions. It would be useful if we’re translating a sentence like “The animal didn’t cross the street because it was too tired”, we would want to know which word “it” refers to.
2. It gives the attention layer multiple “representation subspaces”. With multi-headed attention we have not only one, but multiple sets of Query/Key/Value weight matrices (the Transformer uses eight attention heads, so we end up with eight sets for each encoder/decoder). Each of these sets is randomly initialized. Then, after training, each set is used to project the input embeddings (or vectors from lower encoders/decoders) into a different representation subspace.



With multi-headed attention, first concatenate all the attention heads (self-attention results), then multiply with a weight matrix ($W^O$) that was trained jointly with the mode, finally send the result matrices that captures information from all the attention heads forward to the feed-forward neural network. 



#### residual connection

Each sub-layer (self-attention, feed-forward neural network) in each encoder has a residual connection around it, and is followed by a layer-normalization step.

This goes for the sub-layers of the decoder as well.



#### decoder-encoder attention

The output of the top encoder is then transformed into a set of attention vectors K and V. These are to be used by each decoder in its “encoder-decoder attention” layer which helps the decoder focus on appropriate places in the input sequence



The “Encoder-Decoder Attention” layer works just like multi-headed self-attention, except it creates its Queries matrix from the layer below it, and takes the Keys and Values matrix from the output of the encoder stack.

### Question

+ 





### reference

http://jalammar.github.io/illustrated-transformer/

http://nlp.seas.harvard.edu/2018/04/03/attention.html

