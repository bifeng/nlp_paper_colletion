依存句法分析主要有两种主流方法：基于图（graph-based）的分析方法和基于转移（transition-based）的分析方法。	本方案采用BiLSTMs作为特征抽取器，并结合图解析器联合训练。

模型架构：

![BiLSTMs_Graph_based](https://github.com/bifeng/nlp_paper_notes/raw/master/image/BiLSTMs_Graph_based.png)

其中，解析树位于句子的下面，句子每一个依存弧通过BiLSTMs编码、MLP进行评分，并将每个依存弧的评分求和得到最终评分。在解析一个句子时，我们会计算所有可能的弧，并使用动态规划算法寻找最优得分的依存树。

该模型由以下部分组成：

1. BiLSTMs

   BiLSTMs作为特征抽取器，可以避免了大量手工特征。在本方案中，采用两层BiLSTMs。

2. Graph-based Parser

   基于图的解析器，将解析过程看作基于搜索的结构预测问题，目标是学习整个依存树的评分函数。本方案采用一阶arc-factored模型作为图解析器，该模型将整个依存树的评分函数分解为对树的各个依存弧的评分。

3. Joint training

   联合训练，即BiLSTMs与Parser的目标联合训练，将目标函数的误差传递回BiLSTMs特征抽取器，使BiLSTMs获得适于解析任务的更好的特征表达。



#### parser

a greedy transition-based parser
a globally optimized graph-based parser