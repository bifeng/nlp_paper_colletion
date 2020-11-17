more: 

Knowledge Graph Embedding: A Survey of Approaches and Applications, Quan Wang, Zhendong Mao, Bin Wang, and Li Guo 2017 [pdf](<https://www.semanticscholar.org/paper/Knowledge-Graph-Embedding%3A-A-Survey-of-Approaches-Wang-Mao/30321b036607a7936221235ea8ec7cf7c1627100>) 

A Survey on Knowledge Graphs: Representation, Acquisition and Applications. Shaoxiong Ji, Shirui Pan, Erik Cambria, Pekka Marttinen, Philip S. Yu 2020.08 [arxiv](<https://arxiv.org/abs/2002.00388>) 

Knowledge Graphs. Aidan Hogan, Eva Blomqvist, Michael Cochez, Claudia d'Amato, Gerard de Melo, Claudio Gutierrez, José Emilio Labra Gayo, Sabrina Kirrane, Sebastian Neumaier, Axel Polleres, Roberto Navigli, Axel-Cyrille Ngonga Ngomo, Sabbir M. Rashid, Anisa Rula, Lukas Schmelzeisen, Juan Sequeda, Steffen Staab, Antoine Zimmermann 2020.04 [arxiv](<https://arxiv.org/abs/2003.02320>)  

https://en.wikipedia.org/wiki/Knowledge_representation_and_reasoning





refer:

知识图谱，赵军主编，高等教育出版社



## Question

1. knowledge graph embedding 与 Heterogeneous Network Representation Learning之间的区别与联系？

2. knowledge graph embedding vs graph embedding

   前者重点关系建模，注重**推理**（说**相似**更加合适！），适用于图谱的补全任务

   后者重点网络建模，注重**表示**，理论基础-graph theory!

   

   共同点：建模前都需要序列化，前者序列化三元组，后者随机游走序列化...

   

   kge也有利用graph embedding，比如可以抽取具有相同关系的节点网络（异构图转化为同构图），这样可以将节点结构的表示约束在一个领域里面，有聚类的效果。(学习不同关系下的实体表示)

   

   两种融合是未来可能的趋势：

   <https://github.com/PaddlePaddle/PGL/tree/master/examples/erniesage>

   使用ID特征的GraphSAGE只能够建模图的结构信息，而单独的ERNIE只能处理文本信息。通过PGL搭建的图与文本的桥梁，**ERNIESage**能够很简单的把GraphSAGE以及ERNIE的优点结合一起。以下面TextGraph的场景，**ERNIESage**的效果能够比单独的ERNIE以及GraphSAGE模型都要好。

+ 属性是当做三元组（知识图谱）去学习，还是当做实体的属性（异质信息网络）去学习？有待验证。

  如果把属性和关系应该看作不同的对象，应该采用不同的方法去建模/表示实体、关系、属性。

  



## KG properties

1. 关系的定义（性质）

   类似离散数学中集合的关系概念 - (集合论或集论是研究集合（由一堆抽象物件构成的整体）的数学理论，包含了集合、元素和成员关系等最基本的数学概念)

   （A relation in mathematics defines the relationship between two different sets of information. If two sets are considered, the relation between them will be established if there is a connection between the elements of two or more non-empty sets.）

   

   不同性质，组合成特定关系的定义：

   A binary relation ~ on a set X is said to be an [**equivalence relation**](https://en.wikipedia.org/wiki/Equivalence_relation), if and only if it is reflexive, symmetric and transitive.(等价关系的三个属性——自反性、对称性、传递性)

   

   现实生活中存在具有对称性、反身性但不具有传递性的关系？

   https://math.stackexchange.com/questions/268726/are-there-real-life-relations-which-are-symmetric-and-reflexive-but-not-transiti/268727

   

   **Ontology features for property axioms**

   ![kg_ontology_features](https://github.com/bifeng/daily_book_notes/raw/master/resource/kg_ontology_features.png)

   ... We may define a pair of properties to be equivalent, inverses, or disjoint. We can further define a particular property to denote a transitive, symmetric, asymmetric, reflexive, or irreflexive relation. We can also define the multiplicity of the relation denoted by properties, based on being functional (many-to-one) or inverse-functional (one-to-many). ...

   (refer: Knowledge Graphs. Aidan Hogan, Eva Blomqvist, Michael Cochez, Claudia d'Amato, Gerard de Melo, Claudio Gutierrez, José Emilio Labra Gayo, Sabrina Kirrane, Sebastian Neumaier, Axel Polleres, Roberto Navigli, Axel-Cyrille Ngonga Ngomo, Sabbir M. Rashid, Anisa Rula, Lukas Schmelzeisen, Juan Sequeda, Steffen Staab, Antoine Zimmermann [arxiv](<https://arxiv.org/abs/2003.02320>))

   

   **定义**

   Definition 1

   A relation $r$ is symmetric (antisymmetric) if ∀x, y

   ​	r(x, y) ⇒ r(y, x) ( r(x, y) ⇒ ¬r(y, x) )

   A clause with such form is a symmetry (antisymmetry) pattern.

   示例：

   symmetry - "IsSimilarTo", "synonym", "marriage"

   skewsymmetry/anti-symmetric - "FatherOf", "member_of"

   

   注意：“反对称关系”不是“对称关系”的反义

   symmetric relation - 

   ∀x, y  r(x, y) $\Leftrightarrow$ r(y, x) 

   antisymmetric relation - 

   ∀x, y  r(x, y) with x $\ne$ y, then r(y, x)  must not hold

   or, equivalently,

   ∀x, y  r(x, y) and r(y, x), then x=y

   asymmetric relation - 

   a relation is asymmetric if, and only if, it is antisymmetric and irreflexive.

   <https://en.wikipedia.org/wiki/Symmetric_relation>

   <https://en.wikipedia.org/wiki/Antisymmetric_relation>

   

   Definition 2

   Relation r1 is inverse to relation r2 if 

   ∀x, y  r2(x, y) ⇒ r1(y, x)
   A clause with such form is a inversion pattern. (r1=r2$^{-1}$)

   示例：

   inversion - "hypernym and hyponym", "parent_of" is the inversion of "child_of"

   

   Definition 3

   Relation r1 is composed of relation r2 and relation r3 if 

   ∀x, y, z  r2(x, y) ∧ r3(y, z) ⇒ r1(x, z)
   A clause with such form is a composition pattern. (When r1=r2=r3, then this form is a transitive pattern.)

   示例：

   composition - "IsPartOf", "my mother’s husband is my father", "nationality = born_in_city & city_belong_to_nation"

   transitivity - (goldfish, kind of, fish) and (fish, kind of, animal), we can infer (goldfish, kind of, animal)

   BornInCity(a, b) ^ CityInCountry(b, c) $\Rightarrow$ Nationality(a, c)

   

   

   Definition 4

   A relation $r$ is reflexive (ir-reflexive) if 

   ∀x, y  r(x, x) $\in$ G ( r(x, x) $\notin$ G )

   A clause with such form is a reflexive (ir-reflexive) pattern.

   示例：

   reflexivity（自反性）- 与symmetry不完全等价

   irreflexivity（非自反性） - 与skewsymmetry/anti-symmetric不完全等价. such as hierarchies. "hypernym and hyponym"

   https://en.wikipedia.org/wiki/Reflexive_relation

   reflexivity will lead to self-loops!

   Note that graphs that do not allow these multiple edges and **self-loops** are called simple graphs.

   

   **推论**

   (1) if the models encode a reflexive relation r, they automatically encode symmetric

   (2) if the models encode a reflexive relation r, they automatically encode transitive

   (3) if entity e1 has relation r with every entity in $\triangle \in \mathcal{E}$ and entity e2 has relation r with one of entities in ∆, then e2 must have the relation r with every entity in ∆.

   

   (refer:

   Z. Sun, Z.-H. Deng, J.-Y. Nie, and J. Tang, “RotatE: Knowledge graph embedding by relational rotation in complex space,” in ICLR, 2019, pp. 1–18.

   Seyed Mehran Kazemi and David Poole. Simple embedding for link prediction in knowledge graphs. In Advances in Neural Information Processing Systems, pp. 4284–4295, 2018.)

   

2. 关系的类型

   类似于数学中函数的概念

   - 1-to-1

     一个关系 - 头实体和尾实体都只有一个，如Mary is a sibling of Tom.
     
   - 1-to-N, N-to-1

     一个关系 - 头实体一个/多个与尾实体多个/一个，如Amazon is a workplace for Mary, Tom, and Joe. Joe, Tom, and Mary work at Amazon.
     
   - N-to-N

     一个关系 - 头实体多个/尾实体多个，如Joe, Mary, and Tom are colleagues.
     
   - 1-many-1

     多个关系 - 头实体一个/尾实体一个，如(潘石屹, 夫妻, 张欣)，(潘石屹, 合伙人, 张欣)

     1-many-1 is so called multiple edges!

     A **multi-graph** is a graph that may have multiple edges with the same vertices (in the same direction).

     Note that graphs that do not allow these **multiple edges** and self-loops are called simple graphs.

     

3. 层级结构

   也可以归为，关系的性质之中——组合关系



## Summary1 

+ Overall, developing a novel KRL model is to answer the following questions: 

  1）which representation space to choose;

  从表示空间角度，可以分为欧几里得空间、复空间、流行空间，主要建模关系的性质，如关系的对称、不对称、倒置、组合等性质。

  

  + 关系的性质

    通过空间对象的性质表示（把关系的性质抽象为空间的性质） —— 关系建模为不同空间（如欧几里得空间、复空间、流行空间、概率空间等）中的映射，能否建模关系的这些性质，就看表示关系的向量、矩阵、张量、高斯分布等是否具有这些特点！

    通过转换方法的性质表示 —— translation or isometries，可以建模关系的不同性质

    

  + 关系的类型(1-to-N, N-to-1, N-to-N relations)

    它能够区分实体（实际上，在不同关系下，即使是1-to-N，实体也会被区分？）

  

  + 实体和关系属于相同的对象

    实体与关系在同一个空间建模，都表示为空间中的向量

    

  + 实体和关系属于不同的对象（所以预测实体与预测关系属于两个子任务）

    实体，通常表示为空间中的向量

    关系，表示为上述空间中的操作或运算，可能是向量、矩阵、张量、高斯分布等。从评分函数角度，可以把关系看成双线性或线性映射函数	

  

  2) how to measure the plausibility of triples in specific space; 

  从评分函数角度，可以分为基于翻译的模型及基于匹配的模型，前者主要基于距离的评分函数，后者主要基于相似度的评分函数。

  

  3) what encoding model to modeling relational interaction; 

  

  4) whether to utilize auxiliary information.

  

  5) else

  5.1）选择负样本
  
  How to generate a good negative example ? such as negative example from easy to hard example sampling.
  
  辅助负样本策略来处理关系的性质或类型（主要利用负样本技术，使层级关系对空间形成约束）
  
  
  
  5.2）使用约束条件
  
  构建约束条件，使之能处理关系的性质或类型......
  
  
  
  5.3）设计loss，如1-1 loss、1-n loss等多种loss加和？
  
  
  
  5.4）设计评估方法，如1-N scoring、N-N scoring？
  
  
  
+ 如何学习KG的层级结构？

  Euclidean space编码层级结构的方法：

  1）更高维度

  2）借鉴spherical tree embedding方法（韩家炜组）

  3）也许可以借助self-attention（bert的self-attention表现出语法的层级结构）

  Hyperbolic space非常适于编码层级结构！

  

+ 如何数据自适应（data adaptation）学习不同类型的关系？

  首先，模型是否需要具有关系的某些性质，本质上还要看各类关系的数据比例，即探索数据中存在哪些关系

  其次，模型要能够自适应学习数据中不同类型的关系

  1）引入关系的attention

  

+ 如何考虑可解释性？

  knowledge graph completion 另一个分支，path based reasoning/finding！

  
  
+ 



## Summary2 

refer:

**Tutorial 5 Representation Learning on Knowledge Graphs：From Shallow Embedding to Graph Neural Networks** [【PDF下载】](https://hub-cache.baai.ac.cn/hub-pdf/20201111/Tutorial 5 Representation Learning on Knowledge Graphs：From Shallow Embedding to Graph Neural Networks.pdf) [[▶视频回放\]](https://hub.baai.ac.cn/view/4018) Speaker: Yizhou Sun（UCLA）



+ 引入层级结构

  flat structure assumption - no additional structures, every triple is scored using the same form of score function

  方法：

  1）ontological concepts and meta relations - (instance view and ontological view - cross-view)

  > 层级结构，模型本身是可以学习到，只是这种显式地引入可以指导模型学得更好！最大的优点是，有效缓解长尾问题。

  paper:

  Universal Representation Learning of Knowledge Bases by Jointly Embedding Instances and Ontological Concepts

+ 引入不确定性

  Closed-world assumption - observed triples are true facts, unseen triples are false

  方法：

  1）logic rules and probabilistic soft logic

  paper:

  Embedding Uncertain Knowledge Graphs

+ 

+ 





more refer:

唐建：Neural and Symbolic Logical Reasoning on Knowledge Graphs [[▶\]](https://hub.baai.ac.cn/view/3865) 

> 将关系的性质看成逻辑规则（logical rules）（如对称/反对称规则、逆规则、组合规则等），因此，建模即学习这些规则。最大的优点是，具有可解释性！

+ Reasoning in Continuous Space

+ Symbolic logic reasoning

+ Neural-Symbolic logic reasoning

+ Logic Rule Induction/Learning

  paper:

  Meng Qu, Junkun Chen, Louis-Pascal AC Xhonneux, Yoshua Bengio, Jian Tang. “[RNNLogic: Learning Logic Rules for Reasoning on Knowledge Graphs](https://arxiv.org/pdf/2010.04029.pdf).”, arXiv:2010.04029.



## Keywords

KRL, knowledge representation learning

KGE, knowledge graph embedding

multi-relation learning

statistical relation learning



## Theory

+ ?



## Steps

表示学习方法，主要分为三个步骤：

1. 表示实体和关系

   实体，通常表示为空间中的向量

   关系，表示为上述空间中的操作或运算，可能是向量、矩阵、张量、高斯分布等

2. 定义得分函数

   得分函数，用来评估事实的合理性

3. 学习实体和关系的表示

   主要涉及优化方法，包括目标函数的定义、损失函数的选取、负样本抽样策略等



## Architecture

### assumption

open world assumption (OWA) - has a relaxed assumption that unobserved ones can be either missing or false.



closed world assumption (CWA) - assumes that unobserved facts are false



RESCAL is a typical model trained under the CWA, while more models are formulated under the OWA.

### model

##### representation space - representing entities and relations

Entities are usually represented as vectors, i.e., deterministic points in the vector space, multivariate Gaussian distributions.

Relations are typically taken as operations in the vector space, which can be represented as vectors, matrices, tensors, multivariate Gaussian distributions, or even mixtures of Gaussians.



###### point-wise Euclidean space (real-value)(关系或实体类型角度)

Most popularly !



关系和实体在一个空间里面（$\rm h,t,r \in \mathbb{R}^d$） - 向量 - TransE



关系和实体不在一个空间里面（通过一个映射矩阵$\mathrm{M}_r \in \mathbb{R}^{k \times d}$将实体空间$\rm h,t \in \mathbb{R}^k$映射到关系空间$\rm r \in \mathbb{R}^d$，再做计算） - 矩阵，以关系作为参照系，只有一个参照系（矩阵是线性变换） - TransR



关系和实体不在一个空间里面（动态映射） - TransD



关系由实体表达（$\rm{h}^T M t$，其中$\rm{M} \in \mathbb{R}^{d \times d \times k}$）- 张量，以实体为参照系，不同实体有不同参照系（张量是同一个线性变换在不同的基下的表示，而这里关系就对应到线性变换，实体就对应到基） - NTN



###### complex space(关系性质角度)

(motivation来源于ComplEx论文)

Embedding in complex vector space can model different relational connectivity patterns effectively, especially the symmetry/antisymmetry pattern.



点积 - 可以处理symmetry and (ir-)reflexivity of relations, 甚至是transitivity. 但是不能处理antisymmetric relations. 

> Dot product
>
> - symmetry
>
>   $u \cdot v = v \cdot u$
>
> - reflexivity
>
>   ？？？
>
> - ir-reflexivity
>
>   ？？？
>
> - transitivity
>
>   The Triangle Inequality for Inner Product Spaces:
>
>   $||u+v|| \le ||u|| + ||v||$
>
>   The triangle inequality turns out to be an elementary consequence of the Cauchy–Schwarz inequality, and hence is valid in any inner product space.
>
>   using an appropriate loss function even enables transitivity (Bouchard et al., 2015)



Hermitian product:
$$
\begin{align*}
<u,v>
&:=\bar u^Tv  \\
&=(Re(u)-iIm(u))^T(Re(v)+iIm(v))   \\
&= Re(u)^TRe(v)+Im(u)^TIm(v) + i(Re(u)^TIm(v)-Im(u)^TRe(v))   \\
\end{align*}
$$
where

$u=Re(u)+iIm(u)$ with $Re(u) \in \mathbb{R}^k$ and $Im(u) \in \mathbb{R}^k$, $u \in \mathbb{C}^k$.

A simple way to justify the Hermitian product for composing complex vectors is that it provides a valid topological norm in the induced vectorial space. 

For example, $\bar x^T x = 0$ implies $x = 0$ while this is not the case for the bilinear form $x^T x$ as there are many complex vectors for which $x^T x = 0$. :question:  

Hermitian (or sesquilinear) dot product - as it involves the conjugate-transpose of
one of the two vectors. As a consequence, the dot product is not symmetric any more, and facts about antisymmetric relations can receive different scores depending on the **ordering** of the entities involved. Thus complex vectors can effectively capture antisymmetric relations while retaining the efficiency benefits of the dot product, that is linearity in both space and time complexity. (实数部分，表示对称，虚数部分，表示非对称，这样一个复数，可以同时表示实体间的对称和非对称关系。当虚部为0，则表示实体间的对称关系；当虚部非0，则表示实体间的非对称关系。举例理解？成龙-父子->房祖名，可以用复数表示这种非对称关系)

> Hermitian product
>
> - symmetry
>
>   $<u,v> = <v,u>$, when the imaginary part of $u$ and $v$  are zero.
>
> - anti-symmetry
>
>   $<u,v> \neq <v, u>$
>
> - reflexivity
>
>   ？？？
>
> - ir-reflexivity
>
>   ？？？
>
> - transitivity
>
>   ？？？





实体和关系在同一个空间里面（$\rm h,t,r \in \mathbb{C}^d$, Take head entity as an example, $\rm h=Re(h) + i Im(h)$, $\rm Re(h)$ is real part and $\rm Im(h)$ is imaginary part） - 矩阵/张量 + factorization - ComplEx



实体和关系在同一个空间里面，关系定义为从头实体到尾实体的旋转（$\rm t=h \circ r$, $\circ$ is the Hadmard (element-wise) product, $h,r,t \in \mathbb{C}^k$） - RotatE

Hadmard product - 

Euler’s identity $e^{i \theta} =\rm cos \theta + i\ sin\theta$, which indicates that a unitary complex number can be regarded as a rotation in the complex plane.



实体和关系在同一个空间里面（$\rm h \otimes r$, $\rm h,r,t \in \mathbb{H}^d$） - QuatE

Hamilton product 





###### Manifold space(关系性质角度)

relaxes the real-valued point-wise space into manifold space/Lie group/dihedral group with more expressive representation from the geometric perspective.

A manifold is a topological space which could be defined as a set of points with neighborhoods by the set theory, while the group is algebraic structures defined in abstract algebra. 

Previous point-wise modeling is an ill-posed algebraic system where the number of scoring equations is far more than the number of entities and relations. And embeddings are restricted in an overstrict geometric form even in some methods with subspace projection.





Riemannian manifold - [hyperbolic space](https://en.wikipedia.org/wiki/Hyperbolic_space) $\mathbb{H}^n$, a multidimensional Riemannian manifold with a constant negative curvature, which can be isometrically embedded into $\mathbb{R}^{n+1}$ using the Minkowski inner product, is drawing attention for its capacity of capturing hierarchical information.

https://ronnybergmann.net/mvirt/manifolds/Hn.html



Informally, hyperbolic space can be thought of as a continuous version of trees and as such it is naturally equipped to model hierarchical structures. For instance, it has been shown that any finite tree can be embedded into a finite hyperbolic space such that distances are preserved approximately.



Hyperbolic space's application scenario

power-law distributed data, such as natural language (Zipf’s law [35]) and scale-free networks such as social and semantic networks

 (power-law distributions in datasets can often be traced back to hierarchical structures)



Hyperbolic space vs Euclidean space 

Euclidean space，建模complex relation patterns的能力，受限于embedding space的维度（it is necessary to increase the dimensionality of the embedding to model increasingly complex hierarchies）。单纯的linear embeddings（比如TransE）需要非常大的embedding size，而non-linear embeddings（比如Trans变体及deep neural network）可以在一定程度上减轻这个问题。





Hyperbolic space‘s advantages:

可以更加简单的表达层级结构，相比Euclidean/Complex embedding和deep neural networks，所需内存更少。

（当维度低（32维）时，也能编码层级结构（如tree），效果优于Euclidean space。当维度高（500维）时，略微优于Euclidean space。）



refer:

Maximilian Nickel, Douwe Kiela, Poincaré Embeddings for Learning Hierarchical Representations. 2017 https://paperswithcode.com/paper/poincare-embeddings-for-learning-hierarchical :star::star::star::star::star:



###### Gaussian distribution(关系或实体不确定性角度)

Gaussian embeddings are able to express the uncertainties of entities and relations, and multiple relation semantics.



关系由实体表达，头实体与尾实体不在一个空间（各自服从一个高斯分布）

（$\cal H-T$, $\cal H \sim N (\mu_h, \Sigma_h), T \sim N (\mu_t, \Sigma_t)$） - KG2E



关系、头实体与尾实体都不在一个空间（各自服从一个高斯分布），关系由头实体和尾实体构成的混合高斯分布组成

（$\cal H-T$, $\cal H \sim N (\mu_h, \Sigma_h), T \sim N (\mu_t, \Sigma_t)$） - TransG





###### Summary

The representation space plays an important role in encoding the semantic information of entities and capturing the relational properties. When developing a representation learning model, appropriate representation space should be selected and designed carefully to match **the nature of encoding methods** and balance **the expressiveness** and **computational complexity**.



Euclidean space - 欧式空间

Complex space - 欧几里得空间在复数域上推广，也称为酉空间

Manifold space - 非欧空间

Gaussian distribution - 通常定义在Euclidean space，也可以推广到Manifold space.



Hilbert space - 希尔伯特空间是有限维欧几里得空间的一个推广，使之不局限于实的情形和有限的维数，但又不失完备性，又叫完备的内积空间。

http://blog.sciencenet.cn/home.php?mod=space&uid=71626&do=blog&id=970050



##### scoring function - measuring the plausibility of facts (similarity)

评分函数，也叫the energy function in the energy-based learning framework.

评分函数，实际上就是如何评估两者的相似性，要求模型从相似角度学习实体及其关系。



**distance - Euclidean distance, Hadmard product, Manhattan distance, Poincaré distance, hyperbolic distance, ...**

**matching - dot product, Hamilton product, Hermitian product,... (deep neural network always using dot product!)**



###### distance (以加法规则为主)

utilizes the translation principle



the motivation of translation principle:

1. 从word2vec学习到词向量，实体之间存在一一对应的关系（Washington-American+China=? 这也是词向量评测的常用方法）。这里直接根据关系进行建模！



$\rm h+r-t$（中国+首都=北京. why not $\rm h+t=r$? 但是有$t-h=r$.） - TransE

In TransE, <u>relationships are represented as translations in the embedding space</u>: if (h, r, t) holds, then the embedding of the tail entity t should be close to the embedding of the head entity h plus some vector that depends on the relationship r. 

The relation is interpreted as a translation vector r so that the embedded entities h and t can be connected by r with low error.





###### semantic matching (以乘法规则为主)

employs compositional operators.

Its scoring function is defined with two versions of matching blocks - linear and bilinear block.







##### encoding models - modeling the semantic interaction of facts

###### linear/bilinear(关系->映射)

product-based functions over entities and relations

Linear models formulate relations as a linear/bilinear mapping by projecting head entities into a representation space close to tail entities.



Canonical methods with linear/bilinear encoding include SE [27], SME [34], DistMult [26], ComplEx [18], and ANALOGY [17].



Wang et al. [40] studied various bilinear models and evaluated their expressiveness and connections by introducing the concepts of universality and consistency.

Y. Wang, R. Gemulla, and H. Li, “On multi-relational link prediction with bilinear models,” in AAAI, 2018, pp. 4227–4234

###### factorization(关系->相关)

regard knowledge graphs as three-way tensors.

Factorization aims to decompose relational data into low-rank matrices for representation learning. 



Relational learning is concerned with domains where entities are interconnected by multiple relations. Hence, **correlations** can not only occur directly between entities or relations, but also across these interconnections of different entities and relations.





###### neural nets

play a critical role in modeling interactions of entities and relations.

Neural networks encode relational data with non-linear neural activation and more complex network structures.





###### cnn



###### rnn



###### transformers



###### gcn



##### auxiliary information - utilizing external information

textural - textual description

type -  relation/entity types

visual - entity images





A comprehensive summary of knowledge representation learning models

![kge_models_part1](https://github.com/bifeng/daily_book_notes/raw/master/resource/kge_models_part1.png)

![kge_models_part2](https://github.com/bifeng/daily_book_notes/raw/master/resource/kge_models_part2.png)



#### training strategies

##### loss function

First, margin-based loss is optimized to learn representations that positive samples have higher scores than negative ones. Some literature also called it as pairwise ranking loss. Most translation-based embedding methods use margin-based loss. 

The second kind of loss function is logistic-based loss, which is to minimize
negative log-likelihood of logistic models.

Other kinds of loss functions: the binary cross-entropy or the so-called Bernoulli negative log-likelihood loss function.



the logistic loss：
$$
\mathop{\min}_{\Theta} \sum_{\tau \in {\mathbb{D}^+ \cup \mathbb{D}^-}} \mathrm{log}(1+ \mathrm{exp}(-y_{hrt} \cdot f_r(h,t)))
$$
where

$\tau = (h,r,t)$ is a training example in $\mathbb{D}^+ \cup \mathbb{D}^-$, $\mathbb{D}^+$ is the positive set, $\mathbb{D}^-$ is the negative set.

$y_{hrt}=\pm1$ the label of that example.



the pairwise ranking loss：
$$
\mathop{\min}_{\Theta} \sum_{\tau^+ \in {\mathbb{D}^+}} \sum_{\tau^- \in { \mathbb{D}^-}} \mathrm{max}(0, \gamma - f_r(h,t) +  f_{r'}(h',t')))
$$
where

$\tau^+ = (h,r,t)$ is a positive example in $\mathbb{D}^+$

$\tau^- = (h',r',t')$ is a negative example in $\mathbb{D}^-$

$\gamma$ is a margin separating them.

最小化 the pairwise ranking loss的优势在于，它无需假设负样本是错误的，只需要它的得分较正样本低即可。



​	翻译距离的模型，通常选用 the pairwise ranking loss，语义匹配的模型，通常选用the logistic loss.



##### Negative Sampling

the number of negative samples generated per positive training sample

###### Uniform sampling

the widest applied one, uniformly replaces entities. But it leads to sampling false negative labels.



disadvantage: 

a uniform negative sampling suffers the problem of inefficiency since many samples are obviously false as training goes on, which does not provide any meaningful information



###### Bernoulli sampling

introduces a heuristic of sampling distribution as $\frac{tph}{tph+hpt}$ , where $tph$ and $hpt$ denote the average number of tail entities per head entity and the average number of head entities per tail entity respectively.

Then we define a Bernoulli distribution with parameter $\frac{tph}{tph+hpt}$ for sampling: given a golden triplet (h, r, t) of the relation r, with probability $\frac{tph}{tph+hpt}$ we corrupt the triplet by replacing the head, and with probability $\frac{hpt}{tph+hpt}$ we corrupt the triplet by replacing the tail.

应用案例：

TransH



###### Domain sampling

chooses corrupted samples from entities in the same domain or from the whole entity set with a relation-dependent...with the head and tail domain of relation...



###### Adversarial sampling



![kge_negative_sampling](https://github.com/bifeng/daily_book_notes/raw/master/resource/kge_negative_sampling.png)



###### Self-adversarial sampling

Z. Sun, Z.-H. Deng, J.-Y. Nie, and J. Tang, “RotatE: Knowledge graph embedding by relational rotation in complex space,” ICLR, 2019

self-adversarial negative sampling

samples negative triples according to the current embedding model.

Specifically, we sample negative triples from the following distribution:

...





###### Type Constraint

"[type constraint](https://www.dbs.ifi.lmu.de/~krompass/papers/TypeConstrainedRepresentationLearningInKnowledgeGraphs.pdf)" to corrupt entities with some limited entity sets determining by their relations.





##### 1-N scoring

Tim Dettmers, Pasquale Minervini, Pontus Stenetorp, and Sebastian Riedel. 2018. Convolutional 2D Knowledge Graph Embeddings. In Association for the Advancement of Artificial Intelligence.

Dettmers et al. (2018) introduce a 1-N scoring procedure to speed up training, i.e. we simultaneously score entity-relation pairs $(h, r)$ and $(t, r^{−1})$ with all entities $t ∈ \mathcal{E}$ and $h ∈ \mathcal{E}$ respectively, 



##### data augmentation 

Tim Dettmers, Pasquale Minervini, Pontus Stenetorp, and Sebastian Riedel. 2018. Convolutional 2D Knowledge Graph Embeddings. In Association for the Advancement of Artificial Intelligence.

Timothee Lacroix, Nicolas Usunier, and Guillaume ´Obozinski. 2018. Canonical Tensor Decomposition for Knowledge Base Completion. In International Conference on Machine Learning.

The standard data augmentation technique, first used by Dettmers et al. (2018) and formally described by Lacroix et al. (2018), of adding reciprocal relations for every triple in the dataset, i.e. we add $(t, r^{−1}, h)$ for every $(h, r, t)$.





#### complexity

Comparison of Models in Space and Time Complexity

![kge_complexity](https://github.com/bifeng/daily_book_notes/raw/master/resource/kge_complexity.png)

空间复杂度 - 模型的参数量

时间复杂度 - 模型的计算量

First, models which represent entities and relations as vectors (e.g., TransE, TransH, DistMult, and ComplEx) are more efficient. They usually have space and time complexity that scales linearly with d.

Second, models which represent relations as matrices (e.g., TransR, SE, and RESCAL) or tensors (e.g., NTN) usually have higher complexity in both space and time, scaling quadratically or cubically with the dimensionality of embedding space.

Finally, models based on neural network architectures (e.g., SME, NTN, MLP, and NAM) generally have higher complexity in time, if not in space, since matrix or even tensor computations are often required in these models.

n - the number of entities

m - the number of relations 

d - the dimensionality of entity embedding space

k - the dimensionality of relation embedding space 

## models

### translational-based  (energy function based)

这类模型使用基于距离的评分函数评估三元组的概率，将尾节点视为头结点和关系翻译得到的结果。

Translational distance-based methods borrowed the idea of distributed word representation learning and inspired many following approaches such as TransH and TransR which specify complex relations (1-to-N, N-to-1, and N-to-N) and the recent TransMS which models multi-directional semantics.

Two line of research improves TransE:

Introducing Relation-Specific Entity Embeddings - To overcome the disadvantages of TransE in dealing with 1-to-N, N-to-1, and N-to-N relations, an effective strategy is to allow an entity to have distinct representations when involved in different relations.

Relaxing Translational Requirement h + r ≈ t. -  Relaxing the overstrict requirement of h + r ≈ t.





##### SE  (cited 655) 2011

Paper:

A. Bordes, J. Weston, R. Collobert, and Y. Bengio, “Learning
structured embeddings of knowledge bases,” in Proc. 25th AAAI
Conf. Artif. Intell., 2011, pp. 301–306.



constraints:

$∀e ∈ E$, $||e||_2 ≤ 1$, //scale                            (1)

约束条件的作用：:question:

The normalization helps remove scaling freedoms from our model (where, for example, $E$ can be made smaller while $R^{lhs}$ and $R^{rhs}$ can be made larger and still give the same output).

##### UM (cited 306) 2012

A. Bordes, X. Glorot, J. Weston, and Y. Bengio, “Joint learning
of words and meaning representations for open-text semantic
parsing,” in Proc. 15th Int. Conf. Artif. Intell. Statist., 2012, pp.
127–135.





##### TransE - groundbreaking (cited 2029) 2013

Paper: 

A. Bordes, N. Usunier, A. Garc´ıa-Dur´an, J. Weston, and O. Yakhnenko, “Translating embeddings for modeling multirelational data” in Adv. Neural Inf. Process. Syst., 2013, pp. 2787–2795.

Bordes A, Usunier N, Garcia-Duran A, et al. Irreflexive and hierarchical relations as translations[J]. arXiv preprint arXiv:1304.7158, 2013.

Blog:

http://www.ccri.com/2018/06/27/use-transe-effectively/

http://pyvandenbussche.info/2017/translating-embeddings-transe/



score function:

$f_r(h,t) = ||\bold h + \bold r - \bold t  ||_{2}$

$\bold h, \bold t, \bold r \in \mathbb{R}^d$

constraints:

$∀e ∈ E$, $||e||_2 ≤ 1$, //scale                            (1)


约束条件的作用：

This constraint is important for our model, as it is for previous embedding-based methods...

1. remove scaling freedoms from the model 
2. makes the impact of the margin actually effective 
3. <u>regularizes</u> the optimization objective
4. <u>preventing</u> weights to collapse or diverge 有利于权重学习
5. 有利于相似度的比较计算 





Complexity:

$O(d)$ parameters per relation



Advantage:

It applies well to irreflexive, antisymmetric, inversion, composition and one-to-one relations.

irreflexive: 



antisymmetric:



inversion: 

if h+r1=t and t+r2=h, then r1=-r2  



composition: 

if h+r1=t and t+r2=t2, h+r3=t2, then r3=r1+r2



Disadvantage:

TransE has flaws in dealing with reflexive,symmetric, transitive,1-to-N, N-to-1, and N-to-N relations.

reflexive:

if h+r=h, then r=0

Therefore, TransE cannot infer reflexive relation with $r \neq 0$.



symmetric: 

if h+r=t and t+r=h, then r=0, h=t

Therefore, TransE cannot infer symmetric relation with $r \neq 0$.



transitive:

if h+r=t1, t1+r= t2, h+r=t2, then r=0, h=t1=t2



reflexive and irreflexive:

if TransE encodes a relation r, which is neither reflexive nor irreflexive the following equations should be held simultaneously: $h_1 + r = h_1$, $h_2 + r \ne h_2$. Therefore, both $r = 0$, $r \ne 0$ should be held, which result in contradiction. In this regard, TransE cannot encode a relation which is neither reflexive nor irreflexive. (Yanjie Wang, Rainer Gemulla, and Hui Li. On multi-relational link prediction with bilinear models. In Thirty-Second AAAI Conference on Artificial Intelligence, 2018.) ——解释比较牵强！存在这样的关系吗？反身性的关系非常少！（大部分关系都具有非反身性，比如对称性的关系(Bill Gates, marriage, Melinda Gates)，它具有非反身性，但是不具有反身性）



1-to-N relations:

$∃i = 1, · · · , p$ such that $(h, r, t_i) ∈ D^+$, TransE enforces $h + r ≈ t_i$ for all $i = 1, · · · , p$, and then $t_1 ≈ · · · ≈ t_p$.

示例：

三元组：（姜文，导演，让子弹飞）、（姜文，导演，一步之遥）和（姜文，导演，邪不压正）
transE: 让子弹飞≈一步之遥≈邪不压正。但实际上这三部电影是不同的实体，应该用不同的向量
来表示。



TransE的1-to-N relations推导不够严谨的，谨慎这种极端情况的推导！
$h+r-t_i=0$ 如果不对$t_i$这类做好负样本抵抗（使不同$t_i$之间具有差异），才有可能出现这种情况。因此，可以通过负样本策略避免这种情况。 



###### Question

1. transe使用了反向传播方法吗？
2. 第一个约束条件，放在了每个epoch前，而不是每个batch前？
3. 为什么没有对关系做约束？
4. 怎么保证这个东西work？是否可导？

$$
\begin{align*}
\mathcal{L} 
& = \sum_{(h,r,t)\in S} \sum_{(h',r,t')\in S} [\gamma + d(h+r,t)- d(h'+r,t')]_+ \\
& = \sum_{(h,r,t)\in S} \sum_{(h',r,t')\in S} \max\{0, \gamma + d(h+r,t)- d(h'+r,t')\}\\
\end{align*}
$$

$h = h - \alpha \frac{\partial \mathcal{L}}{\partial h}$

设$f = \gamma + d(h+r,t)- d(h'+r,t')$
$$
\begin{align*}
\frac{\partial \mathcal{f}}{\partial h} 
&=  \frac{\partial \mathcal{f}}{\partial d} \frac{\partial \mathcal{d}}{\partial h} \\
&=  \frac{\partial \mathcal{d}}{\partial h} \\
\end{align*}
$$
$d$ 为$L_1$  虽然$L_1$范数在0处不可导，但存在次梯度，即$ \frac{\partial ||x||_1}{\partial x}  =g$
$$
g=
\begin{cases}
sign(x) \quad x \neq 0 \\
[-1,1]  \quad \ \ x =0
\end{cases}
$$
设$f = h+r-t$
$$
\begin{align*}
\frac{\partial \mathcal{d}}{\partial h} 
&=  \frac{\partial d}{\partial f} \frac{\partial f}{\partial h}\\ 
&= \frac{\partial \mathcal{d}}{\partial f}  \\
&= \frac{\partial \mathcal{||f||_1}}{\partial f}  \\
&= g

\end{align*}
$$
$d$为$L_2$ 
$$
\begin{align*}
\frac{\partial \mathcal{d}}{\partial h} 
&= \frac{\partial \mathcal{||h+r-t||_2}}{\partial h} \\
&= 2 \ (h+r-t)
\end{align*}
$$











##### TransH (cited 1032) 2014

Paper:

Z. Wang, J. Zhang, J. Feng, and Z. Chen, “Knowledge graph
embedding by translating on hyperplanes,” in Proc. 28th AAAI
Conf. Artif. Intell., 2014, pp. 1112–1119.



By introducing the mechanism of projecting to relation-specific **hyperplanes**, TransH enables different roles of an entity in different relations.

将实体表示映射到与关系相关的超平面（每个关系都有与之对应的超平面）



score function:

$f_r(h,t) = || \bold h_{\perp}  +\bold  r -\bold  t_{\perp}  ||^2_2$

where

$ \bold h_{\perp} = \bold h -  \bold w^{\top}_r  \bold h  \bold w_r$

$ \bold t_{\perp} = \bold t -  \bold w^{\top}_r  \bold t  \bold w_r$

$\bold h, \bold t, \bold r, \bold w_r \in \mathbb{R}^d$

其中，$ \bold w_r$为超平面的法向量。

constraints:

$∀e ∈ E$, $||e||_2 ≤ 1$, //scale                            (1)
$∀r ∈ R, |w^{\top}_r r|/||r||_2 ≤ \epsilon$, //orthogonal         (2)
$∀r ∈ R, ||w_r||_2 = 1$, //unit normal vector      (3)





$h_{\perp}$ - 向量$h$在超平面上的投影，即投影向量。根据超平面的法向量可计算任意向量的投影向量。



注意：

1. 根据超平面定义，超平面的维数应该等于原有空间的维数减一，但是这里不需要真的知道超平面，只需要知道超平面的法向量即可。 

2. <u>实体向量$h$或$t$与关系向量$r$都是在一个空间</u>！这里不关心超平面的具体公式（它应该是属于实体向量空间的超平面），只关心这个超平面是由关系法向量$w_r$决定（即超平面的方向）。 也就是说这个超平面只是方便实体向量在其上面的映射。 

3. 怎么使关系向量$r$和实体向量在一个空间？怎么把关系向量$r$放在超平面里面将$h_{\perp}$和$t_{\perp}$联系起来？这就是第二个约束条件的作用！  

   

In mathematics, a hyperplane H is a linear subspace of a [vector](https://deepai.org/machine-learning-glossary-and-terms/vector) space V such that the basis of H has cardinality one less than the cardinality of the basis for V.  In other words, if V is an n-dimensional vector space than H is an (n-1)-dimensional subspace.

n维空间中的超平面由下面的方程确定：

$w^{\top} x + b = 0$ 

其中，$w$为平面的法向量（法向量的维数也是n维），$b$为平面到原点的距离。 超平面的维数为n-1维。

示例：

`a1*x1+a2*x2+b=0` - 二维空间的超平面，即直线

...




$$
\begin{align}
\mathcal{L} = \sum_{(h,r,t)\in \triangle} \sum_{(h',r',t') \in \triangle'} [f_r(\bold{h},\bold {t}) + \gamma - f_{r'}(\bold h',\bold t')]_+ 
+C \Big\{ ...\Big\}
\end{align}
$$




Complexity:

$O(2d)$ parameters per relation

$O(nd+2md)$ parameters 

n - the number of entities

m - the number of relations 

d - the dimensionality of entity/relation embedding space



Advantage

TransH can encode reflexive, one-to-many, many-to-one and many-to-many relations.

can infer and model the symmetry/antisymmetry

symmetry: if r(h,t) and r(t,h) hold, then is identical the truth.

antisymmetry:

one-to-many: if r(h,t1), r(h,t2) and r(h,t3) hold, then t1, t2 and t3 have different module length ($||t1|| \ne ||t2|| \ne ||t3||$), but with identical project vector in hyperplane ($t1_{\perp} =t2_{\perp} =t3_{\perp} $).





Disadvantage

cannot infer inversion and composition

inversion: if r1(h,t) and r2(t,h) hold, then r1=r2, but the truth is r1=r2^-1



composition:



(Kazemi & Poole, 2018) prove that encoding reflexive results in encoding the both symmetric and transitive which is undesired.(Seyed Mehran Kazemi and David Poole. Simple embedding for link prediction in knowledge graphs. In Advances in Neural Information Processing Systems, pp. 4284–4295, 2018.)







###### Question

1. 虽然有超平面，为什么不在超平面计算而在原有空间计算$h_{\perp}+r -t_{\perp}$ ?

   在SVM中，主要是把低维映射到高维，从而非线性转化为线性问题，在高维的超平面中计算，可以减少计算量...

2. 为什么没有把关系向量$r$也映射到超平面？而要放在目标函数的约束条件（第二个）中去？

   如果也映射过去，则对关系向量的约束太严格（关系向量与法向量正交），而且关系向量所在的空间也与超平面所在的空间不相同。

3. 为什么没有把第三个约束条件放在目标函数中去优化？而是在mini-batch中去？

4. 怎么使关系向量$r$在另外一个空间，即不与实体向量共享一个空间？ 

5. 不需要学习法向量的参数吗？



##### TransR+CTransR: Cluster-based TransR (cited 1114) 2015

Paper:

Y. Lin, Z. Liu, M. Sun, Y. Liu, and X. Zhu, “Learning entity and relation embeddings for knowledge graph completion,” in Proc. 29th AAAI Conf. Artif. Intell., 2015, pp. 2181–2187.



Motivation:

1. Relations and entities are completely different objects, it may be not capable to represent them in a common semantic space

2. <u>An entity may have multiple aspects, and various relations focus on different aspects of entities</u>. Hence, it is intuitive that some entities are similar and thus close to each other in the entity space, but are comparably different in some specific aspects and thus far away from each other in the corresponding relation spaces.

存在相似的实体，在一个实体空间里面会聚集，但是在不同关系下，即在关系空间中它们之间的距离应该比较远。如果实体和关系在一个空间，则不能很好地区分，而在各自空间下，可以有更好的区分度。

示例：

中国 <- 北京

北京 <- 北京大学

中国 <- 亚洲

...

上述关系，大体上都是“位于，属于，包含”, 但细分下包含国家-城市, 国家-大学, 国家-洲等关系。



By introducing the mechanism of projecting to relation-specific **spaces**, TransR enables different roles of an entity in different relations.

将实体表示转换到关系对应的子空间

score function:

$f_r(h,t) = || \bold h_{\perp}  +\bold  r -\bold  t_{\perp}  ||^2_2$

where

$\bold h_\perp=\bold  M_r \bold  h$ 

$\bold  t_\perp=\bold  M_r \bold t$

$\bold h, \bold t \in \mathbb{R}^d$, $\bold r \in \mathbb{R}^k$, $\bold M_r \in \mathbb{R}^{k \times d}$

其中，$\bold M_r$为实体空间到关系空间的转换矩阵。



Constraints:

$||h||_2 \leq 1$, $||r||_2 \leq 1$, $||t||_2 \leq 1$    (1)

$||M_rh||_2 \leq 1$, $||M_rt||_2 \leq 1$          (2)





Complexity:

$O(dk)$ parameters per relation

$O(nd+mdk)$ parameters 

n - the number of entities

m - the number of relations 

d - the dimensionality of entity embedding space

k - the dimensionality of relation embedding space 



Advantage:

can infer and model the symmetry/antisymmetry



Disadvantage:







###### Question

1. 怎么使关系向量$r$在另外一个空间，即不与实体向量共享一个空间？ 

   使它们之间的维度不同，应该不是充要条件！

2. 第二个约束条件的作用？

3. 



##### TransD (cited 447) 2015

Paper:

G. Ji, S. He, L. Xu, K. Liu, and J. Zhao, “Knowledge graph
embedding via dynamic mapping matrix,” in Proc. 53rd Annu.
Meeting Assoc. Comput. Linguistics 7th Int. Joint Conf. Natural
Language Process., 2015, pp. 687–696.



Motivation (several flaws of TransR/CTransR):

 (1) For a typical relation r, all entities share <u>the same mapping matrix</u> Mr. However, the entities linked by a relation always contains various types and attributes. For example, in triplet (friedrich burklein, nationality, germany), friedrich burklein and germany are typical different types of entities. These entities should be projected in different ways; 

(2) The projection operation is an interactive process between an entity and a relation, it is unreasonable that <u>the mapping matrices</u> are determined only by relations;

(3) Matrix-vector multiplication makes it has large amount of calculation, and when relation number is large, it also has much more parameters than TransE and TransH.



TransD simplifies TransR by further decomposing the projection matrix into a product of two vectors.

The first vector represents the meaning of an entity or a relation.

The second vector (called projection vector) represents the way that how to project a entity embedding into a relation vector space and it will be used to construct mapping matrices.

Therefore, every entity-relation pair has an unique mapping matrix.  -  dynamic mapping matrix for each entity-relation pair by considering the diversity of entities and relations simultaneously.



score function:

$f_r(h,t) = || \bold h_{\perp}  +\bold  r -\bold  t_{\perp}  ||^2_2$

where

$\rm \bold h_⊥ =\bold M_{rh} \bold h$,    $\rm \bold t_⊥ = \bold M_{rt} \bold t$

$\rm \bold M_{rh} = \bold w_r \bold w^{\top}_h + \bold I$,    $\rm \bold M_{rt} = \bold w_r \bold w^{\top}_t + \bold I$ 

$\rm\bold h, \bold t \in \mathbb{R}^d$, $\rm \bold r \in \mathbb{R}^k$ - the first vector

$\rm \bold w_h, \bold w_t \in \mathbb{R}^d$, $\rm \bold w_r \in \mathbb{R}^k$ - the second vector

$\bold I \in \mathbb{R}^{k \times d}$ is an identity matrix (单位矩阵) - 初始化



In addition, TransD has no matrix-vector multiplication operation which can be replaced by vector operations. The projected vectors can be computed as follows:

$\rm \bold h_⊥ =\bold M_{rh} \bold h =(\bold w_r \bold w^{\top}_h + \bold I) \bold h=\bold w^{\top}_h \bold h \bold w_r+ \bold I \bold h $

...



Constraints:

$||\bold h||_2 \leq 1$, $||\bold r||_2 \leq 1$, $||\bold t||_2 \leq 1$    (1)

$||\bold h_⊥||_2 \leq 1$, $||\bold t_⊥||_2 \leq 1$                (2)





Complexity:

$O(nd+mk)$ parameters  

n - the number of entities

m - the number of relations 

d - the dimensionality of entity embedding space

k - the dimensionality of relation embedding space 







##### else

###### TransM (cited 77) 2014

Paper:

M. Fan, Q. Zhou, E. Chang, and T. F. Zheng, “Transition-based
knowledge graph embedding with relational mapping properties,”
in Proc. 28th Pacific Asia Conf. Language, Inf., Comput., 2014,
pp. 328–337.



###### TransF (cited 41) 2015

Paper:

J. Feng, M. Zhou, Y. Hao, M. Huang, and X. Zhu, “Knowledge
graph embedding by flexible translation,” in arXiv:1505.05253,
2015.



Instead of enforcing the strict translation h+r ≈ t, TransF only requires t to lie in the same direction with h+r, and meanwhile h in the same direction with t−r.

$f_r(h,t) = \rm (h+r)^{\top} t + (t-r)^{\top} h$



###### TransA (cited 47) 2015

Paper:

H. Xiao, M. Huang, Y. Hao, and X. Zhu, “TransA: An adaptive
approach for knowledge graph embedding,” in arXiv:1509.05490,
2015.



Euclidean distance -> Mahalanobis distance





###### TranSparse (cited 177) 2016 

Paper:

G. Ji, K. Liu, S. He, and J. Zhao, “Knowledge graph completion
with adaptive sparse transfer matrix,” in Proc. 30th AAAI Conf.
Artif. Intell., 2016, pp. 985–991.



##### summary

TransE，适用于一对一关系，不能处理一对多和多对一关系（如一对多关系$r_m$,满足$h+r_m \approx t_m$,TransE不能有效地区分不同实体，导致$t_1=t_2=\dots =t_m$）



TransH、TransR部分解决了TransE存在的问题



TransE、TransH、TransR，采用对称式打分函数，不能处理自反关系（不能有效区分不同关系）。



TransD，采用非对称式打分函数（考虑实体的顺序）



#### Gaussian Distribution

###### KG2E (cited 142) 2015

Paper:

S. He, K. Liu, G. Ji, and J. Zhao, “Learning to represent knowledge graphs with Gaussian embedding,” in Proc. 24th ACM Int. Conf. Inf. Knowl. Manage., 2015, pp. 623–632.



A more elegant and rigorous approach to model the 1-to-N, N-to-1, and N-to-N relations is to leverage a probabilistic framework to model the uncertainties of the entities, where each predicted entity is represented as a Gaussian distribution. 



KG2E scores a fact by measuring the distance between the two random vectors of $t−h$ and $r$.



###### TransG (cited 148) 2016

Paper:

H. Xiao, M. Huang, and X. Zhu, “TransG: A generative model for
knowledge graph embedding,” in Proc. 54th Annu. Meeting Assoc.
Comput. Linguistics, 2016, pp. 2316–2325.



TransG（贝叶斯非参数无限混合表示模型），处理关系的多语义问题



#### Manifold Space

###### ManifoldE(cited 59) 2016

H. Xiao, M. Huang, and X. Zhu, “From one point to a manifold:
Knowledge graph embedding for precise link prediction,” in
Proc. 25th Int. Joint Conf. Artif. Intell., 2016, pp. 1315–1321.



###### TorusE(cited 40) 2018

T. Ebisu and R. Ichise, “TorusE: Knowledge graph embedding on
a lie group,” in AAAI, 2018, pp. 1819–1826.



TorusE focuses on the problem of regularization in TransE



###### DihEdral 2019



##### Hyperbolic Space

###### Poincaré 2017 

more:

Maximilian Nickel, Douwe Kiela, Poincaré Embeddings for Learning Hierarchical Representations. 2017 https://paperswithcode.com/paper/poincare-embeddings-for-learning-hierarchical :star::star::star::star::star:

http://bjlkeng.github.io/posts/hyperbolic-geometry-and-poincare-embeddings/





Poincare ball model

There exist multiple, equivalent models of H such as the Beltrami-Klein model, the hyperboloid model, and the Poincaré half-plane model. In the following, we will base our approach on the Poincaré ball model, as it is well-suited for gradient-based optimization. This allows us to develop an efficient algorithm for computing the embeddings based on Riemannian optimization, which is easily parallelizable and scales to large datasets.







###### MuRP 2019

Ivana Balazevi ˇ c, Carl Allen, and Timothy Hospedales. ´ 2019. Multi-relational poincare graph embeddings. ´ In Advances in Neural Information Processing Systems, pages 4465–4475.



###### AttH 2020

paper: Low-Dimensional Hyperbolic Knowledge Graph Embeddings. https://paperswithcode.com/paper/low-dimensional-hyperbolic-knowledge-graph-1



1. KG的层级性质

   从局部看，KG具有不同类型的关系，从整体看，KG表现出层级的结构。

   如果编码空间能够保留层级结构（即非邻居节点相距较远...），则在推断时，更具有区分度。

2. isometries-based

   相比translation-based，isometries-based的几何性质可以建模不同类型的关系。

3. atttention

   基于attention可以适应数据中多种类型的关系（attentionbased transformations generalize to multiple relations）





### matching-based 

这类模型使用基于相似度的评分函数评估三元组的概率，将实体和关系映射到隐语义空间中进行相似度度量。

As for the semantic matching side, many methods utilizes mathematical operations or compositional operators including linear matching in SME, bilinear mapping in DistMult, tensor product in NTN, circular correlation in HolE and ANALOGY, Hadamard product in CrossE, and quaternion inner product in QuatE.

##### TATEC (cited 33) 2014

Paper:

A. Garc´ıa-Dur´an, A. Bordes, and N. Usunier, “Effective blending
of two and three-way interactions for modeling multi-relational
data,” in ECML. Springer, 2014, pp. 434–449.



##### SME (cited 387) 2014

Paper:

A. Bordes, X. Glorot, J. Weston, and Y. Bengio, “A semantic
matching energy function for learning with multi-relational data,”
Machine Learning, vol. 94, no. 2, pp. 233–259, 2014.



Semantic Matching Energy



constraints:

$∀e ∈ E$, $||e||_2 ≤ 1$, //scale                            (1)

约束条件的作用：

The normalization helps remove scaling freedoms from the model, makes the impact of the margin actually effective and <u>regularizes</u> the optimization objective, <u>preventing</u> weights to collapse or diverge.



##### HolE  (cited 432) 2016

Paper:

Maximilian Nickel, Lorenzo Rosasco, Tomaso Poggio, “Holographic embeddings of knowledge graphs,” in AAAI, 2016, pp. 1955–1961. [arxiv](https://arxiv.org/abs/1510.04935) 

Bolg:

<https://mnick.github.io/project/knowledge-graph-embeddings/>



**Compositional vector space models**





Holographic Embeddings (HolE) model antisymmetry

In HolE the <u>circular correlation</u> is used for combining entity embeddings, measuring the covariance between embeddings at different dimension shifts. This generally suggests that other composition functions than the classical tensor product can be helpful as they allow for a richer interaction of embeddings. However, <u>the asymmetry in the composition function in HolE stems from the asymmetry of circular correlation</u>, an O(nlog(n)) operation.



Circular correlation:







##### ANALOGY (cited 110) 2017

Paper:

H. Liu, Y. Wu, and Y. Yang, “Analogical inference for multirelational
embeddings,” in ICML, 2017, pp. 2168–2178.



##### CrossE  (cited 23) 2019

Paper:

W. Zhang, B. Paudel, W. Zhang, A. Bernstein, and H. Chen, “Interaction
embeddings for prediction and explanation in knowledge
graphs,” in WSDM, 2019, pp. 96–104.



#### tensor factorization

##### MF (cited 915) 2008

Paper:

Singh, Ajit P., and Geoffrey J. Gordon. "Relational learning via collective matrix factorization." *Proceedings of the 14th ACM SIGKDD international conference on Knowledge discovery and data mining*. 2008.



##### RESCAL  (cited 906) 2011

Paper:

Maximilian Nickel, Volker Tresp, and Hans-Peter Kriegel, “A three-way model for collective learning on multi-relational data,” in Proc. 28th Int. Conf. Mach. Learn., 2011, pp. 809–816.

Nickel M, Tresp V, Kriegel H P. Factorizing yago: scalable machine learning for linked data[C]//Proceedings of the 21st international conference on World Wide Web. 2012: 271-280. - The authors further extended it to handle attributes of entities efficiently.





motivation to use tensor:

manifold

1) From a modeling perspective tensors provide simplicity, as multiple relations of any order can be expressed straightforwardly as a higher order tensor.

2) From a learning perspective is that relational domains are usually high-dimensional and sparse, a setting where factorization methods have shown very good results.



利用多个低维的矩阵或张量的积代替原始的（稀疏）关系矩阵，通过低维矩阵的分布式表示实现关系矩阵中蕴含的复杂关系的**解耦**！（类似于word embedding）

Maximilian Nickel将矩阵分解方法推广到三维张量空间（rank-r factorization），提出RESCAL模型：

$\mathcal{X}_k \approx AR_kA^T$,  for $k=1,\dots,m$

$\mathcal{X}_k$为三维张量，其中每个二维矩阵切片代表一种关系，如果两个实体存在某种关系，则将矩阵中对应的值标为1，否则为0；

$A$ 为$n \times r$矩阵，denote the latent-component representation of the entities in the domain，实体矩阵$A$的每一行代表一个实体的向量；

$R_k$为$r\times r$非对称矩阵，denote the relations in the domain，三维张量$R$的每个切片$R_i$表示第$i$种关系。其中，the asymmetry of $R_k$ takes into account whether a latent component occurs as a subject or an object.



score function:

$f_r(h,t)=\bold h^{\top} \bold M_r \bold t = \sum^{d-1}_{i=0} \sum^{d-1}_{j=0} [\bold M_r]_{ij} \cdot [\bold h]_i \cdot [\bold t]_j$

where

$\bold h, \bold t \in \mathbb{R}^d$, $\bold M_r \in \mathbb{R}^{d \times d}$





$$
\min_{A,R_k} f(A,R_k) + g(A,R_k)
$$
where

$f(A,R_k) = \frac{1}{2} \bigg( \sum_k || \mathcal{X_k} - AR_kA^{T} ||^2_F \bigg)$

$g(A,R_k) = \frac{1}{2} \lambda \bigg( ||A||^2_F + \sum_k ||R_k||^2_F \bigg)$



优化：

1. any nonlinear optimization algorithm, such as  alternating least-squares (ALS) approach.
2. a stochastic gradient descent approach



注意:

1. 每个关系，都有一个关系矩阵（$\bold M_r$）

2. 联合优化，实体（$\bold h, \bold t$）是共享的

   



优点：

1. 在不同关系下，一个实体可能存在不同的domain
2. 在一个关系下，一个实体只有一个domain，而不管它是头实体还是尾实体

缺点：

1. 



more:

An extensive review of tensor decompositions and their applications can be found in (Kolda & Bader, 2009).

Kolda, Tamara G. and Bader, Brett W. Tensor decompositions and applications. SIAM Review, 51(3):455—500, 2009. ISSN 00361445. doi: 10.1137/07070111X. URL http://link.aip.org/link/SIREAD/v51/i3/p455/s1&Agg=doi.



###### Question

1. 张量分解使用了反向传播方法吗？

2. 这种能够建模关系的非对称性？

3. 梯度下降方法可以保证学习的关系是an asymmetric r × r matrix？

4. 

   

Summary

1. 该张量分解方法对输入矩阵没有约束条件

   The model can be considered a relaxed version of DEDICOM or equivalently, an asymmetric extension of IDIOSCAL. 

   The rank-r DEDICOM  decomposition of a three-way tensor: $\mathcal{X}_k \approx AD_kRD_kA^T$, for $k=1,\dots,m$. where $A$  is a $n×r$ matrix that contains the latent components and $R$ is an asymmetric $r × r$ matrix that models the global interactions of the latent components. The diagonal $r × r$ matrix $D_k$ models the participation of the latent components in the k-th predicate.

   

   The model can be regarded as a restricted Tucker3 model.

   Turcker3 model: $X_{(n)} = AG_{n}(C \otimes B)^T$

   

   

##### DistMult (cited 582) 2015

Paper:

B. Yang, W.-t. Yih, X. He, J. Gao, and L. Deng, “Embedding entities
and relations for learning and inference in knowledge bases,” in
ICLR, 2015, pp. 1–13.



score function：

$f_r(h,t)=\bold h^{\top} \rm diag(\bold r) \bold t = \sum^{d-1}_{i=0}  [\bold r]_{i} \cdot [\bold h]_i \cdot [\bold t]_i$ 

where

$\bold h, \bold r, \bold t \in \mathbb{R}^d$





Advantage

symmetric: $\bold h^{\top} \rm diag(\bold r) \bold t  = \bold t^{\top} \rm diag(\bold r) \bold h $

多对多关系



Disadvantage

can model the asymmetric and inversion








##### LFM (cited 331) 2012

Paper:

R. Jenatton, N. L. Roux, A. Bordes, and G. R. Obozinski, “A latent
factor model for highly multi-relational data,” in NIPS, 2012, pp.
3167–3175.



##### TATEC (cited 33) 2014

TATEC A. Garc´ıa-Dur´an, A. Bordes, and N. Usunier, “Effective blending
of two and three-way interactions for modeling multi-relational data,” in Proc. Joint Eur. Conf. Mach. Learn. Knowl. Discovery
Databases, 2014, pp. 434–449.



##### SimplE (cited 85) 2018

Paper:

S. M. Kazemi and D. Poole, “SimplE embedding for link prediction
in knowledge graphs,” in NeurIPS, 2018, pp. 4284–4295.



Introduce the concept of full expressiveness: 

a model is fully expressive if, given any valid graph, there exists at least one combination of embedding values for the model that correctly separates all correct triples from incorrect ones.



Canonical Polyadic (CP) decomposition (Hitchcock, 1927), in which subject and object entity embeddings for the same entity are independent (note that DistMult is a special case of CP). 

SimplE’s scoring function alters CP to make subject and object entity embedding vectors dependent on
each other by computing the average of two terms, first of which is a bilinear product of the subject
entity head embedding, relation embedding and object entity tail embedding and the second is a bilinear product of the object entity head embedding, inverse relation embedding and subject entity tail embedding.



score function：

$f_r(h,t) =\frac{1}{2}( <\bold h, \bold r , \bold t >+<\bold t  ,\bold r^{-1},  \bold h>)$ 

where

$\bold h, \bold r,  \bold r^{-1}, \bold t \in \mathbb{R}^d$







##### TuckER (cited 34) 2019

Paper:

I. Balaˇzevi´c, C. Allen, and T. M. Hospedales, “TuckER: Tensor
factorization for knowledge graph completion,” in EMNLPIJCNLP,
2019, pp. 5185–5194.



Tucker decomposition (Tucker, 1966) factorizes a tensor into a core tensor multiplied by a matrix along each mode. 

It can be thought of as a form of higher order SVD in the special case where matrices are orthogonal and the core tensor is “all-orthogonal” (Kroonenberg and De Leeuw, 1980).



Subject and object entity embedding matrices are assumed equivalent, i.e. we make no distinction between the embeddings of an entity depending on whether it appears as a subject or as an object in a particular triple. 



score function：

$f_r(h,t) = \mathcal{W} \times_{1} \bold h \times_{2} \bold r \times_{3}  \bold t $ 

where

$\bold h, \bold t \in \mathbb{R}^{d_e}$ 

$ \bold r \in \mathbb{R}^{d_r}$ 

$\mathcal{W} \in \mathbb{R}^{d_e \times d_r \times d_e}$ is the core tensor.

Rather than learning distinct relation-specific matrices, the core tensor of TuckER can be viewed as containing a shared pool of “**prototype**” relation matrices, which are linearly combined according to the parameters in each relation embedding.



**Representing Asymmetric Relations**

So far, there have been two possible ways in which linear link prediction models introduce asymmetry into factorization of the binary tensor of triples:

+ distinct (although possibly related) embeddings for subject and object entities and a diagonal matrix (or equivalently a vector) for each relation, as is the case with models such as ComplEx and SimplE; or
+ equivalent subject and object entity embeddings and each relation represented by a full rank matrix, which is the case with RESCAL and TuckER.

The latter approach appears more intuitive, since asymmetry is a property of the relation, rather than the entities.





**Advantage**

Its fully expressive.

Its number of parameters increases linearly with respect to entity and relation embedding dimension, as the number of entities and relations increases, since the number of parameters of $\mathcal{W}$ depends only on the entity and relation embedding dimensionality and not on the number of entities or relations.



**Disadvantage**





###### Question

+ How to understand "fully expressive" ?
+ 



##### Complex Space

###### ComplEx  (cited 467) 2016

Paper: 

T. Trouillon, J. Welbl, S. Riedel, ´ E. Gaussier, and G. Bouchard, “Complex embeddings for simple link prediction,” in ICML, 2016, pp. 2071–2080.

[Knowledge Graph Completion via Complex Tensor Factorization](http://www.jmlr.org/papers/volume18/16-563/16-563.pdf), Théo Trouillon, Christopher R. Dance, Éric Gaussier, Johannes Welbl, Sebastian Riedel and Guillaume Bouchard, JMLR 2017. 该论文详细论述了算法细节！

This paper has applied [Patent](<https://patentimages.storage.googleapis.com/7e/80/0a/42e2e59514d001/US20170337481A1.pdf>). 



考虑一个关系的情形

$P(Y_{so}=1) = \sigma(X_{so})$

...

$X = E W \bar E^{T}$

where 

$W \in \mathbb{C}^{n \times n}$ is the diagonal matrix (对角矩阵) of eigenvalues (with decreasing modulus)

$E  \in \mathbb{C}^{n \times n}$ is a unitary matrix (酉矩阵) of eigenvectors 

$\bar E  \in \mathbb{C}^{n \times n}$ representing its complex conjugate.

However, far from all matrices expressed as $X = E W \bar E^{T}$ are purely real, So we simply keep only the real part of the decomposition:

$X = Re(E W \bar E^{T})$

notes:

$EW\bar E^T$ 采用复数的Hermitian内积计算，计算结果依然是复数

$Re(E W \bar E^{T})$ 只取计算结果的实部，为什么也可以呢？作者在另外一篇论文（Trouillon et al.(2016)）中证明了 - performing this projection on the real subspace allows the exact decomposition of any real square matrix $X$ and not only normal ones.也就是说，如果只取实部，那么可以对任意实数矩阵进行分解，而不一定要求是正规矩阵！**这里保证了特征值分解可以用于任意矩阵！**



Compared to the singular value decomposition, the eigenvalue decomposition has two key differences:

- The eigenvalues are not necessarily positive or real;
- The factorization is useful as the rows of E can be used as vectorial representations of the entities corresponding to rows and columns of the relation matrix X. Indeed, for a given entity, its subject embedding vector is the <u>complex conjugate</u> of its object embedding vector



Low-Rank Decomposition

> Assumption：**the binary relation matrix is low sign-rank.**
>
> If the observation matrix $Y$ is low-sign-rank, then our model can decompose it with a rank at most the double of the sign-rank of $Y$ . That is, for any $Y ∈ \{−1, 1\}^{n×n}$, there always exists a matrix $X = Re(EW\bar E^T)$ with the same sign pattern $\rm sign(X) = Y$ , where the rank of $EW\bar E^T$ is at most twice the sign-rank of $Y$ (Trouillon et al., 2016). 
>
> ...

$X = Re(E W \bar E^{T})$

where

$W \in \mathbb{C}^{k \times k}$

$E \in \mathbb{C}^{n \times k}$

$k$ is the rank.





考虑多个关系的情形

We do so by allocating an embedding $W_r$ to each relation $r$, and by sharing the entity embeddings across all relations.

$P(Y_{rso}=1) = \sigma( \phi (r,s,o; \Theta))$

...

$$
\begin{align*}
X_r 
&= Re(E W_r \bar E^{T}) \\
&= Re((Re(E)+iIm(E))(Re(W_r)+iIm(W_r))(Re(E)-iIm(E))^T)\\
&=  (Re(E)Re(W_r)Re(E)^T + Im(E)Re(W_r)Im(E)^T)   \\
&+ (Re(E)Im(W_r)Im(E)^T - Im(E)Im(W_r)Re(E)^T)       \\
\end{align*}
$$
$X_r$ is indeed symmetric when $W_r$ is purely real, and antisymmetric when $W_r$ is purely imaginary. 

(The matrix $(Re(E)Re(W_r)Re(E)^T + Im(E)Re(W_r)Im(E)^T)$ is symmetric, and the matrix   $(Re(E)Im(W_r)Im(E)^T - Im(E)Im(W_r)Re(E)^T)$ is antisymmetric.)

Relation embeddings naturally act as weights on each latent dimension: $Re(W_r)$ over the symmetric, real part of $<e_o, e_s>$, and $Im(W_r)$ over the antisymmetric, imaginary part of $<e_o, e_s>$.

Hence this model is well suited to model jointly symmetric and antisymmetric relations between pairs of entities, while still using the same entity representations for subjects and objects.

...
$$
\begin{align*}
\phi (r,s,o; \Theta)
&=  Re(<w_r, e_s, \bar e_o>) \\
&=  Re(\sum^K_{k=1} w_{rk} e_{sk} \bar e_{ok}) \qquad \qquad \qquad (10)\\ 
&=  <Re(w_r), Re(e_s), Re(e_o)>  \\
 & + <Re(w_r), Im(e_s), Im(e_o)> \\
 & + <Im(w_r), Re(e_s), Im(e_o)> \\
 & - <Im(w_r), Im(e_s), Re(e_o)>  \qquad (11)
\end{align*}
$$
These equations provide two interesting views of the model:

- Changing the representation: Equation (10) would correspond to DistMult with real embeddings, but handles asymmetry thanks to the complex conjugate of one of the embeddings.

- Changing the scoring function: Equation (11) only involves **real vectors** corresponding to the real and imaginary parts of the embeddings and relations.

  也就是说不把$i$考虑进来，只考虑复数的实数部分，即实部和虚部。

<u>Geometrically, each relation embedding $w_r$ is an anisotropic scaling of the basis defined by the entity embeddings $E$, followed by a projection onto the real subspace.</u> (???)

Note:

Equation (10) used the standard componentwise multi-linear dot product $< a, b, c >:= \sum_k a_k b_k c_k$. This is not the Hermitian extension as it is not properly defined in the linear algebra literature. ​




score function:

$f_r(h,t)= \rm Re(\bold h^{\top} \rm diag (\bold r) \bold {\bar t}) = Re(\sum^{d-1}_{i=0} [\bold r]_i \cdot [\bold h]_i \cdot [\bold {\bar t}]_i)$ 

where

$\bold h, \bold r, \bold t \in \mathbb{C}^d$

ie. $\bold h=\rm Re(\bold h)+i \rm Im(\bold h)$ with $\rm Re(\bold h) \in \mathbb{R}^d$ and $\rm Im(\bold h) \in \mathbb{R}^d$, $\bold h \in \mathbb{C}^d$.

$\bold {\bar t}$ is the conjugate of $\bold t$

$\rm Re(\cdot)$ means taking the real part of a complex value


$$
\min_{\Theta} \sum_{r(s,o) \in \Omega} \log(1+ exp(-Y_{rso} \phi(s,r,o; \Theta))) + \lambda ||\Theta||^2_2
$$


One can easily check that this function is antisymmetric when $w_r$ is purely imaginary (i.e. its real part is zero), and symmetric when $w_r$ is real. 

...



Advantage

ComplEx is able to infer both the symmetry and asymmetric patterns with complex embeddings. Moreover, it can infer inversion rules because the complex conjugate of the solution to $\rm arg max_r Re(<\bold x, \bold r, \bold {\bar y}>)$ is exactly the solution to $\rm arg max_r Re(<\bold y, \bold r, \bold {\bar x}>)$.(???)



symmetry: r(x,y) = r(y,x)

$Re(<\bold x,\bold r, \bold {\bar y}>) = Re(<\bold y,\bold r, \bold{\bar x}>)$, then $Im(\bold r) = 0$

$(Re(\bold x)Re(\bold r)Re(\bold y)^T + Im(\bold x)Re(\bold r)Im(\bold y)^T) + (Re(\bold x)Im(\bold r)Im(\bold y)^T - Im(\bold x)Im(\bold r)Re(\bold y)^T) $

=

$(Re(\bold y)Re(\bold r)Re(\bold x)^T + Im(\bold y)Re(\bold r)Im(\bold x)^T) + (Re(\bold y)Im(\bold r)Im(\bold x)^T - Im(\bold y)Im(\bold r)Re(\bold x)^T) $



asymmetric:  应该是antisymmetric！

$Re(<\bold x,\bold r, \bold {\bar y}>) \ne Re(<\bold y,\bold r, \bold{\bar x}>)$, then $Re(\bold r) = 0$

Subject and object entity embeddings for the same entity are complex conjugates, which introduces asymmetry into the tensor decomposition and thus enables ComplEx to model asymmetric relations.



inversion:r2(x,y) $\Rightarrow$ r1(y,x), relation r1 is inverse to relation r2

$Re(<\bold x,\bold r, \bold {\bar y}>) = Re(<\bold y,\bold r, \bold{\bar x}>)$ ??? 



Disadvantage

ComplEx cannot infer composition rules, since it does not model a bijection mapping (???) from h to t via relation r.

composition







Question

1. 如何理解低秩分解（Low-Rank Decomposition）？

2. 梯度下降方法可以保证学习的实体是a unitary matrix of eigenvectors与关系是the diagonal matrix of eigenvalues (with decreasing modulus)？

3. why model the symmetric need the $Im(\bold r) = 0$, the anti-symmetric need the $Re(\bold r) = 0$ ? what it's modeling when the $Im(\bold r) \ne 0$ and $Re(\bold r) \ne 0$ ?

4. 

   

Summary

1. 复空间转实空间 - 只取实部！

2. 复数的特征值分解方法对输入矩阵没有约束条件

   matrix factorization/singular value decomposition - $X \approx UV^{T}$,  $X \in \mathbb{R}^{n \times n}$

   It is assumed that entities appearing as subjects are different from entities appearing as objects. This means that the same entity will have two different embedding vectors, depending on whether it appears as the subject or the object of a relation.

   However, in many link prediction problems, the same entity can appear as both subject and
   object. It then seems natural to learn joint embeddings of the entities, which entails sharing the embeddings of the left and right factors.

   In order to use the same embedding for subjects and objects, researchers have generalized the notion of dot products to scoring functions, also known as composition functions, that combine embeddings in specific ways.

   

   实数的 Eigenvalue decomposition - $W$ 是对称矩阵，无法建模非对称关系！

   Using the same embeddings for right and left factors boils down to Eigenvalue decomposition:

   $X = EWE^{-1}$

   It is often used to approximate real **symmetric** matrices such as covariance matrices, kernel functions and distance or similarity matrices. In these cases all eigenvalues and eigenvectors live in the real space and $E$ is orthogonal: $E^{T}=E^{-1}$.

   

   复数的 Eigenvalue decomposition - $W$ 是对称矩阵，但是为复数向量，可以建模非对称关系！

   

3. 基本思想：利用复数的特征值分解方法，将关系矩阵分解为实体复向量和关系复向量之间的乘积。

   









###### ComplEx-N3 (cited 59) 2018

paper:

Lacroix, Timothée, Nicolas Usunier, and Guillaume Obozinski. "Canonical tensor decomposition for knowledge base completion." *arXiv preprint arXiv:1806.07297* (2018).



###### RotatE  (cited 89) 2019

Paper:

Z. Sun, Z.-H. Deng, J.-Y. Nie, and J. Tang, “RotatE: Knowledge graph embedding by relational rotation in complex space,” in ICLR, 2019, pp. 1–18. [review](<https://openreview.net/forum?id=HkgEQnRqYQ>)  有非常详细的论证！

Group Representation Theory for Knowledge Graph Embedding [paper](<https://grlearning.github.io/papers/15.pdf>). (群论角度解读RotatE).

PPT:

<https://jian-tang.com/files/RotatE/RotatE.pdf>





Motivation:

Euler’s identity (欧拉公式) $e^{i \theta} =\rm cos \theta + i\ sin\theta$, which indicates that a unitary complex number can be regarded as a rotation in the complex plane.

Specifically, the RotatE model maps the entities and relations to the complex vector space and defines each relation as a rotation from the source entity to the target entity



the RotatE model defines each relation as a rotation from the source entity to the target entity in the complex vector space



score function：

$f_r(h,t) =|| \bold h \circ  \bold r  - \bold t||$ 

where

$\bold h, \bold r, \bold t \in \mathbb{C}^d$

$\circ$ is the Hadamard (element-wise) product

Specifically, for each element in the embeddings, we have:

$t_i = h_i r_i$

where $h_i,r_i,t_i \in \mathbb{C}$ 



constraints:

$|r_i| = 1$

$r_i = e^{iθ_{r,i}}$

where $θ_{r,i}$ is the phase angle of $\bold r$ in the i-th dimension.

By doing this, $r_i$ is of the form $e^{iθ_{r,i}}$ , which corresponds to a counterclockwise rotation by $θ_{r,i}$ radians about the origin of the complex plane, and only affects the phases of the entity embeddings in the complex vector space.

Notes:

若$θ_{r,i} > 0$，即$h_i$逆时针旋转$θ_{r,i}$度，否则顺时针旋转$θ_{r,i}$度.



Connection with TransE:

RotatE can degenerate into TransE

As for the comparison with TransE, the rotation in the RotatE model is in the complex plane of each embedding vector element, as the same as TransE. This is different from the rotation is in the whole embedding space by matrix multiplication.



Advantage

symmetry:

if r(x,y) and r(y,x) hold, we have

$\bold x \circ \bold r= \bold y$ and $\bold y \circ \bold r= \bold x$, then $\bold r \circ \bold r = 1$

 $r_j = \pm1$ (i.e. $\theta_{r,j} = 0 \ \rm or \ \pi $) 



Different symmetric relations can be also represented with different embedding vectors.



antisymmetry:

if r(x,y) and ¬r(y,x) hold, we have

$\bold x \circ \bold r= \bold y$  and $\bold y \circ \bold r \neq \bold x$, then $\bold r \circ \bold r \neq 1$

 $r_j \neq \pm1$ 



inversion:

if $r_1(x,y)$ and $r_2(y,x)$ hold, we have

$\bold x \circ \bold r_1= \bold y$  and $\bold y \circ \bold r_2 = \bold x$, then $\bold r_1= \bold r_2^{-1}$ (i.e. $\theta_{1,j} = - \theta_{2,j}$)

(then $\bold r_1 \circ \bold r_2$ = 0 or $2\pi$)

$r_2=\bar r_1$ 共轭复数（举例理解？动物-下位->猫，动物<-上位-猫，可以用共轭复数表示这种翻转关系）



composition:

if $r_1(x,z)$, $r_2(x,y)$ and $r_3(y,z)$ hold, we have

$\bold x \circ \bold r_1= \bold z$  and $\bold x \circ \bold r_2 = \bold y$ and $\bold y \circ \bold r_3 = \bold z$, then $\bold r_1= \bold r_2 \circ \bold r_3$ (i.e. $\theta_1=\theta_2+\theta_3$)

(then $\bold r_1^{-1} \circ \bold r_2 \circ \bold r_3$ = 0 or $2\pi$)



The RotatE model can also somehow model the 1-to-N relations.

Why ?

Answer: Taking a 1-to-N relation r as an example. The triplets having the head entity x and relation r are denoted as: r(x, y1), r(x, y2) …. r(x, yn). When the optimization converges, it could be easily to find out that the embeddings of y1, y2, …, yn <u>will be evenly distributed on the surface of a hypercube (or a hypersphere in the case of L-2 norm) centered at rx</u>. In other words, ||rx - y1|| = ||rx - y2|| = .. = ||rx - yn||. ($\ell_2$范数，$||\bold x||_2$ ，可以看成一个球面，即度量$\bold x$到原点的距离。这里也可以将rx看作原点，即度量y1, y2, ..., yn到rx的距离) This phenomenon is the same as in semantic matching models, like ComplEx, where the scores <r,x,\bar{y1}>=<r,x,\bar{y2}>=..=<r,x,\bar{yn}>. Therefore, the RotatE model can somehow deal with 1-to-N relations just like ComplEx, as well as TransE.

这里论证了TransE、ComplEx和RotatE都能建模1-to-N类型的关系！！！也就是说加入正则约束，可以使之建模关系的某些性质或类型。

（例如:Regularizing Knowledge Graph Embeddings via Equivalence and Inversion Axioms）



TransX can infer and model the symmetry/antisymmetry pattern when $g_{r,1} = g_{r,2}$, e.g. in TransH (Wang et al., 2014), but cannot infer inversion and composition as $g_{r,1}$ and $g_{r,2}$ are **invertible matrix multiplications**;

TransX represents a wide range of TransE’s variants, such as TransH (Wang et al., 2014), TransR (Lin et al., 2015b), and STransE (Nguyen et al., 2016). The score function is $||g_{r,1}(\bold h)+\bold r-g_{r,2}(\bold t)||$, where $g_{r,i}(·)$ denotes a matrix multiplication with respect to relation $r$. 





Disadvantage

+ The relations are generally non-commutative

  You father’s wife does not equal to your wife’s father

  $\bold r_1 \circ \bold r_2≠ \bold r_2 \circ \bold r_1$

  Solution: rotation in four-dimensional space through Quaternion



Question

1. 学习到r的参数是什么？

   the embedding phases

2. 



###### QuatE  (cited 15) 2019

Paper:

S. Zhang, Y. Tay, L. Yao, and Q. Liu, “Quaternion knowledge graph embedding,” in NeurIPS, 2019, pp. 2731–2741.





Summary

Symmetry

Antisymmetry 

Inversion

Composition - In QuatE, the composition patterns are not fixed.



#### neural network



##### NTN (cited 1186) 2013

Paper:

R. Socher, D. Chen, C. D. Manning, and A. Ng, “Reasoning with
neural tensor networks for knowledge base completion,” in NIPS,
2013, pp. 926–934.

##### MLP (cited 1142) 2014

X. Dong, E. Gabrilovich, G. Heitz, W. Horn, N. Lao, K. Murphy,
T. Strohmann, S. Sun, and W. Zhang, “Knowledge vault: A webscale
approach to probabilistic knowledge fusion,” in SIGKDD.
ACM, 2014, pp. 601–610.

##### NAM (cited 37) 2016

Q. Liu, H. Jiang, A. Evdokimov, Z.-H. Ling, X. Zhu, S. Wei,
and Y. Hu, “Probabilistic reasoning via deep learning: Neural
association models,” arXiv preprint arXiv:1603.07704, 2016.



##### ConvE (cited 295) 2018

Paper:

T. Dettmers, P. Minervini, P. Stenetorp, and S. Riedel, “Convolutional
2d knowledge graph embeddings,” in AAAI, vol. 32, 2018,
pp. 1811–1818.



1-N scoring: - 提高了训练及评估速度，也提高了性能。

Unlike other link prediction models which take an entity pair and a relation as a triple (s, r, o), and score it (1-1 scoring), we take one (s, r) pair and score it against all entities $o ∈ E$ simultaneously (1-N scoring).

Thus 1-N scoring has an additional effect which is akin to batch normalisation (Ioffe and Szegedy 2015) – we trade some computational performance for greatly increased convergence speed and also achieve better performance 



##### ConvKB (cited 90) 2018

D. Q. Nguyen, T. D. Nguyen, D. Q. Nguyen, and D. Phung, “A
novel embedding model for knowledge base completion based
on convolutional neural network,” in NAACL, 2018, pp. 327–333.



##### R-GCN (cited 490) 2018

Paper:

M. Schlichtkrull, T. N. Kipf, P. Bloem, R. Van Den Berg, I. Titov, and
M. Welling, “Modeling relational data with graph convolutional
networks,” in ESWC, 2018, pp. 593–607.



Motivation: Capture the structural information in knowledge graphs by utilizing node structure, node attributes, and relation types.





##### summary

SME，参数较少，但计算量大，特别是使用三维张量的情况下，很难运用到大规模知识图谱。



NTN，目前表达能力最强的模型，适合学习稠密的知识图谱，缺点是参数太多，计算量大，不适合稀疏知识图谱。











