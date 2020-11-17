#### textrank

关键词提取 - 1）BOW思想，忽略语序；2）采用共现关系（co-occurrence）构造任两点之间的边（窗口） - 构成边；3）边的权重为1。

自动摘要（关键句提取）- 1）BOW思想，忽略语序；2）一般认为全部句子都是相邻的 - 构成边；3）相似度矩阵（如BM25等）- 边的权重。





#### code

https://en.wikipedia.org/wiki/PageRank#Python

keyword extraction [jieba](https://github.com/fxsjy/jieba/blob/master/jieba/analyse/textrank.py) - create Undirect Weighted Graph and hard code

summarization [textrank](https://github.com/DerwenAI/pytextrank) - use networkx library

#### application

+ keyword extraction

  - In place of web pages, we use n-grams words
  - co-occurrence between any two words in n-grams window is used as an equivalent to the web page transition probability

  

+ summarization

  - In place of web pages, we use sentences
  - Similarity between any two sentences is used as an equivalent to the web page transition probability

