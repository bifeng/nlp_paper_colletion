## Keyword

OpenIE



## Tasks

Oren Etzioni 首次提出Open Information Extraction概念.



## Scholars

+ Oren Etzioni 

  the CEO of the Allen Institute for AI (AI2), 华盛顿大学图灵中心主任

+ 



## Literature Review

+ A Survey on Open Information Extraction, COLING 2018 [paper](https://aclweb.org/anthology/papers/C/C18/C18-1326/) 

  > Challenge:
  >
  > （1）自动化。不需要预先定义schema，不需要标注数据；或者定义少量的schema，标注少量的数据
  >
  > （2）数据依赖。理想中的OIE是**domain-independent**的。
  >
  > （3）计算高效。“Open IE systems must be computationally efﬁcient. Enabling fast extraction over huge datasets, shallow linguistic features, like POS tags, are to be preferred over deep features that are derived from parse trees”
  >
  > 
  >
  > Direction:
  >
  > 第一：learning-based
  >
  > 第二：rule-based
  >
  > 第三：clause-based
  >
  > 第四：approaches capturing inter-proposition relationships

+ [Extracting Knowledge from Twitter and the Web](http://aritter.github.io/thesis.pdf)
  Alan Ritter
  Ph.D. Thesis, University of Washington 2013



## Paperlist

+ <https://github.com/NPCai/Open-IE-Papers>

+ <https://github.com/gkiril/oie-resources>





## Paper

### Seq2seq

+ Extracting Relational Facts by an End-to-End Neural Model with Copy Mechanism, ACL2018
+ 

### Question Answering

+ Open Information Extraction from Question-Answer Pairs



### Chinese

+ Jia S, Li M, Xiang Y. Chinese Open Relation Extraction and Knowledge Base Establishment[J]. ACM Transactions on Asian and Low-Resource Language Information Processing (TALLIP), 2018, 17(3): 15. [code](<https://github.com/lemonhu/open-entity-relation-extraction>) [code](<https://github.com/TJUNLP/COER>) 
+ ZORE: A Syntax-based System for Chinese Open Relation Extraction. Likun Qiu, Yue Zhang. EMNLP 2014 [paper](<https://www.aclweb.org/anthology/D14-1201/>) 
+ Chinese Open Relation Extraction for Knowledge Acquisition. 2014

## Datasets

+ [The Automatic Content Extraction(ACE)](https://www.ldc.upenn.edu/collaborations/past-projects/ace/annotation-tasks-and-specifications) 



## Tools

+ ReVerb
+ TextRunner



## Summary

### Rule-based

第一是基于内容的匹配，例如写正则表达式；

第二是基于结构的匹配，基于句法分析。

实际上，这两条线从相关学术界和工业界的一些工作来看，在**垂直场景**下都是可以work的。

前者需要业务专家的参与，后者需要好的句法分析和业务专家，如果句法分析是数据驱动的，且通用句法分析不满足要求，则是将直接的关系标注任务转移到了句法分析，其实这是很有启发性的一条思路。

### Unsupervised-based

+ Unsupervised Open Relation Extraction. Hady Elsahar, Elena Demidova, Simon Gottschalk, Christophe Gravier, Frederique Laforest. ESWC 2017 [arxiv](<https://arxiv.org/abs/1801.07174>) 

  > 对relation进行clustering

+ 

### Semi-supervised-based

Bootstrapping (Semi-supervised)

+ Neural Snowball for Few-Shot Relation Learning
  Tianyu Gao, Xu Han, Ruobing Xie, Zhiyuan Liu, Fen Lin, Leyu Lin, Maosong Sun. AAAI 2020 [arxiv](<https://arxiv.org/abs/1908.11007>) 

+ StatSnowball: a Statistical Approach to Extracting Entity Relationships

  Jun Zhu, Zaiqing Nie, Xiaojing Liu, Bo Zhang, Ji-Rong Wen [paper](<https://www.microsoft.com/en-us/research/wp-content/uploads/2016/06/p101.pdf>) 

+ Snowball: Extracting Relations from Large Plain-Text Collections
  Eugene Agichtein, Luis Gravano 2000 [paper](<http://www.mathcs.emory.edu/~eugene/papers/dl00.pdf>) 



+ Ruidong Wu, Yuan Yao, Xu Han, Ruobing Xie, Zhiyuan Liu, Fen Lin, Leyu Lin, Maosong Sun. Open Relation Extraction: Relational Knowledge Transfer from Supervised Data to Unsupervised Data. 2019 Conference on Empirical Methods in Natural Language Processing and 9th International Joint Conference on Natural Language Processing (EMNLP-IJCNLP 2019).

### Distant Supervision





## Application



### **Washington**

KnowItAll <https://github.com/knowitall>, TextRunner...

<http://reverb.cs.washington.edu/>



<https://openie.allenai.org/>

<https://github.com/dair-iitd/OpenIE-standalone>



+ Stanovsky, G., Michael, J., Zettlemoyer, L., & Dagan, I. (2018, June). Supervised open information extraction. In *Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long Papers)* (pp. 885-895).  [pdf](https://www.aclweb.org/anthology/N18-1081) | [code](https://allennlp.org/models#open-information-extraction) 

  > formulate of Open IE as a sequence tagging problem, addressing challenges such as encoding multiple extractions for a predicate
  >
  > introduce a novel approach that can extract multiple, overlapping tuples for each sentence 

+ Fader, Anthony, Stephen Soderland, and Oren Etzioni. "Identifying relations for open information extraction." *Proceedings of the conference on empirical methods in natural language processing*. Association for Computational Linguistics, 2011. :star::star::star::star:

+ Etzioni, O., Fader, A., Christensen, J., & Soderland, S. (2011, June). Open information extraction: The second generation. In *Twenty-Second International Joint Conference on Artificial Intelligence*.

+ Yates, A., Cafarella, M., Banko, M., Etzioni, O., Broadhead, M., & Soderland, S. (2007, April). Textrunner: open information extraction on the web. In *Proceedings of Human Language Technologies: The Annual Conference of the North American Chapter of the Association for Computational Linguistics: Demonstrations* (pp. 25-26). Association for Computational Linguistics.

+ Banko, M., Cafarella, M. J., Soderland, S., Broadhead, M., & Etzioni, O. (2007, January). Open information extraction from the web. In *Ijcai* (Vol. 7, pp. 2670-2676). :star::star::star::star:



### **Stanford**

<https://nlp.stanford.edu/software/openie.html>

Socher, R., Chen, D., Manning, C. D., & Ng, A. (2013). Reasoning with neural tensor networks for knowledge base completion. In *Advances in neural information processing systems* (pp. 926-934).



### **IBM Watson**

PRISMATIC



### **Microsoft**

+ Cui, L., Wei, F., & Zhou, M. (2018). Neural open information extraction. *arXiv preprint arXiv:1805.04270*.

  > seq2seq









