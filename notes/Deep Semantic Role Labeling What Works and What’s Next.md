语义角色标注，属于自然语言处理中的序列标注任务，其目标是识别句子的谓词-论元结构，判断：何时，何地，谁对谁做了什么。在本方案中，我们采用端到端模型，即带解码约束的highway BiLSTM模型。

模型架构：

![Highway_BiLSTM](https://github.com/bifeng/nlp_paper_notes/raw/master/image/Highway_BiLSTM.jpg)

我们的任务是给定句子-谓词对$(w,y)$作为输入，从所有可能的标注序列空间$\cal{Y}$中寻找得分最高的标注序列$y$。
$$
\hat{y} = \arg \max_{y \in \cal{Y}} f(w,y)
$$
其中，$y$采用BIO标注，词语在论元范围之外，标注为$O$，词语在论元范围的开头和中间则根据该论元角色$r$相应地标注为$B_r$和$I_r$.

我们采用深度BiLSTM将评分函数分解为局部评分函数之和，并加入了外部信息约束，作为评分函数的惩罚项：
$$
f(w,y) = \sum_{t=1}^{n} \log p(y_t|w) - \sum_{c\in\cal{C}} c(w,y_{1:t})
$$
其中，约束函数$c$为对输入$w$和前$t$个$y$的非负惩罚，该约束可以是结构连续、语法规则等外部信息，在本方案中，选择BIO约束。

该模型由以下部分组成：

1. deep BiLSTM

   深度BiLSTM，即堆叠多层的BiLSTM，获得句子的深度语义表示。

2. highway connections

   highway连接可以减轻深度BiLSTM的梯度消失问题。上图中的曲线连接即为highway连接，“+”表示转换门，用于控制网络层间的信息流动。

3. recurrent dropout

   recurrent失活可以降低过拟合。

4. decoding with BIO-constraints

   在解码阶段，加入了BIO约束（hard constraints）,使用$A^*$解码算法，该算法可以使预测时的结果具有结构连续性，而不会增加训练过程的复杂度。

   其中，BIO约束可以拒绝BIO转移不合理的序列，如$I_{ARG1}$后面是$B_{ARG0}$。



#### training strategy

初始化- orthogonal initialization

All the weight matrices in BiLSTMs are initialized with random orthonormal matrices

正则化 - recurrent dropout



#### constraints

BIO Constraints

SRL Constraints

Syntactic Constraints

