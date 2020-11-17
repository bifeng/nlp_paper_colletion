### Question

+ how to learning by matching the blanks (MTB) with three losses ?



### Contribution

+ we build on extensions of Harris’ distributional hypothesis to relations, as well as recent advances in learning text representations (specifically, BERT), to build <u>task agnostic relation representations</u> solely from entity-linked text.

  基于关系学习的框架，将一个有标签的监督任务转换为一个无标签的监督任务，从而充分利用大量的无监督数据，获得任务无关的关系表示。(translate the supervised learning to unsupervised label representation learning)



### Task definition

In this paper, we focus on learning mappings from relation statements to relation representations.

A relation statement is a triple $r = (x, s_1, s_2)$, where the indices in $s_1$ and $s_2$ delimit entity mentions in $x$.

Our goal is to learn a function $h_r = f_{\theta}(r)$ that maps the relation statement to a fixed-length vector $h_r \in R^d$ that represents the relation expressed in $x$ between the entities marked by $s_1$ and $s_2$.



### Architectures for Relation Learning

#### Relation Representations from Deep Transformers Model

(1) how do we represent entities of interest in the input to BERT, and (2) how do we extract a fixed length
representation of a relation from BERT’s output.

![relation_representation](https://github.com/bifeng/daily_book_notes/raw/master/resource/variants_architecture_relation_representation_from_bert.png)



Unlike previous work that have benefited from positional embeddings, the deep Transformers benefits the most from seeing the new entity boundary word pieces (ENTITY MARKERS).



### Application

#### Matching the Blanks (Unsupervised Pretraining Relation Representation)

基于关系学习的框架，将一个有标签的监督任务转换为一个无标签的监督任务，从而充分利用大量的无监督数据，获得任务无关的关系表示。

##### Hypothesis

the same entity share the same semantic relation, then we doesn't need to know the true relation labels.

##### Task definition

We aim to learn a relation statement encoder $f_\theta$ that we can use to determine whether or not two relation statements encode the same relation.

##### Training data

1. Since this linking system does not have any notion of relations, it is not reasonable to assume that $f_\theta$ will somehow magically build meaningful relation representations. To avoid simply relearning the entity linking system, we introduce a modified corpus

   $\widetilde{\cal{D}} = [(\tilde{r}^0, e^0_1, e^0_2) \cdots (\tilde{r}^N, e^N_1, e^N_2)]$

   where each $\tilde{r}^i = (\tilde{x}^i, s^i_1, s^i_2)$ contains a relation statement in which one or both entity mentions may have been replaced by a special [BLANK] symbol.

2. To prevent a large bias towards relation statements that involve popular entities, we limit the number of relation statements that contain the same entity by randomly sampling a constant number of relation statements that contain any given entity.

3. In practice, it is not possible to compare every pair of relation statements,  so we use a noise-contrastive estimation:

   Positive pairs of relation statements that contain the same entity, Negative pairs of relation statements that are either randomly sampled uniformly from the set of all relation statement pairs, or are sampled from the set of relation statements that share just a single entity (‘hard’ negatives).

`[CLS]` determine whether or not two relation statements encode the same relation ?



##### Loss

To train a model with matching the blank task, we construct a training setup similar to BERT, where two losses are used concurrently: the masked language model loss and the matching the blanks loss.







