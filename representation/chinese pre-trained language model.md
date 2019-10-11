

#### Word2Vec

https://github.com/Embedding/Chinese-Word-Vectors

[HanLP(v_1.5.3)](https://github.com/hankcs/HanLP) is used for word segmentation.





#### FastText

https://fasttext.cc/docs/en/crawl-vectors.html

We used the [*Stanford word segmenter*](https://nlp.stanford.edu/software/segmenter.html) for Chinese.

[*Common Crawl*](http://commoncrawl.org/) and [*Wikipedia*](https://www.wikipedia.org/) - Chinese: [bin](https://dl.fbaipublicfiles.com/fasttext/vectors-crawl/cc.zh.300.bin.gz), [text](https://dl.fbaipublicfiles.com/fasttext/vectors-crawl/cc.zh.300.vec.gz) 



#### ELMO

https://github.com/HIT-SCIR/ELMoForManyLangs

Do remember tokenization!

Use [udpipe](http://ufal.mff.cuni.cz/udpipe) for **tokenization**!

| ELMO                     |                                                              |      |
| ------------------------ | ------------------------------------------------------------ | ---- |
| traditional Chinese ELMo | Wikipedia                                                    |      |
| simplified-Chinese ELMo  | xinhua proportion of [Chinese gigawords-v5](https://catalog.ldc.upenn.edu/ldc2011t13) [baidu-pan](https://pan.baidu.com/s/1RNKnj6hgL-2orQ7f38CauA) |      |
|                          |                                                              |      |



#### BERT

+ <https://github.com/ymcui/Chinese-BERT-wwm>

  中文分词 - 中文维基百科（包括简体和繁体）

+ <https://github.com/PaddlePaddle/LARK/tree/develop/ERNIE>

  中文实体mask - 百科类、资讯类、论坛对话类数据（简体）

  （将ERNIE从PaddlePaddle格式转换为TensorFlow格式）

+ <https://github.com/thunlp/OpenCLaP>

  字 - 民事文书、刑事文书、百度百科                                                                                                                                 



#### GPT-2

+ <https://github.com/Morizeyao/GPT2-Chinese>

#### RoBERTa

+ Chinese [site](<https://github.com/brightmart/roberta_zh>) 



#### Question

+ Different output vectors for same sentences

It seems the unstable output is resulted from the stateful LSTM in ELMo. But empirically, it does not hurt the performance (**result can't replicate ! How to deal with it?**).

I guess its something related to LSTM internal states as stated in AllenNLP note (Notes on statefulness and non-determinism) :
<https://github.com/allenai/allennlp/blob/master/tutorials/how_to/elmo.md>

https://github.com/HIT-SCIR/ELMoForManyLangs/issues/45

https://github.com/HIT-SCIR/ELMoForManyLangs/issues/30

+ continue training with pretrained models

  https://github.com/HIT-SCIR/ELMoForManyLangs/issues/60

  i am afraid it is impossible to use softmax. you can try some softmax-free method like the one in <https://arxiv.org/abs/1902.11269>

  

+ 









