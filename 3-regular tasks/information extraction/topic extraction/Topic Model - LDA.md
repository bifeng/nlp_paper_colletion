more refer: 

[文本主题模型之LDA(一) LDA基础](https://www.cnblogs.com/pinard/p/6831308.html)

[文本主题模型之LDA(二) LDA求解之Gibbs采样算法](https://www.cnblogs.com/pinard/p/6867828.html)

[文本主题模型之LDA(三) LDA求解之变分推断EM算法](https://www.cnblogs.com/pinard/p/6873703.html)  



Latent Dirichlet Allocation（LDA）



### Question

+ 文档主题分布和主题词分布是独立的？

  

+ 为什么需要共轭分布？

  使先验分布与后验分布的形式一致，1）符合直观，2）简化计算。

  

### algorithm

有向无环图：omit

$\alpha \rightarrow \theta_d \rightarrow Z_{d,n} \rightarrow W_{d,n} \leftarrow \beta_k \leftarrow \eta$



<u>文档主题的先验分布是Dirichlet分布</u>，对于任一文档$d$, 其主题分布$θ_d$为：

$\theta_d = Dirichlet(\vec \alpha)$

其中，$α$为分布的超参数，是一个$K$维向量

<u>主题中词的先验分布是Dirichlet分布</u>，对于任一主题$k$, 其词分布$β_k$为：

$\beta_k= Dirichlet(\vec \eta)$

其中，$η$为分布的超参数，是一个$V$维向量。$V$代表词汇表里所有词的个数。



生成过程：

对于数据中任一一篇文档$d$中的第$n$个词，我们可以从主题分布$θ_d$中得到它的主题编号$z_{dn}$的概率分布为：

$z_{dn} = multi(\theta_d)$

对于该主题编号，得到我们看到的词$w_{dn}$的概率分布为：

$w_{dn} = multi(\beta_{z_{dn}})$





### inference



基于Gibbs采样算法

基于变分推断EM算法





### Advantages/Disadvantages

Advantages:

1. 从文档生成过程来看： Topics->topic words->words
2. 从分布的角度来看：一篇文档可能包含多类主题，一个主题可能包含多类词语







