refer: [文本主题模型之非负矩阵分解(NMF)](https://www.cnblogs.com/pinard/p/6812011.html)



Matrix factorization

non-negative matrix factorization (NMF)

### Contribution

$A_{m \times n} \approx W_{m \times k} H_{k \times n}$



### Optimization

$\underbrace{arg\;min}_{W,H}\frac{1}{2}||A-WH||_{Fro}^2$

其中，$||*||_{Fro}$为Frobenius范数。

常用的迭代方法有梯度下降法和拟牛顿法。



$\underbrace{arg\;min}_{W,H}\frac{1}{2}||A-WH||_{Fro}^2 +\alpha\rho|| W||_1+\alpha\rho|| H||_1+\frac{\alpha(1-\rho)}{2}|| W||_{Fro}^2 + \frac{\alpha(1-\rho)}{2}|| H||_{Fro}^2$

其中，$α$为L1&L2正则化参数，而$ρ$为L1正则化占总正则化项的比例。$||∗||_1$为L1范数。

常用的迭代方法有坐标轴下降法或者最小角回归法.





### Disadvantage/Advantage

Advantage:

1. 速度快

2. （non-negative）拥有直观的概率解释

   



### Application

图像处理，语音处理，信号处理，医药工程