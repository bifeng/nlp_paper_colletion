### Awesome

https://github.com/Jiakui/awesome-bert





#### reg

http://fancyerii.github.io/2019/03/20/bert-reg/

https://github.com/google-research/bert/issues/74



#### rank

https://github.com/nyu-dl/dl4marco-bert

#### multi-task



#### papers

+ Yoav Goldberg. Assessing BERT’s syntactic abilities, 2019. arXiv:1901.05287.
+ BERT has a Mouth, and It Must Speak: BERT as a Markov Random Field Language Model, Alex Wang, Kyunghyun Cho, 2019 [arxiv](https://arxiv.org/abs/1902.04094) | [code](https://github.com/nyu-dl/bert-gen)  
+ To Tune or Not to Tune? Adapting Pretrained Representations to Diverse Tasks, Matthew Peters, Sebastian Ruder, Noah A. Smith, 2019 [arxiv](https://arxiv.org/abs/1903.05987) 

+ Linguistic Knowledge and Transferability of Contextual Representations-1903.08855

+ Distilling Task-Specific Knowledge from BERT into Simple Neural Networks, Raphael Tang, Yao Lu, Linqing Liu, Lili Mou, Olga Vechtomova, Jimmy Lin, [arxiv](https://arxiv.org/abs/1903.12136) 

  

+ Pretraining-Based Natural Language Generation for Text Summarization-1902.09243

+ Toward Fast and Accurate Neural Chinese Word Segmentation with Multi-Criteria Learning [arxiv](https://arxiv.org/pdf/1903.04190.pdf) 

  BERT + model compression + multi-criterial learing 

  

### code

https://github.com/google-research/bert

https://github.com/huggingface/pytorch-pretrained-BERT

### datasets

[multilingual](https://github.com/google-research/bert/blob/master/multilingual.md) Chinese

The entire Wikipedia dump for each language (excluding user and talk pages) was taken as the training data for each language.

we performed <u>exponentially smoothed weighting</u> of the data during pre-training data creation (and WordPiece vocab creation). So, high-resource languages like English will be under-sampled, and low-resource languages like Icelandic will be over-sampled.



### excise

- bert for ranking
- bert for text generation
- 