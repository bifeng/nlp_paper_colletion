more:

http://www.scholarpedia.org/article/Metalearning



### conference

+ ICML

  Meta-Learning: from Few-Shot Learning to Rapid  Reinforcement Learning

  <https://sites.google.com/view/icml19metalearning>

  AutoML 2017 @ ICML

+ ICLR

+ http://metalearning.ml/2018/

+ meta-learning symposium @ NIPS 2018

+ Limited Labeled Data

  https://lld-workshop.github.io/



### Scholars

+ [Chelsea Finn](http://people.eecs.berkeley.edu/~cbfinn/)

  MAML

+ Hugo Larochelle


### Literature review

+ https://msiam.github.io/Few-Shot-Learning/

+ Learning to Learn with Gradients, Chelsea Finn, [PhD Thesis](http://people.eecs.berkeley.edu/~cbfinn/_files/dissertation.pdf) 

  MAML

+ Generalizing from a Few Examples: A Survey on Few-Shot Learning, Yaqing Wang, Quanming Yao, James Kwok, Lionel M. Ni, 2019, [arxiv](https://arxiv.org/abs/1904.05046) 

+ Few-shot Learning - State of the Art, Dr. Joseph Shtok Research Staff Member at Computer Vision and Augmented Reality Team IBM Research AI, Haifa Lab, IMVC 2019

  http://www.research.ibm.com/haifa/dept/imt/ist_dm.shtml

  http://www.research.ibm.com/haifa/dept/imt/IMVC19/IMVC2019%20-%20Few-shot%20learning.pptx

+ Few-Shot Object X, or How Can We Train A DL Model with Only Few Examples, Dr. Leonid Karlinsky, DL Team Lead, CVAR Group IBM Research AI, IMVC 2019

  http://www.research.ibm.com/haifa/dept/imt/ist_dm.shtml

  http://www.research.ibm.com/haifa/dept/imt/IMVC19/IMVC2019_one%20shot%20object%20x.pptx

+ Few-shot Learning with Meta-Learning: Progress Made and Challenges Ahead, Larochelle, Hugo 2018 [video](https://smartech.gatech.edu/handle/1853/60506) 

+ **Generalizing from Few Examples with Meta-Learning** [[Slides](https://sites.google.com/site/automl2017icml/accepted-papers/slides_hugo.pdf?attredirects=0)] *Hugo Larochelle, Google* 2017 

+ THOUGHTS ON PROGRESS MADE AND CHALLENGES AHEAD IN FEW-SHOT LEARNING, 2018 [slide](http://metalearning.ml/2018/slides/meta_learning_2018_Larochelle.pdf) 

### paperlist

+ https://github.com/floodsung/Meta-Learning-Papers
+ 

### paper

+ Memory

+ Memory Augmented Model

  Santoro A, Bartunov S, Botvinick M, et al. One-shot learning with memory-augmented neural networks[J]. arXiv preprint arXiv:1605.06065, 2016.

+ Meta Network

  Munkhdalai, Tsendsuren, and Hong Yu. "Meta networks." Proceedings of the 34th International Conference on Machine Learning-Volume 70. JMLR. org, 2017.



+ Metric

+ Siamese Network

  Koch, Gregory, Richard Zemel, and Ruslan Salakhutdinov. "Siamese neural networks for one-shot image recognition." ICML Deep Learning Workshop. Vol. 2. 2015.

+ Match Network

  Oriol Vinyals, Charles Blundell, Tim Lillicrap, Daan Wierstra, et al. Matching networks for one shot learning. In Advances in Neural Information Processing Systems, pages 3630–3638, 2016, Google DeepMind. [tensorflow](https://github.com/AntreasAntoniou/MatchingNetworks) | [note](https://github.com/karpathy/paper-notes/blob/master/matching_networks.md) 

  contribution:

  the idea of episodic training - It utilizes sampled mini-batches called episodes during training, where each episode is designed to mimic the few-shot task by subsampling classes as well as data points. The use of episodes makes the training problem more faithful to the test environment and thereby improves generalization. It is worth noting that there are exponentially many possible meta tasks to train the model on, making it hard to overfit.

  matching networks - which uses an attention mechanism over a learned embedding of the labeled set of examples (the support set) to predict classes for the unlabeled points (the query set). Matching networks can be interpreted as a weighted nearest-neighbor classifier applied within an embedding space.

+ Prototypical Network

  Snell, Jake, Kevin Swersky, and Richard Zemel. Prototypical networks for few-shot learning. NIPS. 2017. [arxiv](https://arxiv.org/abs/1703.05175) :star::star::star:

+ Relation Network

  Sung, Flood, et al. "Learning to compare: Relation network for few-shot learning." Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition. 2018. :star::star: 

+ Induction Network

  Geng R, Li B, Li Y, et al. Few-Shot Text Classification with Induction Network[J]. arXiv preprint arXiv:1902.10482, 2019. It's important? [arxiv](https://arxiv.org/pdf/1902.10482v1.pdf) [code](<https://github.com/wuzhiye7/Induction-Network-on-FewRel>) 

+ Multiple Metrics

  Yu, Mo, et al. "Diverse few-shot text classification with multiple metrics." arXiv preprint arXiv:1805.07513 (2018).



- Optimization

- Optimization as a model for few-shot learning. Ravi, Sachin, and **Hugo Larochelle** (Research Scientist at Google Brain). Twitter,  ICLR 2017 oral. :star::star::star: 

  > 同时学习优化规则和初始化权重，以往的工作往往是只能学习二者之一


+ MAML: Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks, **Chelsea Finn**, Pieter Abbeel, Sergey Levine, ICML 2017 [arxiv](https://arxiv.org/abs/1703.03400) | [Pytorch](https://github.com/AntreasAntoniou/HowToTrainYourMAMLPytorch) [Tensorflow](<https://github.com/gitlimlab/MAML-tf>) :star::star::star: 

  Chelsea Finn and Sergey Levine. [Meta-learning and universality: Deep representations and gradient descent can approximate any learning algorithm.](https://arxiv.org/abs/1710.11622) arXiv preprint arXiv:1710.11622, 2017.



+ Semi-supervised

+ Meta-Learning for Semi-Supervised Few-Shot Classification, Mengye Ren, Eleni Triantafillou, Sachin Ravi, Jake Snell, Kevin Swersky, Joshua B. Tenenbaum, Hugo Larochelle, Richard S. Zemel, ICLR 2018 [arxiv](https://arxiv.org/abs/1803.00676) | [code](https://github.com/renmengye/few-shot-ssl-public) 

  two situations: one where all unlabeled examples are assumed to belong to the same set of classes as the labeled examples of the episode, as well as the more challenging situation where examples from other distractor classes are also provided. 



+ Imbalance

+ Few-Shot Learning with Localization in Realistic Settings, Davis Wertheimer, Bharath Hariharan, CVPR 2019, [arxiv](https://arxiv.org/abs/1904.08502) 

  Real-world problems may have highly imbalanced, heavy-tailed class distributions, with orders of magnitude more data in some classes than in others.



+ Comparison Analysis

+ A Closer Look at Few-shot Classification, Chen, Wei-Yu and Liu, Yen-Cheng and Kira, Zsolt and Wang, Yu-Chiang and  Huang, Jia-Bin, ICLR 2019 [paper](https://openreview.net/pdf?id=HkxLXnAcFQ) | [code](https://github.com/wyharveychen/CloserLookFewShot) 



### FSL in NLP

+ Hybrid Attention-Based Prototypical Networks for Noisy Few-Shot Relation Classification,  Tianyu Gao*, Xu Han*, Zhiyuan Liu, Maosong Sun, AAAI2019 [paper](https://gaotianyu1350.github.io/assets/aaai2019_hatt_paper.pdf) | [code](https://github.com/thunlp/HATT-Proto) 

  corrupt the support set: each instance in the support set has a probability of rate to be corrupted with a sentence whose relation is not the same as the original one.

+ Han, Xu, et al. "FewRel: A Large-Scale Supervised Few-Shot Relation Classification Dataset with State-of-the-Art Evaluation."  (EMNLP 2018) [arxiv](https://arxiv.org/abs/1810.10147). 

+ Diverse Few-Shot Text Classification with Multiple Metrics, Mo Yu, Xiaoxiao Guo, Jinfeng Yi, Shiyu Chang, Saloni Potdar, Yu Cheng, Gerald Tesauro, Haoyu Wang, Bowen Zhou, NAACL 2018

+ Geng R, Li B, Li Y, et al. Few-Shot Text Classification with Induction Network[J]. arXiv preprint arXiv:1902.10482, 2019. It's important? [arxiv](https://arxiv.org/pdf/1902.10482v1.pdf) [code](<https://github.com/wuzhiye7/Induction-Network-on-FewRel>) 

+ Meta-Learning for Low-Resource Neural Machine Translation, Jiatao Gu, Yong Wang, Yun Chen, Kyunghyun Cho, Victor O.K. Li, EMNLP 2018

+ Meta-Learning a Dynamical Language Model, Thomas Wolf, Julien Chaumond, Clement Delangue, ICLR 2018

+ One-shot and few-shot learning of word embeddings, Andrew K. Lampinen, James L. McClelland, ICLR 2018

### state of art

https://thunlp.github.io/fewrel.html



Few-Shot Relation Classification: https://www.paperswithcode.com/task/few-shot-relation-classification

Few-Shot Image Classification: https://www.paperswithcode.com/task/few-shot-image-classification



### Tools

https://github.com/thunlp/FewRel

https://github.com/ProKil/FewRel

https://github.com/oscarknagg/few-shot/ [blog1](https://towardsdatascience.com/advances-in-few-shot-learning-reproducing-results-in-pytorch-aba70dee541d) [blog2](https://towardsdatascience.com/advances-in-few-shot-learning-a-guided-tour-36bc10a68b77)





### dataset

+ Han, Xu, et al. "FewRel: A Large-Scale Supervised Few-Shot Relation Classification Dataset with State-of-the-Art Evaluation."  (EMNLP 2018) [arxiv](https://arxiv.org/abs/1810.10147). Citations (2)

  **FewRel 数据集**是一个小样本关系分类数据集，包含64种关系用于训练，16种关系用于验证和20种关系用于测试，每种关系下包含700个样本。

+ Yu, Mo, et al. "Diverse few-shot text classification with multiple metrics." (NAACL 2018) [arxiv](https://arxiv.org/abs/1805.07513). Citations (10)

  **ARSC 数据集**取自亚马逊多领域情感分类数据，该数据集包含 23 种亚马逊商品的评论数据，对于每一种商品，构建三个二分类任务，将其评论按分数分为 5、4、 2 三档，每一档视为一个二分类任务，则产生 23*3=69 个 task，然后取其中 12 个 task（4\*3）作为测试集，其余 57 个 task 作为训练集。

+ Geng R, Li B, Li Y, et al. Few-Shot Text Classification with Induction Network[J]. arXiv preprint arXiv:1902.10482, 2019.

  **ODIC 数据集**来自阿里巴巴对话工厂平台的线上日志，用户会向平台提交多种不同的对话任务，和多种不同的意图，但是每种意图只有极少数的标注数据，这形成了一个典型的 Few-shot Learning 任务，该数据集包含 216 个意图，其中 159 个用于训练，57 个用于测试。It's public?













