### Question

+ Use different entity embeddings for one entity with different entity descriptions ?
+ Entity embeddings normalized before calculation the difference vector of the entity pairs ?
+ 

### Contribution

+ Use (e1-e2) to represent the relation label



### Motivation

Motivated by TransE (Bordes et al. 2013) which regarded relation as translation from head entity (e1) to tail entity (e2). They used e1 + r ≈ e2 to model the translation for triplet r(e1, e2).

1. we use (e1 − e2) to represent the relation between e1 and e2 in sentences.

2. we let the vectors of entities be close to this entity descriptions (constraint).









