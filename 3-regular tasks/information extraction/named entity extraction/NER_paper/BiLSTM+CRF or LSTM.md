refer: [CRF_Layer_on_the_Top_of_BiLSTM](https://createmomo.github.io/2017/09/12/CRF_Layer_on_the_Top_of_BiLSTM_1/) series

more:

Neural architectures for named entity recognition, Guillaume Lample, Miguel Ballesteros, Sandeep Subramanian, Kazuya Kawakami, and Chris Dyer. NAACL 2016. [arxiv](https://arxiv.org/abs/1603.01360) :star::star::star::star:

Ashish Vaswani, Yonatan Bisk, Kenji Sagae, and Ryan Musa. 2016. Supertagging with lstms. In Proceedings of the NAACL international conference. pages 232–237.



## Question

1. Can the CRF layer learn the constraint of two (relation) entities in one sentence ?

2. Can add some constraint to the CRF layer to learn ?

3. what's the difference between the CRF layer with CRF++ ?

   

4. what's the loss function of CRF ?

   `crf_log_likelihood`

   (softmax can't express the dependency of labels)

   https://tensorflow.google.cn/api_docs/python/tf/contrib/crf/crf_log_likelihood

   ```python
   def crf_log_likelihood(inputs,
                          tag_indices,
                          sequence_lengths,
                          transition_params=None):
     """Computes the log-likelihood of tag sequences in a CRF.
   
     Args:
       inputs: A [batch_size, max_seq_len, num_tags] tensor of unary potentials
           to use as input to the CRF layer.
       tag_indices: A [batch_size, max_seq_len] matrix of tag indices for which we
           compute the log-likelihood.
       sequence_lengths: A [batch_size] vector of true sequence lengths.
       transition_params: A [num_tags, num_tags] transition matrix, if available.
     Returns:
       log_likelihood: A [batch_size] `Tensor` containing the log-likelihood of
         each example, given the sequence of tag indices.
       transition_params: A [num_tags, num_tags] transition matrix. This is either
           provided by the caller or created in this function.
     """
     # Get shape information.
     num_tags = inputs.get_shape()[2].value
   
     # Get the transition matrix if not provided.
     if transition_params is None:
       transition_params = vs.get_variable("transitions", [num_tags, num_tags])
   
     sequence_scores = crf_sequence_score(inputs, tag_indices, sequence_lengths,
                                          transition_params)
     log_norm = crf_log_norm(inputs, sequence_lengths, transition_params)
   
     # Normalize the scores to get the log-likelihood per example.
     log_likelihood = sequence_scores - log_norm
     return log_likelihood, transition_params
   ```

   

5. why don't use the combination of BiLSTM and CRF this two loss function ?



6. how to decrease the importance of 'O' tag in the loss ?

   This is impossible if you using the CRF as decoding (because the loss is calculate the sentence labels), but it possible for LSTM as decoding (the loss is calculate the independent label of word in a sentence). 

   In this paper: `<<Joint Extraction of Entities and Relations Based on a Novel Tagging Scheme>>`. It use a bias objective function to decrease the importance of 'O' tag and increase the importance of relational tags.

   

7. how to calculate the loss of padding element ?

   In the loss function `crf_log_likelihood`, there is an important parameter: 

   - **sequence_lengths**: A [batch_size] vector of true sequence lengths.

   https://tensorflow.google.cn/api_docs/python/tf/contrib/crf/crf_log_likelihood

   

   

8. Can it learning the context of feature and layer simultaneously in one architecture ?



## Architecture

we decompose the task of sequence labeling into two sub-problems in this paper: encoding and decoding.

The encoding layer: Learning the context of feature

The decoding layer: Learning the context of label



## encoding (BiLSTM)

Input: character embedding + word embedding

Every word in sentence is represented as a vector which includes the word’s character embedding and word embedding. The character embedding is initialized randomly. The word embedding usually is from a pre-trained word embedding file. All the embeddings will be fine-tuned during the training process.

Output: each label scores of each word

Every word in sentence will calculate the scores of each label



## decoding (CRF/LSTM)

Input: each label scores of each word

Output: label sequence

The label sequence which has the highest prediction score would be selected as the best answer.



### CRF layer

CRF is good at capturing the joint probability of the entire sequence of labels.



#### Emission score

The emission scores come from the BiLSTM layer. -> The labels score of each word.

We use $x_{iy_j}$ to represent the emission score. $i$ is the index of word and $y_j$ is the index of label. For instance, according the figure 2.1, $x_{i=1,yj=2}$=$x_{w1,B−Organization}$=0.1​ which means the score of $w_1$ as B-Organization is 0.1.

#### Transition score

The transition matrix has learned some useful constrains. -> The score between the labels transition.

We use $t_{y_iy_j}$ to represent a transition score. For example, $t_{B−Person,I−Person}$=0.9 means the score of label transition B−Person→I−Person is 0.9.

#### Loss function

The CRF loss function which is consist of the real path score and the total score of all the possible paths.

we supposed that every possible path has a score $P_i$ and there are totally $N$ possible paths.
$$
loss = \frac{P_{RealPath}}{P_{total}}=\frac{P_{RealPath}}{P_1+P_2+…+P_N}=\frac{e^{S_{RealPath}}}{e^{S_1}+e^{S_2}+…+e^{S_N}}
$$
$e$ is the mathematical constant $e$.

$S_i$ consists of 2 parts: $S_i$=Emission Score + Transition Score.

The $P_{total}$ is calculate using the idea of dynamic programing. In each steps,  it will calculate the **obs** and **previous**. **previous** stores <u>the final results of previous steps</u> (include the previous path). **obs** denotes the information from current word (include the emission score and transition score).



#### Infer the labels for a new sentence

**Step 1: Emission and transition scores from the BiLSTM-CRF model**

**Step 2: Start Inference**

The $P_{best}$ is calculate using Viterbi algorithm (he idea of dynamic programing). In each steps,  it will calculate the **obs** and **previous**. **previous** stores <u>the maximum score of the path which ends up with each label</u> (include the previous path). **obs** denotes the information from current word (include the emission score and transition score).

#### CRF layer can learn constrains from training data

The CRF layer could add some constrains to the final predicted labels to ensure they are valid. These constrains can be learned by the CRF layer automatically from the training dataset during the training process.

The constrains could be:

- The label of the first word in a sentence should start with “B-“ or “O”, not “I-“
- “B-label1 I-label2 I-label3 I-…”, in this pattern, label1, label2, label3 … should be the same named entity label. For example, “B-Person I-Person” is valid, but “B-Person I-Organization” is invalid.
- “O I-label” is invalid. The first label of one named entity should start with “B-“ not “I-“, in other words, the valid pattern should be “O B-label”
- …

With these useful constrains, the number of invalid predicted label sequences will decrease dramatically.

### LSTM layer

LSTM is capable of learning long-term dependencies.


At each time step $i$, the RNN decoder computes current decoder hidden state $h^{Dec}_{i+1}$ in terms of previous step tag $y_i$, previous step decoder hidden state $h^{Dec}_i$ and current step encoder hidden state $h^{Enc}_{i+1}$ ; the current output tag $y_{i+1}$ is decoded by using a softmax loss function and is further fed as an input to the next time step.





## Summary

### Practice 

For <u>sequence labeling problem</u> such as name entity recognition, relation extraction, attribute extraction, open information extraction, is easy converge for domain specific, but is very difficult converge for multiple domain.





