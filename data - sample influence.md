refer:<br>[样本生而不等——聊聊那些对训练数据加权的方法](https://zhuanlan.zhihu.com/p/53545036)

[深度学习中有什么方法可以找出训练集中脏数据(比如标记错误的数据)？](https://www.zhihu.com/question/298719271)

如何找出那些对于降低验证集loss没有帮助的样本，把他们从训练集中排除，从而提升model的性能？

### Data Dropout

首先使用全部数据得到一个初始模型，然后在这样的初始模型上计算每个样本的influence，去掉那些对降低验证集loss的样本后，使用新的训练集再次训练得到最终的模型。

Wang, Tianyang, Jun Huan, and Bo Li. "Data dropout: Optimizing training data for convolutional neural networks." *2018 IEEE 30th International Conference on Tools with Artificial Intelligence (ICTAI)*. IEEE, 2018.





训练完成后计算网络的Hessian矩阵，计算的时候需要对训练数据取均值，这时候可以对数据进行leave-one-out，看哪个数据会导致矩阵的谱的较大偏离，这个数据可能就是噪声。

实际是看哪个数据对网络复杂度的影响大，导致网络复杂度剧变的数据一般是噪声。

Koh, Pang Wei, and Percy Liang. "Understanding black-box predictions via influence functions." *ICML* (2017) Best Paper. [arxiv](https://arxiv.org/abs/1703.04730) | [code](https://github.com/kohpangwei/influence-release) 

### Summary

+ 是否有必要对脏数据进行处理？依情况而定，对于大数据量而言，模型的鲁棒性强，无需处理，而对于小数据量，则需要处理。（随机误差与系统误差）
+ 



