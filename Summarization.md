https://en.wikipedia.org/wiki/Automatic_summarization



### Task

+ short text summarization
+ long text summarization
+ single-doc summarization
+ multi-doc summarization



### Awesome

+ <https://github.com/icoxfog417/awesome-text-summarization>
+ 



### challenge

- NLPCC 2017 Task 3

  <https://biendata.com/competition/nlptask03/>

- Byte Cup 2018 国际机器学习竞赛 [site](https://www.biendata.com/competition/bytecup2018/) 

  **文章标题自动生成**

  [1st](https://mp.weixin.qq.com/s/2Mh68gfbG_5gKnoICuRmeA) 

  [3rd](https://github.com/iwangjian/ByteCup2018) 

+ 

### STOA

+ <https://summari.es/> 

  <https://github.com/lil-lab/newsroom>

+ 



### Dataset

+ two sentence-level summarization datasets

  DUC-2004

  Gigaword



+ long text summarization datasets

  The CNN / Daily Mail dataset (non-anonymized) [site](<https://github.com/abisee/cnn-dailymail>) 



+ WikiHow: A Large Scale Text Summarization Dataset [site](<https://github.com/mahnazkoupaee/WikiHow-Dataset>) 

+ Scientific Document Summarization Corpus and Annotations from the WING NUS group.

  <https://github.com/WING-NUS/scisumm-corpus>

+ [Yale SciSumm Dataset](https://cs.stanford.edu/~myasu/projects/scisumm_net/)

+ [Multi-News](<https://github.com/Alex-Fabbri/Multi-News>) 



+ 中文
+ 哈工大-新浪微博短文本摘要 [LCSTS](<http://icrc.hitsz.edu.cn/Article/show/139.html>) [baidupan]([download](https://pan.baidu.com/s/1szq0Wa60AS5ISpM_SNPcbA), pwd is ayn6) 
+ 港大-多文本摘要 [site](<http://www1.se.cuhk.edu.hk/~textmine/dataset/ra-mds/>) 
+ 个人-教育培训行业主流垂直媒体-中文语料库 [site](<https://github.com/wonderfulsuccess/chinese_abstractive_corpus>) 
+ 个人-新浪微博 [site](<https://www.jianshu.com/p/8f52352f0748>) [baidupan](百度网盘：<https://pan.baidu.com/s/1NWe6K33GMTp4Wk7CwaGotA>
  密码：4k12) 
+ 



### Literature Review

+ Searching for Effective Neural Extractive Summarization: What Works and What’s Next [site](<http://pfliu.com/InterpretSum/interpretSum.html>) 

- Text Summarization Techniques: A Brief Survey, Mehdi Allahyari, Seyedamin Pouriyeh, Mehdi Assefi, Saeid Safaei, Elizabeth D. Trippe, Juan B. Gutierrez, Krys Kochut, 2017 [arxiv](https://arxiv.org/abs/1707.02268) :star::star:
- A survey of text summarization techniques, *Ani Nenkova, Kathleen R. McKeown*. In Mining Text Data (pp. 43-76). Springer US, 2012 [paper](https://pdfs.semanticscholar.org/8d7f/6dc8b0b9101580cc96f1f303d1eba3d590af.pdf) focus on extractive summarization methods :star::star::star::star::star:
- A Survey of Text Summarization Extractive Techniques,  Vishal Gupta, Gurpreet Singh Lehal, 2010 [paper](http://www.learnpunjabi.org/pdf/survey-paper.pdf) :star::star::star:





### Paper



+ A Simple Theoretical Model of Importance for Summarization, ACL 2019, **Outstanding paper awards** [paper](https://www.aclweb.org/anthology/P19-1101) 
+ BottleSum: Unsupervised and Self-supervised Sentence Summarization using the Information Bottleneck Principle



+ Get To The Point: Summarization with Pointer-Generator Networks, Abigail See, Peter J. Liu, Christopher D. Manning, ACL 2017 [arxiv](https://arxiv.org/abs/1704.04368) [blog](<http://www.abigailsee.com/2017/04/16/taming-rnns-for-better-summarization.html>) [code](<https://github.com/abisee/pointer-generator>) [pytorch code](https://github.com/atulkum/pointer_summarizer) :star::star::star:

+ A Deep Reinforced Model for Abstractive Summarization
  Romain Paulus, Caiming Xiong, Richard Socher, [arxiv](<https://arxiv.org/abs/1705.04304>) 

+ Abstractive Text Summarization Using Sequence-to-Sequence RNNs and Beyond
  Ramesh Nallapati, Bowen Zhou, Cicero Nogueira dos santos, Caglar Gulcehre, Bing Xiang CoNLL 2016 [arxiv](<https://arxiv.org/abs/1602.06023>) 




- Retrieve, Rerank and Rewrite: Soft Template Based Neural Summarization. Ziqiang Cao, Wenjie Li, Sujian Li, Furu Wei. ACL 2018 [arxiv](https://aclanthology.info/papers/P18-1015/p18-1015) 
- Global Encoding for Abstractive Summarization, Junyang Lin, Xu Sun, Shuming Ma, Qi Su, ACL 2018 [arxiv](https://arxiv.org/abs/1805.03989) 
- Fast Abstractive Summarization with Reinforce-Selected Sentence Rewriting, Yen-Chun Chen, Mohit Bansal, ACL 2018 [arxiv](https://arxiv.org/abs/1805.11080?context=cs.LG) 



- Bottom-Up Abstractive Summarization, Sebastian Gehrmann, Yuntian Deng, **Alexander M. Rush**, EMNLP 2018 [arxiv](https://arxiv.org/abs/1808.10792) **SOTA**
- Don't Give Me the Details, Just the Summary! Topic-Aware Convolutional Neural Networks for Extreme Summarization, Shashi Narayan, Shay B. Cohen, Mirella Lapata, EMNLP 2018 [arxiv](https://arxiv.org/abs/1808.08745) 



#### Integer linear programming 

<http://l2r.cs.illinois.edu/tutorials.html>





#### submodular function

- A class of submodular functions for document summarization, Hui Lin, Jeff Bilmes, ACL 2011 [paper](http://www.anthology.aclweb.org/P/P11/P11-1052.pdf) :star::star::star:
- Multi-document summarization via budgeted maximization of submodular functions, Hui Lin, Jeff Bilmes, NAACL 2010 [paper](http://www.aclweb.org/anthology/N10-1134) :star::star::star:
- 



#### centroid-based

+ Centroid-based summarization of multiple documents: sentence extraction, utility-based evaluation, and user studies, [paper](​https://www.aclweb.org/anthology/W00-0403) :star::star::star::star:

#### graph-based



#### optimization-based

+ A study of global inference algorithms in multi-document summarization, R McDonald, European Conference on Information Retrieval, 2007 :star::star::star:



### Tools

+ <https://github.com/policeme/transformer-pointer-generator>

+ <https://github.com/google-research/bert/issues/352>

  <https://github.com/nlpyang/BertSum>
  
  <https://github.com/nlpyang/hiersumm>
  
  ...
  
+ [Sumy](https://github.com/miso-belica/sumy) :star::star::star::star::star: 

+ [**SweSum - An automatic text summarizer for Swedish and other languages**](http://swesum.nada.kth.se/index.html) 

  [**What is text summarization?**](http://www.dsv.su.se/~hercules/textsammanfattningeng.html) 


