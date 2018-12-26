https://boknilev.github.io/nlp-analysis-methods/
https://github.com/boknilev/nlp-analysis-methods
### key points

+ review analysis methods in neural language processing, categorize them according to
  prominent research trends, highlight existing limitations, and point to potential directions
  for future work.
+ As end to end systems are gaining prevalence, one may point to two trends. First, some push back against the abandonment of linguistic knowledge and call for incorporating it inside the networks in different ways. Others strive to better understand how neural language processing models work (interpretability). Much of the analysis work thus aims to understand how linguistic concepts that were common as features in NLP systems are captured in neural networks.
+ Elman (1989) introduced analysis methods: from visualizing network activations in time, through clustering words by hidden state activations, to projecting representations to dimensions that emerge as capturing properties like sentence number or verb valency. But his work was limited in some ways, such as evaluating generalization or various linguistic phenomena.

#### What linguistic information is captured in neural networks

##### which methods are used for conducting the analysis

+ The most common approach - predict linguistic properties from activations of the neural network.
+ Other methods for finding correspondences between parts of the neural network and certain
  properties include counting how often attention weights agree with a linguistic property or directly/indirectly computing correlations between neural network activations and some property,

##### what kind of linguistic information is sought

Different kinds of linguistic information have been analyzed (ranging from basic properties like sentence length, word position, word presence, or simple word order, to morphological, syntactic,
and semantic information), (while it is difficult to synthesize a holistic picture from this diverse body of work) it appears that neural networks are able to learn a substantial amount of information on various linguistic phenomena.

But:

+ These models are especially successful at capturing frequent properties, while some
  rare properties are more difficult to learn.
+ the hierarchical nature of the learned representations.
+ models trained with latent trees perform better on natural language inference (NLI) than ones trained with linguistically-annotated trees. Moreover, the trees in these models do not resemble syntactic trees corresponding to known linguistic theories, which casts doubts on the importance of syntax learning in the underlying neural network.

##### which objects in the neural network are being investigated.

Various neural neural network components were investigated, including word embeddings, RNN hidden states or gate activations, sentence embeddings, and attention weights in sequence-to-sequence (seq2seq) models.

##### limitations

From a methodological point of view, most of the relevant analysis work is concerned with correlation: how correlated are neural network components with linguistic properties? What may be lacking is a measure of causation (causal inference): how does the encoding of linguistic properties affect the system output.

+ “embedding models are able to encode divergent linguistic information but have limits on how this information is surfaced.”

  The classification approach may find that a certain amount of linguistic information is captured in the neural network. However, this does not necessarily mean that the information is used by the network.

#### the generation and use of adversarial examples to probe weaknesses of neural networks.






