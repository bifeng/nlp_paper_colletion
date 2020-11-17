### Task

1. Link Prediction

2. Relation Prediction

3. Triple Classification

   

### Related Task

+ relational learning



### Theory

+ Group Representation Theory for Knowledge Graph Embedding [NeurIPS graph representation workshop]
  <https://grlearning.github.io/papers/15.pdf>
+ A Group-Theoretic Framework for Knowledge Graph Embedding [reject paper] [arxiv](<https://arxiv.org/abs/2005.10956>) 



### Literature Review

- Knowledge Graph Embedding: A Survey of Approaches and Applications, Quan Wang, Zhendong Mao, Bin Wang, and Li Guo. IEEE 2017 [pdf](<https://persagen.com/files/misc/Wang2017Knowledge.pdf>) 
- A survey of embedding models of entities and relationships for knowledge graph completion.
- Y. Lin, X. Han, R. Xie, Z. Liu, and M. Sun, “Knowledge representation learning: A quantitative review,” arXiv preprint arXiv:1812.10901, 2018.
- A Review of Relational Machine Learning for Knowledge Graphs. Maximilian Nickel, Kevin Murphy, Volker Tresp, Evgeniy Gabrilovich  2015.03  [arxiv](https://arxiv.org/abs/1503.00759) 



### Datasets

+ https://github.com/simonepri/datasets-knowledge-embedding
+ 

### Paper

+ Entity Context and Relational Paths for Knowledge Graph Completion. Hongwei Wang, Hongyu Ren, Jure Leskovec 2020 [arxiv](https://arxiv.org/abs/2002.06757) [code](https://github.com/hwwang55/PathCon) 

  

+ SEEK: Segmented Embedding of Knowledge Graphs. ACL 2020 [github](<https://github.com/Wentao-Xu/SEEK>) 



+ Comparative

+ Knowledge Graph Embedding for Link Prediction: A Comparative Analysis

  > 注意：该文比较了各个模型对不同关系性质的建模性能

+ Knowledge Base Completion: Baselines Strike Back
  Rudolf Kadlec, Ondrej Bajgar, Jan Kleindienst 2017



+ Evaluation

+ Wang Y, Ruffinelli D, Gemulla R, et al. On evaluating embedding models for knowledge base completion[J]. arXiv preprint arXiv:1810.07180, 2018.

+ A Re-evaluation of Knowledge Graph Completion Methods. Zhiqing Sun, Shikhar Vashishth, Soumya Sanyal, Partha Talukdar, Yiming Yang ACL 2020

  

  

+ Traning

+ You CAN Teach an Old Dog New Tricks! On Training Knowledge Graph Embeddings [review](<https://openreview.net/forum?id=BkxSmlBFvr>) 

+ Toward Understanding The Effect Of Loss function On Then Performance Of Knowledge Graph Embedding



+ Symbolic based

+ Reinforced Anytime Bottom Up Rule Learning for Knowledge Graph Completion





### Tools

- tensorflow
- <https://github.com/Accenture/AmpliGraph>
- <https://github.com/thunlp/OpenKE>
- 



+ pytorch
+ <https://github.com/uma-pi1/kge>
+ https://github.com/thunlp/OpenKE
+ <https://github.com/DeepGraphLearning/KnowledgeGraphEmbedding>



#### [PyTorch-BigGraph](https://github.com/facebookresearch/PyTorch-BigGraph)

#####  [Graph (data model)](<https://torchbiggraph.readthedocs.io/en/latest/data_model.html>)

Graph - Vertices are called **entities**.  Each **edge** connects a source to a destination entity, which are respectively called its **left-** and **right-hand side** (shortened to **LHS** and **RHS**).

PBG operates on directed multi-relation multigraphs. Multiple edges between the same pair of entities are allowed. Loops, i.e., edges whose left- and right- hand sides are the same, are allowed as well.

Each entity is of a certain **entity type**. Similarly, each edge also belongs to exactly one **relation type**. All edges of a given relation type must have all their left-hand side entities of the same entity type and, similarly, all their right-hand side entities of the same entity type (possibly a different entity type than the left-hand side one). This property means that each relation type has a left-hand side entity type and a right-hand side entity type.(如: 苏辙 - 父子关系 -> 苏轼, '父子关系'左/右手边的实体类型是人, 意味着关系类型对两边的实体类型起约束作用)

##### [Scoring](https://torchbiggraph.readthedocs.io/en/latest/scoring.html)

In the current implementation, they are only allowed to transform the embedding of one of the two sides, which is then compared to the un-transformed embedding of the other side using a generic symmetric comparator function, which is the same for all relations.

Formally, for left- and right-hand side entities $x$ and $y$ respectively, and for a relation type $r$, the score is:

$f_r(\theta_x, \theta_y) = c(\theta_x, g_r(\theta_y))$

where $\theta_x$ and $\theta_y$ are the embeddings of $x$ and $y$

$f_r$ is the scoring function for $r$

$g_r$ is the operator for $r$ and $c$ is the comparator.

Applying the operator to both sides would oftentimes be redundant. Also, preferring one side over the other allows to <u>break the symmetry and capture the direction of the edge</u>.

##### [Featurized entities](<https://torchbiggraph.readthedocs.io/en/latest/featurized_entities.html>)

In normal operation PBG considers each entity atomic and distinct from all others, and as such it learns an independent embedding for each of them, with no correlation other than the one acquired during training. However, it is common practice to represent some type of data as collections of underlying “features”, each of which has its own learned embedding. The embedding of an entity will be implicitly derived from the embeddings of its features. **Sharing a feature will enforce a correlation between the embeddings of two entities**.

##### [Loss calculation](<https://torchbiggraph.readthedocs.io/en/latest/loss_optimization.html>)





### Pre-trainedd Embedding

+ [PyTorch-BigGraph](<https://github.com/facebookresearch/PyTorch-BigGraph>)

  The model contains 78 million entities, 4,131 relations and the dimension of the embeddings is 200.

  [Wikidata](https://www.wikidata.org/):

  Data Prepare - We used as **entities** all the distinct strings that appeared as either source or target nodes in this dump: this means that entities include URLs of Wikidata entities (in the form `<http://www.wikidata.org/entity/Q*123*>`), plain quoted strings (e.g., `"*Foo*"`), strings with language annotation (e.g., `"*Bar*"@*fr*`), dates and times, and possibly more. Similarly, we used as **relation types** all the distinct strings that appeared as properties.

  We then filtered out entities and relation types that <u>appeared less than 5 times</u> in the data dump.

  ```
  # the source entities    the relation types         the target entities    
  /m/027rn	/location/country/form_of_government	/m/06cx9
  /m/017dcd	/tv/tv_program/regular_cast./tv/regular_tv_appearance/actor	/m/06v8s0
  /m/07s9rl0	/media_common/netflix_genre/titles	/m/0170z3
  /m/01sl1q	/award/award_winner/awards_won./award/award_honor/award_winner	/m/044mz_
  /m/0cnk2q	/soccer/football_team/current_roster./sports/sports_team_roster/position	/m/02nzb8
  ```

  [how to access wikidata](<https://www.wikidata.org/wiki/Wikidata:Data_access>) [some works about wikidata, such as visualization](<https://www.wikidata.org/wiki/Wikidata:Tools>)









