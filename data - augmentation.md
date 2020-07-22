## Paperlists

+ <https://github.com/quincyliang/nlp-data-augmentation>



## Paper

- EDA: Easy Data Augmentation Techniques for Boosting Performance on Text Classification Tasks, Jason W. Wei, Kai Zou, ICLR 2019, [arxiv](https://arxiv.org/abs/1901.11196) | [code](https://github.com/jasonwei20/eda_nlp) 

  <details>
      EDA is the following operations: <br>
  1. Synonym Replacement (SR): Randomly choose n words from the sentence that are not
     stop words. Replace each of these words with one of its synonyms chosen at random.<br>
  2. Random Insertion (RI): Find a random synonym of a random word in the sentence that is
     not a stop word. Insert that synonym into a random position in the sentence. Do this n times.<br>
  3. Random Swap (RS): Randomly choose two words in the sentence and swap their positions.
     Do this n times.<br>
  4. Random Deletion (RD): Randomly remove each word in the sentence with probability p.

- Conditional BERT Contextual Augmentation, Xing Wu, Shangwen Lv, Liangjun Zang, Jizhong Han, Songlin Hu, 201812, [arxiv](https://arxiv.org/abs/1812.06705) 

- Contextual Augmentation: Data Augmentation by Words with Paradigmatic Relations. Sosuke Kobayashi, NAACL-HLT, 2018. [arxiv](https://arxiv.org/pdf/1805.06201.pdf) | [code](https://github.com/pfnet-research/contextual_augmentation) 

  Contextual augmentation is a domain-independent data augmentation for text classification tasks. Texts in supervised dataset are augmented by replacing words with other words which are predicted by a label-conditioned bi-directional language model.

- Data Noising as Smoothing in Neural Network Language Models, Ziang Xie, Sida I. Wang, Jiwei Li, Daniel Lévy, Aiming Nie, Dan Jurafsky, Andrew Y. Ng, ICLR 2017 [arxiv](https://arxiv.org/abs/1703.02573) 

- Learning to Compose Domain-Specific Transformations for Data Augmentation
  Alexander J. Ratner, Henry R. Ehrenberg, Zeshan Hussain, Jared Dunnmon, Christopher Ré NIPS 2017 [arxiv](<https://arxiv.org/abs/1709.01643>) [code](<https://github.com/HazyResearch/tanda>) 

## Blogs

+ <https://amitness.com/2020/05/data-augmentation-for-nlp/>



+ <https://github.com/makcedward/nlp#data-augmentation>

|                                                         |                                                              |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| Data Augmentation in NLP                                | [Medium](https://towardsdatascience.com/data-augmentation-in-nlp-2801a34dfc28) |
| Data Augmentation library for Text                      | [Medium](https://towardsdatascience.com/data-augmentation-library-for-text-9661736b13ff) |
| Does your NLP model able to prevent adversarial attack? | [Medium](https://hackernoon.com/does-your-nlp-model-able-to-prevent-adversarial-attack-45b5ab75129c) |
| Data Augmentation library for Speech Recognition        | [Medium](https://towardsdatascience.com/data-augmentation-for-speech-recognition-e7c607482e78) |
| Data Augmentation library for Audio                     | [Medium](https://towardsdatascience.com/data-augmentation-for-audio-76912b01fdf6) |
| 聊一聊，预处理和数据增强技术                            | [site](https://zhpmatrix.github.io/2019/03/08/preprocess-augmentation-in-nlp/) |
|                                                         |                                                              |
|                                                         |                                                              |
|                                                         |                                                              |

+ 基于Markov Chain的极简数据增强方法 [原文](https://mp.weixin.qq.com/s?__biz=MzA5MjEyNDMxOQ==&mid=2247483684&idx=1&sn=e0a904d6eeefd8ba42980ccfc6bc7a22&chksm=9070a4d4a7072dc2e4316202663615909f58a910b0a355af3282df723f8a2884c505f3302130&token=1216643233&lang=zh_CN#rd) [代码](https://github.com/leerumor/nlpcab/blob/master/code/markov_data_augmentation.py) 



## Tools

+ https://github.com/makcedward/nlpaug
+ <https://github.com/QData/TextAttack>

