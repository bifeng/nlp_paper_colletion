refer:<br>[效果惊人的GPT 2.0模型：它告诉了我们什么](https://zhuanlan.zhihu.com/p/56865533)



### Innovation

+ large, broad domain and high quality datasets
+ unsupervised



### Summary

- GPT 2.0验证了Bert两阶段模型第一个阶段-预训练过程（**语言模型**）是非常有效的无监督NLP语言知识编码方法。说明预训练过程，如果采用更高质量的数据，采用更宽泛的数据（Web数据量大了估计包含任何你能想到的领域），采用更大量的数据（WebText，800万网页），Transformer采用更复杂的模型（最大的GPT2.0模型是Transformer的两倍层深），那么在Transformer里能学会更多更好的NLP的通用知识。

  为什么是通用的？因为第二阶段不做任何fine-tuning就能达到更好的效果，而且是各种任务，说明通用性好。



### Question

+ 语言模型是否学习到通用知识（common sense）？只是记忆，不能推理？

+ 如何让语言模型在语言生成方面起作用？

+ 为什么可以用在机器翻译的任务？（阅读paper）

+ 为什么可以用在文本摘要、问答的任务？（阅读paper）

+ 为什么阅读理解任务的引导符为'A:'，文本摘要的引导符为'TL;DR:'就可以区分不同任务？

  两个符号分别引导两个任务的生成。本文的语料都是一些 well-written 的网页，里面有一些带 TL;DR: 的科技博客或者访谈内容最后跟 QA 环节的文章：

  摘要（带 TL;DR 这个符号） [https://towardsdatascience.com/beyond-word-embeddings-part-2-word-vectors-nlp-modeling-from-bow-to-bert-4ebd4711d0ec](http://link.zhihu.com/?target=https%3A//towardsdatascience.com/beyond-word-embeddings-part-2-word-vectors-nlp-modeling-from-bow-to-bert-4ebd4711d0ec)

  问答（带 Q: 和 A: 这两个符号）：[Exclusive interview: Kai-Fu Lee's Innovation Works (Q&A)](http://link.zhihu.com/?target=http%3A//www.chinadaily.com.cn/business/2010-06/03/content_9931161.htm) 

