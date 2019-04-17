



### conference

+ http://metalearning.ml/2018/
+ ICLR 2017 
+ AutoML 2017 @ ICML
+ meta-learning symposium @ NIPS 2018



### Literature review

+ Few-shot Learning: A Survey, Yaqing Wang, Quanming Yao, 2019, [arxiv](https://arxiv.org/abs/1904.05046v1) 

  Computer Vision Application

+ Few-shot Learning - State of the Art, Dr. Joseph ShtokResearch Staff Member at Computer Vision and Augmented Reality Team IBM Research AI, Haifa Lab, IMVC 2019

  http://www.research.ibm.com/haifa/dept/imt/ist_dm.shtml

  http://www.research.ibm.com/haifa/dept/imt/IMVC19/IMVC2019%20-%20Few-shot%20learning.pptx

+ Few-Shot Object X, or How Can We Train A DL Model with Only Few Examples, Dr. Leonid Karlinsky, DL Team Lead, CVAR Group IBM Research AI, IMVC 2019

  http://www.research.ibm.com/haifa/dept/imt/ist_dm.shtml

  http://www.research.ibm.com/haifa/dept/imt/IMVC19/IMVC2019_one%20shot%20object%20x.pptx

+ Few-shot Learning with Meta-Learning: Progress Made and Challenges Ahead, Larochelle, Hugo 2018 [video](https://smartech.gatech.edu/handle/1853/60506) 

+ **Generalizing from Few Examples with Meta-Learning** [[Slides](https://sites.google.com/site/automl2017icml/accepted-papers/slides_hugo.pdf?attredirects=0)] *Hugo Larochelle, Google* 2017 

+ THOUGHTS ON PROGRESS MADE AND CHALLENGES AHEAD IN FEW-SHOT LEARNING, 2018 [slide](http://metalearning.ml/2018/slides/meta_learning_2018_Larochelle.pdf) 

### paper

+ Memory Augmented Model

  Santoro A, Bartunov S, Botvinick M, et al. One-shot learning with memory-augmented neural networks[J]. arXiv preprint arXiv:1605.06065, 2016.

+ Meta Network

  Munkhdalai, Tsendsuren, and Hong Yu. "Meta networks." Proceedings of the 34th International Conference on Machine Learning-Volume 70. JMLR. org, 2017.



+ Siamese Network

  Koch, Gregory, Richard Zemel, and Ruslan Salakhutdinov. "Siamese neural networks for one-shot image recognition." ICML Deep Learning Workshop. Vol. 2. 2015.

+ Match Network

  Oriol Vinyals, Charles Blundell, Tim Lillicrap, Daan Wierstra, et al. Matching networks for one shot learning. In Advances in Neural Information Processing Systems, pages 3630–3638, 2016.

+ Prototypical Network

  Snell, Jake, Kevin Swersky, and Richard Zemel. "Prototypical networks for few-shot learning." Advances in Neural Information Processing Systems. 2017. :star::star::star:

  Gao, Tianyu, et al. "Hybrid Attention-Based Prototypical Networks for Noisy Few-Shot Relation Classification." (2019). It's important?

+ Relation Network

  Sung, Flood, et al. "Learning to compare: Relation network for few-shot learning." Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition. 2018. :star::star: 

+ Induction Network

  Geng R, Li B, Li Y, et al. Few-Shot Text Classification with Induction Network[J]. arXiv preprint arXiv:1902.10482, 2019. It's important?

+ Multiple Metrics

  Yu, Mo, et al. "Diverse few-shot text classification with multiple metrics." arXiv preprint arXiv:1805.07513 (2018).



- Optimization

  Optimization as a model for few-shot learning. Ravi, Sachin, and **Hugo Larochelle** (Research Scientist at Google Brain). Twitter,  ICLR 2017 oral. :star::star::star: 

  > 同时学习优化规则和初始化权重，以往的工作往往是只能学习二者之一

  Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks, Chelsea Finn, Pieter Abbeel, Sergey Levine, ICML 2017 [arxiv](https://arxiv.org/abs/1703.03400)  :star::star::star: 

  > 





### state of art

https://thunlp.github.io/fewrel.html



### dataset

+ Han, Xu, et al. "FewRel: A Large-Scale Supervised Few-Shot Relation Classification Dataset with State-of-the-Art Evaluation." arXiv preprint arXiv:1810.10147 (EMNLP 2018).

  **FewRel 数据集**是一个小样本关系分类数据集，包含64种关系用于训练，16种关系用于验证和20种关系用于测试，每种关系下包含700个样本。

+ Yu, Mo, et al. "Diverse few-shot text classification with multiple metrics." arXiv preprint arXiv:1805.07513 (NAACL 2018).

  **ARSC 数据集**取自亚马逊多领域情感分类数据，该数据集包含 23 种亚马逊商品的评论数据，对于每一种商品，构建三个二分类任务，将其评论按分数分为 5、4、 2 三档，每一档视为一个二分类任务，则产生 23*3=69 个 task，然后取其中 12 个 task（4\*3）作为测试集，其余 57 个 task 作为训练集。

+ Geng R, Li B, Li Y, et al. Few-Shot Text Classification with Induction Network[J]. arXiv preprint arXiv:1902.10482, 2019.

  **ODIC 数据集**来自阿里巴巴对话工厂平台的线上日志，用户会向平台提交多种不同的对话任务，和多种不同的意图，但是每种意图只有极少数的标注数据，这形成了一个典型的 Few-shot Learning 任务，该数据集包含 216 个意图，其中 159 个用于训练，57 个用于测试。It's public?













