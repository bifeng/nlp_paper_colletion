https://github.com/facebookresearch/StarSpace

<https://arxiv.org/pdf/1709.03856.pdf>



Importantly, the StarSpace model is free to compare entities of different kinds. For example, a user entity can be compared with an item entity (recommendation), or a document entity with label entities (text classification), and so on. This is done by learning to embed them in the same space such that comparisons are meaningful – by optimizing with respect to the metric of interest.

notes:

1. 这两类entity放到**同一个**embedding space上。对，真的是同一个，例如在document classification就算是少少的label也和多多的document同样映射到一个d-dimensional空间。这样label也有一个d-dimensional向量表示.


$$
\sum_{(a,b) \in E^{+} \\ b^- \in E^{-}} L^{batch} (sim(a,b),sim(a,b^{-}_{1}, \dots,sim(a,b^{-}_{k})))
$$
The dictionary of $\mathcal{D}$ features as $F$ which is a $\mathcal{D} \times d$ matrix, where $F_{i}$ indexes the $i^{th}$ feature (row), yielding its $d$-dimensional embedding, we embed an entity $a$ with $\sum_{i\in a} F_i$.

notes:

1. 一个实体a具有不同的feature，每个feature都有一个嵌入，所以构成实体a的嵌入就是这些特征的加和(或加权和)（和word2vec之后进行sentence embedding的策略是一样的）。

   





**Collaborative Filtering-based Recommendation** 

The training data consists of a set of users, where each user is described by a bag of items (described as unique features from the dictionary) that the user likes. The positive pair generator picks a user, selects a to be the unique singleton feature for that user ID, and a single item that they like as b. Negative entities b− are sampled from the set of possible items.

**Input file format:**

```
user_1 item_1
```

At training time, at each step for each example (user), one random item is selected as a label.





**Collaborative Filtering-based Recommendation with out-of-sample user extension** 

One problem with classical collaborative filtering is that it does not generalize to new users, as a separate embedding is learned for each user ID. Using the same training data as before, one can learn an alternative model using StarSpace. The positive pair generator instead picks a user, selects a as all the items they like except one, and b as the left out item. That is, the model learns to estimate if a user would like an item by modeling the user not as a single embedding based on their ID, but by **representing the user as the sum of embeddings of items they like**.

**Input file format:**

```
item_1 item_2 ... item_M
```

At training time, at each step for each example (user), one random item is selected as a label and the rest of bag of items are selected as input. 

Example:

https://github.com/facebookresearch/Starspace/blob/master/examples/user-page.png



**Content-based Recommendation** 

This task consists of a set of users, where each user is described by a bag of items, where each item is described by a bag of features from the dictionary (rather than being a unique feature). For example, for document recommendation, each user is described by the bag-of-documents they like, while each document is described by the bag-of-words it contains. Now a can be selected as all of the items except one, and b as the left out item. The system now extends to both new items and new users as both are featurized.

**Input file format:**

```
roger federer loses <tab> venus williams wins <tab> world series ended
i love cats <tab> funny lolcat links <tab> how to be a petsitter  
```

Each line is a user, and each document (documents separated by tabs) are documents that they liked. So the first user likes sports, and the second is interested in pets in this case.

At training time, at each step one random document is selected as the label and the rest of the bag of documents are selected as input.

Example:

https://github.com/facebookresearch/Starspace/blob/master/examples/user-doc.png









