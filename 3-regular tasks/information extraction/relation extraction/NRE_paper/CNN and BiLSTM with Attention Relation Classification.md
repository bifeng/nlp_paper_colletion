## Relation Classification via Convolutional Deep Neural Network

### Question

+ how to represent the lexical features ?
+ 

### Contribution

+ position features

  the PF is the combination of the relative distances of the current word to $w_1$ (entity 1) and $w_2$ (entity 2).



### Architecture

![CNN](https://github.com/bifeng/daily_book_notes/raw/master/resource/cnn_re.png)

The lexical and sentence level features are respectively extracted and then directly <u>concatenated</u> to form the final feature vector.



lexical features: uses generic word embeddings as the source of base features. We select the word embeddings
of marked nouns and the context tokens.

| Features | Remark                          |
| -------- | ------------------------------- |
| L1       | Noun 1                          |
| L2       | Noun 2                          |
| L3       | Left and right tokens of noun 1 |
| L4       | Left and right tokens of noun 2 |
| L5       | WordNet hypernyms of nouns      |

## Attention-Based Bidirectional Long Short-Term Memory Networks for Relation Classification
attention mechanism: which can automatically focus on the words that have decisive effect on classification, to capture the most important semantic information in a sentence.



### Hyperparameters

dropout on the embedding layer, LSTM layer and the penultimate layer (倒数第二层).

We additionally constrain $L_2$-norms of the weight vectors by rescaling $w$ to have $∥w∥ = s$, whenever $∥w∥ > s$ after a gradient descent step.



