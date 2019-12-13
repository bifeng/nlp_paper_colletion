实际上，NLP 的很多场景都几乎不可能从技术上完美解决，只能在实际中通过技术能力和产品设计的平衡来提高用户的综合体验。—— 小米公司自然语言处理首席科学家 王斌

## 挑战

NLP 的发展还存在很多挑战，很多专家都有过总结。这里提我个人认为最重要的两点。

第一是标注数据问题。当前主流方法的效果取决于标注数据的规模和质量。获得大规模的高质量标注数据永远是个难题。要解决这个问题，一种可能的方法是通过自动标注或者半自动标注或者自然标注来扩大标注的数据量。另一种可能的方法是通过弱监督或半监督方法来充分利用大规模的未标注数据。

第二是轻量级优质模型问题。当前的主流模型需要消耗大量资源进行训练，这种趋势目前看来有增无减。如何得到轻量级的优质模型是一个挑战性问题。可能的方法包括对现有模型的裁剪甚至另辟新路提出新的模型。

—— 小米公司自然语言处理首席科学家 王斌

## 应用领域

### 电商

## 应用场景

### 搜索

#### 检索系统



#### 问答系统



### 推荐



### 广告



### 舆情分析



### 其他

#### 信息抽取

关系抽取

事件抽取



#### 文本溯源（文档查重）

句子级

输入：一批待查句子和一个源数据集，

输出：判断待查句子是否改编自源数据集中的句子，如果是则找出相应的源句子。



案例：

<https://biendata.com/competition/smpetst2018/data/>



文档级

...



案例：

<https://biendata.com/competition/smpetst2019/>





#### 公告信息抽取

输入：上市公司年报pdf文件

输出：财务信息的格式化数据



案例：

<https://biendata.com/competition/ccks_2019_5/>



#### 智能问答（知识图谱）*

任务描述：解析问题中涉及的实体及属性，从知识库查找对应的属性值，其中问题均为客观事实型，不包含主观因素。



准备数据：知识库（实体、属性、属性值的三元组）、问题答案标注数据集



输入输出示例：

输入 - 俄罗斯的首都有多少人口？

输出 - 14150000



整体流程：

```text
1、输入问句
2、通过实体识别模型检测问句中的实体，得到mention
3、通过属性抽取模型抽取问句中的属性
4、将实体链接到知识库中，并利用实体及属性信息确定唯一的三元组
```



模型概要：

实体识别模型、属性抽取模型



优缺点及改进方案：

todo



开源案例：

<https://biendata.com/competition/ccks_2019_6/>

<https://github.com/huangxiangzhou/NLPCC2016KBQA>



#### 隐式情感分析

隐式情感的识别与情感倾向性分类







案例：

<https://biendata.com/competition/smpecisa2019/>





#### 细粒度情感分析

任务描述：根据当前的评论文本，预测用户的情感状态



准备数据：文本的粗粒度类别标签及各类别下的细粒度情感标签。示例：对餐厅的评论包括位置、环境、服务、菜品、价格等方面，每个方面根据情感倾向分为正面、负面、中性等。



输入输出示例：

输入 - 这家餐厅的味道不错，就是地方太偏了

输出 - {菜品:正面, 位置:负面}

 

模型概要：

端到端的文本分类模型



开源案例：

 <https://github.com/AIChallenger/AI_Challenger_2018/tree/master/Baselines/sentiment_analysis2018_baseline>

 



#### 基于知识图谱的新闻推荐 *

任务描述：基于用户的浏览历史，预测该用户点击当前新闻的概率。



准备数据：用户的新闻点击历史记录、知识图谱（三元组-一对实体及其关系）

 

输入输出示例： 

|       | news title                                                   | entities                     | label |
| ----- | ------------------------------------------------------------ | ---------------------------- | ----- |
| train | 12/25/2016 Elon Musk teases huge upgrades for Tesla’s supercharger network | Elon Musk; Tesla Inc.        | 1     |
|       | 03/25/2017 Elon Musk offers Tesla Model 3 sneak peek         | Elon Musk; Tesla Model 3     | 0     |
|       | 12/14/2016 Google fumbles while Tesla sprints toward a driverless future | Google Inc.; Tesla Inc.      | 1     |
|       | 12/15/2016 Trump pledges aid to Silicon Valley during tech meeting | Donald Trump; Silicon Valley | 0     |
|       | 03/26/2017 Donald Trump is a big reason why the GOP kept the Montana House seat | Donald Trump; GOP; Montana   | 1     |
|       |                                                              |                              |       |
| test  | 07/08/2017 Tesla makes its first Model 3                     | Tesla Inc; Tesla Model 3     | ?     |



整体流程：

 ```
1. 实体识别模型抽取新闻标题中的实体
2. 实体链接模型将该实体链接到知识图谱中对应的实体
3. 构建子图并学习实体的embedding
4. 将实体的embedding融入DKN模型进行学习
 ```



优缺点及改进方案：

缺点 - DKN模型属于pipeline方式，即先学习知识图谱中实体的embedding，再将embedding引入推荐模型。实体embedding没有在任务中直接学习，因此容易引入误差。此外，没有利用实体之间的关系信息，只用了一跳实体作为实体语境的表示。

改进方案 - 1.尝试联合学习方式，实体的embedding结合任务直接学习。2.利用实体之间的关系信息，筛选有效的实体作为当前实体的语境表示或主题表示。 



开源实现：

 <https://github.com/hwwang55/DKN>

 

#### 事件主体抽取

任务描述：给定文本及事件类型，确定该事件发生的主体



准备数据：事件类型及事件主体标注数据集



输入输出示例： 

输入 - “公司A高管涉嫌违规减持”，“高管减持”

输出 -  “公司A”



整体流程：

```
1.事件类型模型判断当前文本的事件类型
2.事件抽取模型抽取当前文本的事件主体
```



开源案例：

<https://github.com/bojone/ee-2019-baseline>



#### 新闻摘要

任务描述：给定一篇文章，输出该文章的摘要



准备数据：文章摘要标注数据集



输入输出示例： 

输入 - lagos, nigeria (cnn) a day after winning nigeria’s
presidency, muhammadu buhari told cnn’s christiane amanpour that
he plans to aggressively fight corruption that has long plagued nigeria
and go after the root of the nation’s unrest. buhari said he’ll “rapidly give
attention” to curbing violence in the northeast part of nigeria, where the terrorist
group boko haram operates. by cooperating with neighboring nations
chad, cameroon and niger, he said his administration is confident it will
be able to thwart criminals and others contributing to nigeria’s instability.
for the first time in nigeria’s history, the opposition defeated the ruling party
in democratic elections. buhari defeated incumbent goodluck jonathan by
about 2 million votes, according to nigeria’s independent national electoral
commission. the win comes after a long history of military rule, coups
and botched attempts at democracy in africa’s most populous nation.

输出 -  muhammadu buhari says he plans to aggressively
fight corruption that has long plagued nigeria. he says his administration is
confident it will be able to thwart criminals. the win comes after a long history
of military rule, coups and botched attempts at democracy in africa’s
most populous nation.



模型概要：

生成式的端到端模型



开源案例：

<https://github.com/abisee/pointer-generator>

 

#### 大规模文档级关系抽取

任务描述：给定一篇文章，抽取该文章中所有的实体关系



准备数据：知识图谱、含实体关系标注的文章集合



输入输出示例： 

输入 - Me Musical Nephews is a 1942 one-reel animated cartoon directed by Seymour
Kneitel and animated by Tom Johnson and George Germanetti. [2] Jack Mercer and
Jack Ward wrote the script. ...

输出 - {head: Me Musical Nephews, tail: 1942, relation: publication date}, {head: Seymour Kneitel, tail: Me Musical Nephews, relation: director}...



整体流程：

```
1、输入文本
2、通过实体识别模型检测文本中的实体，得到mention
3、通过关系抽取模型判断各实体之间的关系
```



开源案例：

<https://github.com/thunlp/DocRED>

 

#### 文本风格转换

任务描述：给定正向（负向）情感的句子，输出负向（正向）情感的句子



准备数据：正向、负向情感的句子数据集



输入输出示例： 

输入 - do not like it at all !

输出 -  all in all, it's great !



模型概要：

端到端的自编码模型



开源案例：

<https://github.com/shentianxiao/language-style-transfer>



#### 机器阅读理解 *



#### 机器翻译 * 

 



