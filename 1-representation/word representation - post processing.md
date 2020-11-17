讨厌、注销和喜欢、注册出现的语境相似，所以词向量比较接近，然而这并不是我们想要的结果，如何使反义等词语的词向量之间更有区分度？

Adversarial Training Methods for Semi-Supervised Text Classification, Takeru Miyato, Andrew M. Dai, Ian Goodfellow, ICLR 2017 [arxiv](https://arxiv.org/abs/1605.07725) | [code](https://github.com/aonotas/adversarial_text) | [tensorflow](https://github.com/enry12/adversarial_training_methods) | [pytorch](https://github.com/WangJiuniu/adversarial_training) 

Retrofitting Word Vectors to Semantic Lexicons, Manaal Faruqui, Jesse Dodge, Sujay K. Jauhar, Chris Dyer, Eduard Hovy, Noah A. Smith, NAACL 2015 [arxiv](https://arxiv.org/abs/1411.4166) | [code](https://github.com/mfaruqui/retrofitting) 



#### post processing



+ TF-IDF weighting [code](https://github.com/crownpku/text2vec/blob/master/wv_wrt_tfidf.md)

  

+ Retrofitting Word Vectors to Semantic Lexicons, Manaal Faruqui, Jesse Dodge, Sujay K. Jauhar, Chris Dyer, Eduard Hovy, Noah A. Smith, NAACL 2015 **Best Paper Award**, [arxiv](<https://arxiv.org/abs/1411.4166>) | [code](<https://github.com/mfaruqui/retrofitting>) :star::star::star:

+ A Simple but Tough-to-Beat Baseline for Sentence Embeddings, Sanjeev Arora, Yingyu Liang, Tengyu Ma, ICLR 2017 [paper](https://openreview.net/forum?id=SyK00v5xx) | [code](https://github.com/PrincetonML/SIF) | [code](https://github.com/woctezuma/steam-descriptions/blob/d590742f6ffb73c116a77e38c6fd8594a3921897/SIF_embedding.py) :star::star::star:

+ All-but-the-Top: Simple and Effective Postprocessing for Word Representations, Jiaqi Mu, Suma Bhat, Pramod Viswanath, ICLR 2018 [arxiv](https://arxiv.org/abs/1702.01417) | [code](https://github.com/woctezuma/steam-descriptions/blob/44e6490802a4ad6129dcd3c4283446d8e171a147/sif_embedding_perso.py) | [code](https://github.com/jonadsimon/entendrepreneur-web/blob/50dc9faf26384bbcc8dc84d8eaf0bf84cb2deb55/scripts/precompute_word_vector_nearest_neighbors.py) :star::star:

+ Concatenated Power Mean Word Embeddings as Universal Cross-Lingual Sentence Representations, Andreas Rücklé, Steffen Eger, Maxime Peyrard, Iryna Gurevych, 2018 [arxiv](https://arxiv.org/abs/1803.01400) | [code](https://github.com/UKPLab/arxiv2018-xling-sentence-embeddings) 

  Power mean weighting

+ Unsupervised Post-processing of Word Vectors via Conceptor Negation, Tianlin Liu, Lyle Ungar, João Sedoc, AAAI-2019 [arxiv](https://arxiv.org/abs/1811.11001) 

  uses conceptors (a linear transformation) to dampen directions where a word vector has high variances

  (Instead of discarding a fixed number of PCs, we softly filter word vectors using matrix conceptors (Jaeger
  2014; 2017), which characterize the linear space of those word vector features having high variances)

  

+ On the Dimensionality of Word Embedding, Zi Yin, Yuanyuan Shen, NeurIPS 2018 [arxiv](https://arxiv.org/abs/1812.04224) 

 

#### summary

+ supervised methods to enforce linguistic constraints (e.g., synonym relations) on word vectors ), where the linguistic constraints are extracted from an external linguistic knowledge base such as WordNet (Miller 1995) and PPDB (Pavlick et al. 2015)...
+ unsupervised methods, such as Spectral-decomposition methods such as singular value decomposition (SVD) and principal component analysis (PCA)...





