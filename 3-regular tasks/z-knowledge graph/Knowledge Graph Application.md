more:

“Industry-Scale Knowledge Graphs: Lessons and Challenges”, Communication of the ACM, 2019.

知识图谱的技术与应用（18版）[site1](<https://zhuanlan.zhihu.com/p/38056557>) [site2](<https://mp.weixin.qq.com/s/cOgG-7fUpgWht4NBFY3ADA>) :star::star::star:

知识图谱基本概念&工程落地常见问题

[一文揭秘！自底向上构建知识图谱全过程](https://mp.weixin.qq.com/s/lBeV6XWzk5bqNGiIMok-zw)

[知识图谱+Recorder︱中文知识图谱API与工具、科研机构与算法框架](<https://blog.csdn.net/sinat_26917383/article/details/66473253>) 

[项目实战--知识图谱初探]([http://www.shuang0420.com/2017/09/05/%E9%A1%B9%E7%9B%AE%E5%AE%9E%E6%88%98-%E7%9F%A5%E8%AF%86%E5%9B%BE%E8%B0%B1%E5%88%9D%E6%8E%A2/](http://www.shuang0420.com/2017/09/05/项目实战-知识图谱初探/))



实体（Entity）是指客观存在并可相互区别的事物，包括具体的人、事、物、抽象的概念或联系，知识库中包含多种类别的实体。

实体消歧

实体消歧（也称语义消歧）是专门用于解决同名实体产生歧义问题的技术。在实际的语言环境中，经常会遇到某个实体名称对应于多个命名实体对象的问题。

实体对齐

实体对齐（Entity Alignment）也被称作实体匹配（Entity Matching），是指对于异构数据源知识库中的各个实体，找出属于现实世界中的同一实体。

实体链接



知识库实体对齐技术综述，2016，[paper](http://crad.ict.ac.cn/CN/abstract/abstract3093.shtml) 



## Conference

+ AIcon 2019

  <https://aicon.infoq.cn/2019/beijing/#speakers>

  知识图谱在小米的落地与挑战 



## Architecture

![knowledge_graph_architecture](https://github.com/bifeng/daily_book_notes/raw/master/resource/knowledge_graph_architecture.png)





## Datasets

+ [CN-DBpedia](http://kw.fudan.edu.cn/cndbpedia/search/#) 复旦大学
  样例数据文件是txt格式，每行一条数据，每条数据是一个(实体名称，属性名称，属性值)的三元组，中间用tab分隔，具体如下所示:
  【复旦大学 简称 复旦】
  包含900万+的百科实体以及6700万+的三元组关系。其中mention2entity信息110万+，摘要信息400万+，标签信息1980万+，infobox信息4100万+。

  构建流程：

  ![CN_DBpedia_process.png](https://github.com/bifeng/daily_book_notes/raw/master/resource/CN_DBpedia_process.png)

  系统架构：

  ![CN_DBpedia_architecture.png](https://github.com/bifeng/daily_book_notes/raw/master/resource/CN_DBpedia_architecture.png)



- [zhishi.me](http://zhishi.me/) 

  



## Application

+ 一个中草药的知识服务系统：

  http://zcy.ckcest.cn/tcm/

  逆天 <http://zcy.ckcest.cn/tcm/qaos/profilenet>

+ <http://kw.fudan.edu.cn/> 复旦大学

+ <https://www.acemap.info/> 交大

+ [zhishi.me](http://zhishi.me/) 漆桂林老师团队

+ 微软小冰

  ![kg_example_xiaoice.png](https://github.com/bifeng/daily_book_notes/raw/master/resource/kg_example_xiaoice.png)

  We resort to a knowledge graph (KG) for query expansion.

  + First, we identify the topics from contextual user query Qc, e.g., “Beijing” from “tell me about Beijing”.
  + For each topic, we retrieve up to 20 most related topics from the KG, e.g., “Badaling Great Wall” and “Beijing snacks”. These topics are scored by their relevance using a boosted tree ranker Wu et al. [2010] trained on manually labeled training data.
  + Finally, we form a query by combining the topics from Qc and the related topics from the KG, and use the query to retrieve from the unpaired database up to 400 most relevant sentences as response candidates.

  refer: The Design and Implementation of XiaoIce, an Empathetic Social Chatbot
  Li Zhou, Jianfeng Gao, Di Li, Heung-Yeung Shum.

  

## Question

### 1. 领域知识建模方法？

如何定义领域知识的schema？

知识建模的两种方法：一种是自顶向下，一种是自底向上。

建模时需要考虑以下几个关键问题：

1）概念划分的合理性，如何描述知识体系及知识点之间的关联关系

+ Guarino, Nicola. "Formal ontology, conceptual analysis and knowledge representation." *International journal of human-computer studies* 43.5-6 (1995): 625-640.

2）属性定义方式，如何在冗余程度最低的条件下满足应用和可视化展现

3）事件、时序等复杂知识表示，通过匿名节点的方法还是边属性的方法来进行描述，各自的优缺点是什么

4）后续的知识扩展难度，能否支持概念体系的变更及属性的调整









