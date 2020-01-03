

Keyword: text-to-sql, nl2sql, nl2code, seq2sql, Sequence2SQL, sequence to SQL, sql parsing, code generation, semantic parsing



### SOTA

+ https://github.com/sebastianruder/NLP-progress/blob/master/english/semantic_parsing.md
+ <https://www.paperswithcode.com/task/semantic-parsing>
+ <https://paperswithcode.com/task/text-to-sql>
+ https://paperswithcode.com/task/code-generation



### Conference

+ First IEEE International conference on Conversational Data & Knowledge Engineering
  (CDKE 2019) 

  <https://www.cdke.org/>



### Company

keyword: **askdata**, **conversational data access**, **Human2SQL**, **数据问答**

+ Google

  Dhamdhere, Kedar, et al. "Analyza: Exploring data with conversation." Proceedings of the 22nd International Conference on Intelligent User Interfaces. ACM, 2017.

+ microsoft

+ Salesforce 

  <https://einstein.ai/products>

+ askdata

  http://www.askdata.com/

  <https://github.com/AskdataInc>

  > NLP Pipeline
  >
  > NLP stands for **Natural Language Processing** pipeline. It’s a sequence of algorithms that will process the natural language query. Different algos are run in parallel to identify the intent of the user and the data query.

+ <https://github.com/prijindal/askdata>

  Forked from <https://openforge.gov.in/plugins/git/maa-098-askdata/askdata>

+ <https://www.dianaai.com/>

  Conversational BI.

+ Tableau
Tableau2019.1推出数据问答功能
  https://www.tableau.com/products/new-features/ask-data

+ 亿信华辰（BI）

  智能数据问答平台

  <http://www.esensoft.com/products/esenask.html>
  
+ 追一科技


### Competition

+ [首届中文NL2SQL挑战赛](<https://tianchi.aliyun.com/competition/entrance/231716/information>)

  追一科技 - 2019

  4万条有标签数据作为训练集，1万条无标签数据作为测试集。

  SOTA:(average of logic form accuracy and execution accuracy)

  | Model                                                        | accuracy  |
  | ------------------------------------------------------------ | --------- |
  | [1th](<https://github.com/xyzhang16/tianchi-nl2sql-top1>) [1th](<https://github.com/nudtnlp/tianchi-nl2sql-top1>) M-SQL(8个子任务) | 0.9219    |
  | 2th                                                          | 0.9143    |
  | [3th](<https://github.com/beader/tianchi_nl2sql>)            | 0.9106    |
  | [6th](https://github.com/eguilg/nl2sql)                      | 0.9018    |
  | [15th](https://github.com/yscoder-github/nl2sql-tianchi)     | 0.8338    |
  | [baseline](<https://github.com/ZhuiyiTechnology/nl2sql_baseline>) [baseline](<https://github.com/bojone/bert_in_keras/blob/master/nl2sql_baseline.py>) | 0.51 0.58 |


### Datasets

+ ATIS (The Air Travel Information System)

  ATIS is a context-dependent semantic parsing/text-to-SQL datasets.

  5,280 user questions for a flight-booking task

  SOTA:(accuracy)

  | Model                                                        | question-based split | query-based split |
  | ------------------------------------------------------------ | -------------------- | ----------------- |
  | Seq2Seq with copying [Finegan-Dollak et al., 2018](http://arxiv.org/abs/1806.09029) [code](https://github.com/jkkummerfeld/text2sql-data) | 51%                  | 32%               |

  notes: question-based splits allow queries to appear in both train and test, query-based split ensures each query is in only one.

+ [WikiSQL](<https://github.com/salesforce/WikiSQL>) **单表**

  Salesforce - 2017

  87,673 examples of questions, SQL queries, and database tables built from 26,521 tables. 

  特点：SQL的形式较为简单，不涉及到高级用法（如不需要联合多张表格查询）

  条件的表达只支持最基础的>、<、=，条件之间的关系只有and，不支持聚组、排序、嵌套等其它众多常用的SQL语法，不需要联合多表查询答案，真实答案所在表格已知等诸多问题的简化。

  SOTA:(execution accuracy)



| Model                                                        | Dev  | Test |
| ------------------------------------------------------------ | ---- | ---- |
| [X-SQL+ Execution-Guided Decoding (He 2019)](https://www.microsoft.com/en-us/research/publication/x-sql-reinforce-context-into-schema-representation/) | 92.3 | 91.8 |
| [SQLova + Execution-Guided Decoding (Hwang 2019)](https://ssl.pstatic.net/static/clova/service/clova_ai/research/publications/SQLova.pdf) | 90.2 | 89.6 |
| [IncSQL + Execution-Guided Decoding (Shi 2018)](https://arxiv.org/pdf/1809.05054.pdf) | 87.2 | 87.1 |
| baseline [SQLNet](https://arxiv.org/abs/1711.04436) [code](https://github.com/xiaojunxu/SQLNet) |      |      |

  SQLNet 

  SQLNet 是 WikiSQL 数据集上的一个 baseline 模型。根据 WikiSQL 数据集中 SQL 语句的特征，预测 SQL 这一任务被 SQLNet 解耦为了 6 个子任务，包括选择哪一列的 Select-Column、使用什么聚合函数的 Select-Aggregation、有几个条件的 Where-Number、筛选条件是针对哪几列的 Where-Column、各个条件的操作符 Where-Operator 以及各个条件的条件值 Where-Value。

  X-SQL

  X-SQL 是微软 Dynamics 365 提出一种方案。这个方案同样继承了解耦任务的思路，将预测 SQL 分解为 6 个子任务。但不同于 SQLova，X-SQL 引入了更多创新性的一些改进。 

  [SQLova](<https://github.com/naver/sqlova>)

  SQLova 是韩国 Naver 提出的一种模型，全名为 Search & QLova，是作者们所在部门的名称。该方案继承了 SQLNet 任务解耦的思路，同样使用 6 个子任务来预测 SQL。但是并没有提出一些创新性的解决方案。相比SQLNet，不同之处在于，SQLova 使用了 BERT 来作为模型的输入表达层，代替了词向量。

+ [Spider](<https://yale-lily.github.io/spider>) **多表**

  Yale Semantic Parsing and Text-to-SQL Challenge - 2018

  Spider is a large-scale [*complex and cross-domain*](https://medium.com/@tao.yu/spider-one-more-step-towards-natural-language-interfaces-to-databases-62298dc6df3c) semantic parsing and text-to-SQL dataset.

  It consists of 10,181 questions and 5,693 unique complex SQL queries on 200 databases with multiple tables covering 138 different domains. In Spider 1.0, different complex SQL queries and databases appear in train and test sets.

  To do well on it, systems must *generalize well to not only new SQL queries but also new database schemas*.

  特点： 涉及到查询语句嵌套、多表联合查询、并且支持几乎所有SQL语法的用法，用户问句的表达方式和语义信息也更丰富，更贴近于真实场景

  SOTA: (Exact Set Match without Values - Not execution accuracy)

  | Model                                                        | Dev      | Test     |
  | ------------------------------------------------------------ | -------- | -------- |
  | IRNet v2 + BERT  Microsoft Research Asia                     | **63.9** | **55.0** |
  | GIRN + BERT  Anonymous                                       | 60.2     | 54.8     |
  | IRNet + BERT  Microsoft Research Asia [(Guo and Zhan et al., ACL '19)](https://arxiv.org/abs/1905.08205)  [code](https://github.com/zhanzecheng/IRNet) | 61.9     | 54.7     |

+ [SParC](<https://github.com/taoyds/sparc>)

  Yale & Salesforce Semantic Parsing and Text-to-SQL in Context Challenge - 2019

  **SParC** is a dataset for cross-domain **S**emantic **Par**sing in **C**ontext. It is the context-dependent/multi-turn version of the [**Spider task**](https://yale-lily.github.io/spider). SParC consists of 4,298 coherent question sequences (12k+ unique individual questions annotated with SQL queries), obtained from user interactions with 200 complex databases over 138 domains.

  SOTA: (Exact Set Match without Values - Not execution accuracy)

  | Model                                                        | Question Match | Interaction Match |
  | ------------------------------------------------------------ | -------------- | ----------------- |
  | EditSQLYale  University & Salesforce Research[(Zhang et al. EMNLP '19)](https://arxiv.org/abs/1909.00786) [code](https://github.com/ryanzhumich/sparc_atis_pytorch) | **47.9**       | **25.3**          |
  | CD-Seq2Seq  Yale University & Salesforce Research[(Yu et al. ACL '19)](https://arxiv.org/abs/1906.02285) [code](https://github.com/ryanzhumich/sparc_atis_pytorch) | 23.2           | 7.5               |



+ [8 traditional single datasets: ATIS, GeoQuery, Academic, Advising, Scholar etc.](https://github.com/jkkummerfeld/text2sql-data)



### Methods

1. 高质量的语法树和词典来构建语义解析器，再将自然语言语句转化为相应的SQL

2. 端到端与SQL特征规则相结合

   将select与where两个子句，拆分为不同原子操作，如select包括agg(count/sum)、column等，where包括条件(and/or)、column 、value等，不同原子由不同子任务预测。

   端到端训练方式 - 1）多个子任务multi-task learning；2）多个子任务parallel training

   其中，子任务主要为序列标注+分类两种。

   





### Papers

[你已经是个成熟的表格了，该学会自然语言处理了-  微软研究院AI头条](https://mp.weixin.qq.com/s/gZ4N18jvM_0oUvOaKBBxfQ)



+ Google 2017 [Analyza: Exploring Data with Conversation](https://static.googleusercontent.com/media/research.google.com/zh-CN//pubs/archive/45791.pdf) 

  

+ Model-based Interactive Semantic Parsing: A Unified Framework and A Text-to-SQL Case Study
  Ziyu Yao, Yu Su, Huan Sun, Wen-tau Yih. Facebook. EMNLP 2019 [arxiv](<https://arxiv.org/abs/1910.05389>) 

+ Towards Complex Text-to-SQL in Cross-domain Database, (ACL’19)

  [blog](https://mp.weixin.qq.com/s/bGpTU0fA5bWvSERBokMKSA) 



+ Semantic Parsing with Syntax- and Table-Aware SQL Generation, Yibo Sun, Duyu Tang, Nan Duan, Jianshu Ji , Guihong Cao , Xiaocheng Feng , Bing Qin, Ting Liu, Ming Zhou, ACL 2018 

  ![nl2sql](https://github.com/bifeng/nlp_paper_notes/raw/master/image/nl2sql_1.png)



+ Improving Text-to-SQL Evaluation Methodology [arxiv](http://arxiv.org/abs/1806.09029) [Data and System](https://github.com/jkkummerfeld/text2sql-data) 

  > first propose the evaluation method: question-based split and query-based split.

+ *SyntaxSQLNet:* [Syntax Tree Networks for Complex and Cross-Domain Text-to-SQL Task](https://arxiv.org/abs/1810.05237)
+ *Zero-shot Parser:* [Decoupling Structure and Lexicon for Zero-Shot Semantic Parsing](https://arxiv.org/abs/1804.07918)
+ *A Detailed Analysis of WikiSQL:* [What It Takes to Achieve 100% Condition Accuracy on WikiSQL](http://aclweb.org/anthology/D18-1197)
+ *Coarse2fine*: [Coarse-to-Fine Decoding for Neural Semantic Parsing](https://arxiv.org/pdf/1805.04793.pdf)
+ *SQL Evaluation Methodology*: [Improving Text-to-SQL Evaluation Methodology](https://arxiv.org/abs/1806.09029)
+ *User Feedback via Dialog:* [DialSQL: Dialogue Based Structured Query Generation](http://cs.ucsb.edu/~ysu/papers/acl18_dialsql.pdf)
+ *Involving Context in the Task:* [Learning to Map Context-Dependent Sentences to Executable Formal Queries](http://alanesuhr.com/atis.pdf)
+ *TypeSQL:* [TypeSQL: Knowledge-based Type-Aware Neural Text-to-SQL Generation](https://arxiv.org/abs/1804.09769)
+ *SQLNet:* [SQLNet: Generating Structured Queries From Natural Language Without Reinforcement Learning](https://arxiv.org/abs/1711.04436)
+ *Seq2SQL:* [Seq2SQL: Generating Structured Queries from Natural Language using Reinforcement Learning](https://arxiv.org/abs/1709.00103)
+ *Syntactic Neural Models:* [A Syntactic Neural Model for General-Purpose Code Generation](https://arxiv.org/abs/1704.01696), [Abstract Syntax Networks for Code Generation and Semantic Parsing](https://arxiv.org/abs/1704.07535)
+ *NL2SQL:* [Learning a Neural Semantic Parser from User Feedback](https://arxiv.org/pdf/1704.08760.pdf)
+ *Seq2Tree:* [Learning a Neural Semantic Parser from User Feedback](https://arxiv.org/pdf/1704.08760.pdf)
+ *NaLIR*: [Constructing an Interactive Natural Language Interface for Relational Databases](http://www.vldb.org/pvldb/vol8/p73-li.pdf)
+ *Paraphrase:* [Cross-domain Semantic Parsing via Paraphrasing](https://arxiv.org/abs/1704.05974)
+ *NL2WebAPI:* [Building Natural Language Interfaces to Web APIs](http://cs.ucsb.edu/~ysu/papers/cikm17_nl2api.pdf)
+ 



### Talks, Blogs, or Books

- [Spider: One More Step Towards Natural Language Interfaces to Databases](https://yale-lily.github.io/spider)
- [How to Talk to Your Database](https://blog.einstein.ai/how-to-talk-to-your-database/)
- [Natural Language Interfaces to Databases (NLIDB)](http://jonaschapuis.com/2017/12/natural-language-interfaces-to-databases-nlidb/) 
- [ACL 2018 Tutorial on Neural Semantic Parsing](https://github.com/allenai/acl2018-semantic-parsing-tutorial)
- [Natural Language Data Management and Interfaces](http://www.morganclaypoolpublishers.com/catalog_Orig/product_info.php?products_id=1286)
- [A Syntactic Neural Model for General-Purpose Code Generation](https://vimeo.com/234954608)
- [Learning to Map Context-Dependent Sentences to Executable Formal Queries](http://alanesuhr.com/sia2018-slides.pdf)



### Tools

+ allennlp-semparse

  A framework for building semantic parsers (including neural module networks) with AllenNLP, built by the authors of AllenNLP

  <https://github.com/allenai/allennlp-semparse>

+ [Coarse2fine](https://github.com/donglixp/coarse2fine)

+ [SyntaxSQL](https://github.com/taoyds/syntaxSQL)

+ [TypeSQL](https://github.com/taoyds/typesql)

+ [SQLNet](https://github.com/xiaojunxu/SQLNet)

+ [NL2Code](https://github.com/pcyin/NL2code)

+ [TRANX](<https://github.com/pcyin/tranX>)







refered:

https://medium.com/@tao.yu/awesome-sequence-to-sql-and-semantic-parsing-1d7656861679

[NL2SQL：弱监督学习与有监督学习完成进阶之路](<https://mp.weixin.qq.com/s/kXtaqrhN24BrCob1W0LIjQ>)

[NL2SQL 这个领域研究进展如何了？ 大家如何看待WikiSQL的准确度达到90%以上 ？](<https://www.zhihu.com/question/323109035>)