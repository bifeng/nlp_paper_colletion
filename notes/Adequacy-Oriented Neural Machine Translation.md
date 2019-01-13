#### Syntax-Aware

Source Syntax<br>
Target Syntax

#### Larger-Granularity

soft phrase<br>
hard phrase

#### Document-level

Challenge:

Consistency problem (时态等一致性)

Ambiguity problem

The cross-sentence context has proven helpful for the aforementioned two problems in SMT. However, it has received relatively little attention in NMT.

Exploiting Cross-Sentence Context for Neural Machine Translation, EMNLP 2017 [paper](http://aclweb.org/anthology/D17-1301) | [slides](https://www.computing.dcu.ie/~lwang/slides/EMNLP2017.pdf)

#### Adequacy Learning

##### over/under-translation

![encoder decoder](https://github.com/bifeng/nlp_paper_notes/raw/master/image/encoder-decoder-NMT.png)

![encoder decoder attention](https://github.com/bifeng/nlp_paper_notes/raw/master/image/encoder-decoder-attention-NMT.png)



Future Modeling - Modeling Past and Future for Neural Machine Translation, TACL 2017, [arxiv](https://arxiv.org/abs/1711.09502)



##### pro-dropped

Challenge:

SMT can't solve it. NMT can alleviate the problem for simple dropped pronouns (DPs), but not complicated DPs.



Reconstruction - 

+ Learning to Jointly Translate and Predict Dropped Pronouns with a Shared Reconstruction Mechanism, EMNLP 2018, [pdf](http://emnlp2018.org/program/accepted/short-papers)

+ Translating Pro-Drop Languages with Reconstruction Models, AAAI 2018, [arxiv](https://arxiv.org/abs/1801.03257)



#### QA

**Q：如何提升解码速度？**

**A：**可以看看 Jacob Devlin 的一些工作，他现在在微软。他的一些开源报告中提出了很多加速方式。比如我们一般使用全部的 softmax，可以换成使用 sampled softmax 等等。

**Q：Transformer 的实际实验效果差距大吗？**

**A：**差距确实很大。Transformer 可能是未来的一个 benchmark，但是现在它还存在一些问题，虽然有自己的优点，但也有很大的提升空间。































