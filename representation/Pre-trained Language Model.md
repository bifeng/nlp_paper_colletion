<https://github.com/thunlp/PLMpapers>

<https://github.com/daiwk/daiwk.github.io/blob/master/_posts/2019-03-20-nlp-paddle-lark.md>



## Word embedding

#### FastText

<https://github.com/facebookresearch/fastText>

<https://fasttext.cc/docs/en/autotune.html>







## Transformer-based



#### Transformers

🤗 Transformers: State-of-the-art Natural Language Processing for TensorFlow 2.0 and PyTorch. https://huggingface.co/transformers

https://github.com/huggingface/transformers



#### RoBERTa: A Robustly Optimized BERT Pretraining Approach
Yinhan Liu, Myle Ott, Naman Goyal, Jingfei Du, Mandar Joshi, Danqi Chen, Omer Levy, Mike Lewis, Luke Zettlemoyer, Veselin Stoyanov [arxiv](<https://arxiv.org/abs/1907.11692>) 



#### XLNet

https://arxiv.org/abs/1906.08237

https://github.com/zihangdai/xlnet



### ALBERT

ALBERT: A Lite BERT for Self-supervised Learning of Language Representations. [arxiv](<https://arxiv.org/abs/1909.11942>) 

<https://github.com/google-research/ALBERT>

Notes on ALBERT” by Rémi Louf paper:《ALBERT: A Lite BERT for Self-supervised Learning of Language Representations》 

**two parameter reduction techniques**

+ Factorized embedding parameterization

  The WordPiece embedding size E is tied with the hidden layer size H, i.e., E ≡ H. This decision appears suboptimal for both modeling and practical reasons, as follows.

  From a modeling perspective, WordPiece embeddings are meant to learn context-independent representations, whereas hidden-layer embeddings are meant to learn context-dependent representations.

  From a practical perspective, natural language processing usually require the vocabulary size V to be large. If E ≡ H, then increasing H increases the size of the embedding matrix, which has size V ×E. This can easily result in a model with billions of parameters, most of which are only updated sparsely during training.

  we use a factorization of the embedding parameters, decomposing them
  into two smaller matrices. Instead of projecting the one-hot vectors directly into the hidden space of size H, we first project them into a lower dimensional embedding space of size E, and then project it to the hidden space.

  <u>We choose to use the same E for all word pieces because they are much more evenly distributed across documents compared to whole-word embedding, where having different embedding size (Grave et al. (2017); Baevski & Auli (2018); Dai et al. (2019) ) for different words is important</u>.(???)

+ cross-layer parameter sharing

  There are multiple ways to share parameters, e.g., only sharing feed-forward network (FFN) parameters across layers, or only sharing attention parameters.
  The default decision for ALBERT is to share all parameters across layers.





**a self-supervised loss** - Inter-sentence coherence loss

a self-supervised loss that focuses on modeling inter-sentence coherence, and show it consistently helps downstream tasks with multi-sentence inputs. 



#### ELECTRA

ELECTRA: Pre-training Text Encoders as Discriminators Rather Than Generators. ICLR 2020

<https://zhuanlan.zhihu.com/p/89763176>

不仅提出了NLP式的Generator-Discriminator，而且文章简直就是最近nlp发展的timeline。顺着文章读下去，然后跟进参考文献，基本就可以把最近nlp的发展理得一清二楚。并且，也简单总结了目前各模型存在的缺点。 Manning PPT链接在下面。https://www.jianguoyun.com/p/DVRRLHUQq7ftBxjG3Y8C 

链接:[https://pan.baidu.com/s/172hClbA4fwON9MFzspnRBw](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/172hClbA4fwON9MFzspnRBw) 密码:b6qg

第一个有效学到用当前位置提取的信息预测当前位置的输出的模型，之前的bert/xlnet等都是用别的位置提取的信息预测当前位置的输出.



