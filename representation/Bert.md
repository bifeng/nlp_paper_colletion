### Awesome

https://github.com/Jiakui/awesome-bert

#### rank

https://github.com/nyu-dl/dl4marco-bert

#### multi-task



#### relate papers

+ BERT has a Mouth, and It Must Speak: BERT as a Markov Random Field Language Model, Alex Wang, Kyunghyun Cho, 2019 https://arxiv.org/abs/1902.04094?context=cs
+ 

### code

https://github.com/google-research/bert

https://github.com/huggingface/pytorch-pretrained-BERT

### datasets

[multilingual](https://github.com/google-research/bert/blob/master/multilingual.md) Chinese

The entire Wikipedia dump for each language (excluding user and talk pages) was taken as the training data for each language.

we performed <u>exponentially smoothed weighting</u> of the data during pre-training data creation (and WordPiece vocab creation). So, high-resource languages like English will be under-sampled, and low-resource languages like Icelandic will be over-sampled.



### question

- Why the strategy for mismatch problem is useful?

  

- How many number of parameters in transformer?

  

- How many sample is enough for transfer learning?

  

- Did bert can achieve state of art in dependency parsing, semantic role labeling etc. area? why?

  

- What's WordPiece tokenization ?

- 

### excise

- bert for ranking
- bert for text generation
- 