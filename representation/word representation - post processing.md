讨厌、注销和喜欢、注册出现的语境相似，所以词向量比较接近，然而这并不是我们想要的结果，如何使反义等词语的词向量之间更有区分度？

Adversarial Training Methods for Semi-Supervised Text Classification, Takeru Miyato, Andrew M. Dai, Ian Goodfellow, ICLR 2017 [arxiv](https://arxiv.org/abs/1605.07725) | [code](https://github.com/aonotas/adversarial_text) | [tensorflow](https://github.com/enry12/adversarial_training_methods) | [pytorch](https://github.com/WangJiuniu/adversarial_training) 

Retrofitting Word Vectors to Semantic Lexicons, Manaal Faruqui, Jesse Dodge, Sujay K. Jauhar, Chris Dyer, Eduard Hovy, Noah A. Smith, NAACL 2015 [arxiv](https://arxiv.org/abs/1411.4166) | [code](https://github.com/mfaruqui/retrofitting) 



#### post processing



+ TF-IDF weighting [code](https://github.com/crownpku/text2vec/blob/master/wv_wrt_tfidf.md)

  

+ A Simple but Tough-to-Beat Baseline for Sentence Embeddings, Sanjeev Arora, Yingyu Liang, Tengyu Ma, ICLR 2017 [paper](https://openreview.net/forum?id=SyK00v5xx) | [code](https://github.com/PrincetonML/SIF) | [code](https://github.com/woctezuma/steam-descriptions/blob/d590742f6ffb73c116a77e38c6fd8594a3921897/SIF_embedding.py) 

  Smooth Inverse Frequency weighting (remove common component of embedding by PCA/SVD)

+ All-but-the-Top: Simple and Effective Postprocessing for Word Representations, Jiaqi Mu, Suma Bhat, Pramod Viswanath, ICLR 2018 [arxiv](https://arxiv.org/abs/1702.01417) 

  eliminate the common mean vector and a few top dominating directions from the word vectors

  (the variances explained by the leading principal components (PCs) “encode the frequency of the word to a significant degree”. Since word frequencies are arguably unrelated to lexical semantics, they recommend removing such leading PCs from word vectors using a PCA reconstruction)

+ Concatenated Power Mean Word Embeddings as Universal Cross-Lingual Sentence Representations, Andreas Rücklé, Steffen Eger, Maxime Peyrard, Iryna Gurevych, 2018 [arxiv](https://arxiv.org/abs/1803.01400) | [code](https://github.com/UKPLab/arxiv2018-xling-sentence-embeddings) 

  Power mean weighting

  

+ Unsupervised Post-processing of Word Vectors via Conceptor Negation, Tianlin Liu, Lyle Ungar, João Sedoc, AAAI-2019 [arxiv](https://arxiv.org/abs/1811.11001) 

  uses conceptors (a linear transformation) to dampen directions where a word vector has high variances

  (Instead of discarding a fixed number of PCs, we softly filter word vectors using matrix conceptors (Jaeger
  2014; 2017), which characterize the linear space of those word vector features having high variances)



#### summary

+ supervised methods to enforce linguistic constraints (e.g., synonym relations) on word vectors ), where the linguistic constraints are extracted from an external linguistic knowledge base such as WordNet (Miller 1995) and PPDB (Pavlick et al. 2015)...
+ unsupervised methods, such as Spectral-decomposition methods such as singular value decomposition (SVD) and principal component analysis (PCA)...





