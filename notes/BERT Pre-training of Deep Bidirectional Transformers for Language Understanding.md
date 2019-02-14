

### introduction

+ Two existing strategies for applying pre-trained language representations to downstream tasks: feature-based (such as ELMo) and fine-tuning (such as
  the Generative Pre-trained Transformer (OpenAI GPT)). Both approaches share the same objective function during pre-training, where they use unidirectional language
  models to learn general language representations. Notes, ELMo uses a shallow concatenation of <u>independently</u> trained left-to-right and right-to-left LMs.

+ The advantage of feature-based approach

  First, not all NLP tasks can be easily be represented by a Transformer encoder architecture, and therefore require a task-specific model architecture to be added. Second, there are major computational benefits to being able to pre-compute an expensive representation of the training data once and then run many experiments with less expensive models on top of this representation.

+ The advantage of fine-tuning approach

  It eliminate the needs of many heavily engineered task-specific architectures.

+ 



### contribution

+ unidirectional $\rightarrow$ bidirectional

+ a new pre-training objective: the “masked language model” (MLM). The masked language model randomly masks some of the tokens from the input, and the objective is to predict the original vocabulary id of the masked word based only on its context.

  This is a very simple trick that's used in **de-noising auto-encoders**, where we mask some percent of words from the input and have to reconstruct those words from context. We call this a "masked LM" but it is often called <u>a Cloze task</u>.

  + mismatch problem

    a mismatch between pre-training and finetuning, since the [MASK] token is never seen during fine-tuning.

    **Strategy**: chooses 15% of tokens at random -> 80% of the time replace the word with the [MASK] token, 10% of the time replace the word with a random word, 10% of the time keep the word unchanged.

  + converge problem

    only 15% of tokens are predicted in each batch, which suggests that more pre-training steps maybe required for the model to converge.

+ a “next sentence prediction” task that jointly pre-trains text-pair representations.


### architecture

a multi-layer bidirectional Transformer encoder

the number of layers (i.e., Transformer blocks) as $L$, the hidden size as $H$, and the number of self-attention heads as $A$. In all cases we set the feed-forward/filter size to
be $4H$.

+ $BERT_{BASE}$: L=12, H=768, A=12, Total Parameters=110M

  12

  feed-forward/filter size 4 * 768

  hidden size 768

  number of self-attention heads 12

+ $BERT_{LARGE}$: L=24, H=1024, A=16, Total Parameters=340M


#### input representation

For a given token, its input representation is constructed by summing the corresponding
token, segment and position embeddings.

+ tokenization

  character-based tokenization for Chinese, and WordPiece tokenization for all other languages

+ the token embeddings

  The first token [CLS] is the embedding for classification

  The separation of non-consecutive token [SEP] is the embedding for separation

+ the segmentation embeddings (sentence embeddings)

+ the position embeddings

  supported sequence lengths up to <u>512</u> tokens

#### pre-training procedure

The training loss is the sum of the mean masked LM likelihood and mean next sentence prediction likelihood.



#### fine-tuning procedure

The fine-tuning procedure is a simple classification layer be added to the pre-trained model, and all parameters are jointly fine-tuned on a downstream task.

For fine-tuning, most model hyperparameters are the same as in pre-training, with the exception of the <u>batch size</u>, <u>learning rate</u>, and <u>number of training epochs</u>.

The optimal hyperparameter values are task-specific, but we found the following range of possible values to work well across all tasks:
• Batch size: 16, 32
• Learning rate (Adam): 5e-5, 3e-5, 2e-5
• Number of epochs: 3, 4



+ sequence-level classification tasks $\rightarrow$ straightforward

  sentence pair classification tasks: 

  single sentence classification tasks: 

+ span level and token-level prediction tasks $\rightarrow$ must be modified slightly in a task specific manner

  question answering tasks: 

  single sentence tagging tasks: 


#### feature-based procedure

The feature-based procedure is using the fixed features which are extracted from the pretrained model.



- sequence-level classification tasks $\rightarrow$ straightforward

  sentence pair classification tasks: 

  single sentence classification tasks: 

- span level and token-level prediction tasks $\rightarrow$ must be modified slightly in a task specific manner

  question answering tasks: 

  single sentence tagging tasks: concatenate the token representations from the top <u>four</u> hidden layers of the pretrained Transformer.

### datasets

To generate each training input sequence, we sample <u>two spans of text</u> from the corpus, which we refer to as “sentences” even though they are typically much longer than single sentences (but can be shorter also).

They are sampled such that the combined length is $\le$ 512 tokens.

### application 

According the training task of bert: Masked-LM、Next-Sequence-Prediction, so its more suitable for the similar task in application:

1. two long sentence relation inference tasks.
2. question answering (Cloze task)
3. ...



### code

https://github.com/google-research/bert

https://github.com/huggingface/pytorch-pretrained-BERT



### question

+ Why the strategy for mismatch problem is useful?

  

+ How many number of parameters in transformer?

  


+ How many sample is enough for transfer learning?

  

+ Did bert can achieve state of art in dependency parsing, semantic role labeling etc. area? why?

  

+ What's WordPiece tokenization ?

+ 

### excise

+ bert for ranking
+ bert for text generation
+ 

### reference

BERT visualization tool
https://github.com/jessevig/bertviz
The Illustrated BERT, Elmo, and Co.
http://jalammar.github.io/illustrated-bert/

https://medium.com/dissecting-bert/dissecting-bert-part-1-d3c3d495cdb3

https://www.reddit.com/r/MachineLearning/comments/9nfqxz/r_bert_pretraining_of_deep_bidirectional/ author of the paper







