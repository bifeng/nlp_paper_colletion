refer: [文本主题模型之潜在语义索引(LSI)](https://www.cnblogs.com/pinard/p/6805861.html)



Matrix factorization



Latent Semantic Indexing（LSI）

Latent Semantic Analysis（LSA）

### Contribution

$A_{m \times n} \approx U_{m \times k} \Sigma_{k \times l} V^T_{l \times n}$

奇异值分解（SVD）与隐含主题结合

### Assumption

假设各个topic是互相垂直的向量，结果是得到的类比较难有明确的意义（:question:）



### Disadvantage

1. SVD计算耗时

   solution - 非负矩阵分解（NMF）

2. k值的选择

   solution - 层次狄利克雷过程（HDP）

3. 结果不具有概率含义（难以解释）

   solution - pLSI(pLSA)、隐含狄利克雷分布(LDA)、层次狄利克雷过程（HDP）



### Application

文本主题矩阵 - 计算文本相似度



