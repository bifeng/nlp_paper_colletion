

### Task

Input:

+ Document level: In the document level, the algorithm obtains the relevant categories of a full document.

+ Paragraph level: In the paragraph level, the algorithm obtains the relevant categories of a single paragraph (a portion of a document).

+ Sentence level: In the sentence level, obtains the relevant categories of a single sentence (a portion of a paragraph).

+ Sub-sentence level: In the sub-sentence level, the algorithm obtains the relevant categories of sub-expressions within a sentence (a portion of a sentence )).



Output:

- Binary-class
- Multi-class
- Multi-label
- Hiearchical



### Awesome

https://github.com/fendouai/Awesome-Text-Classification



### Competition

+ 2018-DC-“达观杯”文本智能处理挑战赛

  [first](<https://github.com/ShawnyXiao/2018-DC-DataGrand-TextIntelProcess>) 

+ kaggle - Toxic Comment Classification Challenge [site](<https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge#description>) 

  

+ kaggle - Jigsaw Unintended Bias in Toxicity Classification [site](<https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification/overview>) 

  [1st](<https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification/discussion/103280#latest-619135>) 



### Scholars

[杨益銘](http://www.cs.cmu.edu/~yiming/) CMU: 文本分类



### STOA

+ https://paperswithcode.com/task/text-classification



### Datasets

+ 清华大学-新浪新闻 [site]([http://thuctc.thunlp.org/#%E4%B8%AD%E6%96%87%E6%96%87%E6%9C%AC%E5%88%86%E7%B1%BB%E6%95%B0%E6%8D%AE%E9%9B%86THUCNews](http://thuctc.thunlp.org/#中文文本分类数据集THUCNews)) 
+ 搜狗实验室-搜狐新闻 [site](<http://www.sogou.com/labs/resource/cs.php>) 



### Tools

[brightmart - text classification](https://github.com/brightmart/text_classification) 

https://github.com/kk7nc/Text_Classification

<https://github.com/liqunhit/NeuralClassifier>



### Literature review

+ A Survey of Text Classification Algorithms, Charu C. Aggarwal, ChengXiang Zhai, Mining Text Data Chapter 6, 2012 [paper](http://charuaggarwal.net/text-class.pdf) :star::star::star:
+ 



### Paper

#### Data Augmentation

+ EDA: Easy Data Augmentation Techniques for Boosting Performance on Text Classification Tasks, [arxiv](https://arxiv.org/abs/1901.11196) 

#### Label Embedding

基本思想：将label作为输入，也映射为低维向量，并影响或指导text embedding。

优点：

1. 学习到的label embedding作为该类别的原型（事实上，传统分类模型的分类层，其权重也是label embedding，也可作为类别的原型！所以，这不能是优点！！！）
2. 可以利用label相关的外部信息（如描述信息）

缺点：

1. 训练与测试不一致，类似于翻译中存在的问题



+ Label-Embedding for Image Classification
  Zeynep Akata, Florent Perronnin, Zaid Harchaoui, Cordelia Schmid IEEE 2015 [arxiv](<https://arxiv.org/abs/1503.08677>) 
+ Joint Embedding of Words and Labels for Text Classification
  Guoyin Wang, Chunyuan Li, Wenlin Wang, Yizhe Zhang, Dinghan Shen, Xinyuan Zhang, Ricardo Henao, Lawrence Carin ACL 2018 [arxiv](<https://arxiv.org/abs/1805.04174>) 



#### Evaluation

- An Evaluation of statistical approach to text categorization [[pdf](http://nyc.lti.cs.cmu.edu/yiming/Publications/cmu-cs-97-127.pdf)]
  Yang, Y.
  *Technical Report CMU-CS-97-127, Computer Science Department, Carnegie Mellon University, 1997*

#### Explanation

+ What Does a TextCNN Learn? Linyuan Gong, Ruyi Ji, [arxiv](<https://arxiv.org/abs/1801.06287>)  





