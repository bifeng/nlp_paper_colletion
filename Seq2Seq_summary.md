

### Application

machine translation

semantic parsing

code generation

summarization generation

keyphrase Generation

paraphrase generation

story generation

text generation

chatbot

commonsense Inference

### Literature review

- Controllable Text Generation: Types, Knowledge, and Logic. 2018, December, JD AI, 黄民烈 [slides](http://coai.cs.tsinghua.edu.cn/hml/media/files/controllable-text-generation.pdf) 
- [干货 | 文本改写和风格迁移的一些思路](https://mp.weixin.qq.com/s/AxmpnP5RJa7y9ju3RaEgdw)
- [干货 | 限定和指导 Seq2Seq 模型的生成结果（一）](https://mp.weixin.qq.com/s/6q9txFjgqs1YXn348ylXhQ)
- [干货 | 限定和指导 Seq2Seq 模型的生成结果（二）](https://mp.weixin.qq.com/s/jvozDRtKb4kaGSJvoP5nkw)
- 



Constrain the output space to selections that matter
Inference: Avoid invalid parses
Training: Do not waste modeling power in distinguishing invalid parses from valid ones!

### Challenges

#### The "UNK" problem

Specific entities, low frequency words cannot be generated

由于decoder部分产生词汇的来源是通过训练语料得到的词汇表，但是在实际测试过程中，测试集中的词不一定完全在训练集中出现，也就超出了decoder的预测范围。这种现象通常称为OOV问题（Out of Vocabulary）。

#### The repetition problem

由于decoder过度依赖其输入，也就是先前的总结词，会导致一个词的出现触发无尽的重复。

### Methods

#### Token-based Decoding



#### Grammar-based Decoding

+ Lexically Constrained Decoding for Sequence Generation Using Grid Beam Search, Chris Hokamp, Qun Liu, ACL 2017 [arxiv](https://arxiv.org/abs/1704.07138) | [code](https://github.com/chrishokamp/constrained_decoding) 
+ 




#### retrieve and edit

+ A Retrieve-and-Edit Framework for Predicting Structured Outputs, Tatsunori B. Hashimoto, Kelvin Guu, Yonatan Oren, Percy Liang, NeurIPS 2018 [arxiv](https://arxiv.org/abs/1812.01194) | [code](https://worksheets.codalab.org/worksheets/0x1ad3f387005c492ea913cf0f20c9bb89/#)  
+ 

