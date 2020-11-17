A Survey on Knowledge Graphs: Representation, Acquisition and Applications
Shaoxiong Ji, Shirui Pan, Erik Cambria, Pekka Marttinen, Philip S. Yu



# Knowledge graph

​	A knowledge graph is a structured representation of facts, consisting of entities, relationships and semantic descriptions. Entities can be real-world objects and abstract concepts, relationships represent the relation between entities, and semantic descriptions of entities and their relationships contain **types** and **properties** with a well-defined meaning.



## Categorization of research on knowledge graphs



+ Knowledge Representation Learning

  1) representation space in which the relations and entities are represented;
  2) scoring function for measuring the plausibility of factual triples;
  3) encoding models for representing and learning relational interactions;
  4) auxiliary information to be incorporated into the embedding methods.

+ Knowledge Acquisition

  entity discovery and relation extraction - discover new knowledge (aka relations and entities) from text

  KGC - is for expanding existing knowledge graphs

+ Temporal Knowledge Graphs

+ Knowledge-aware Applications

  
  
  

## knowledge graph representation learning



### representation space





### scoring function





### encoding models





### auxiliary information

To facilitate more effective knowledge representation, multimodal embedding incorporates external information such as text descriptions, type constraints, relational paths, and visual information, with a knowledge graph itself.



## knowledge acquisition

### entity discovery

Summary:

+ entity recognition

+ entity typing

  Entity typing includes coarse and fine-grained types, while the latter one uses a tree-structured type category and is typically regarded as multi-class and multi-label classification.

+ entity disambiguation

  Entity disambiguation or entity linking is a unified task which links entity mentions to the corresponding entities in a knowledge graph.

  For example, Einstein won Noble Prize in Physics in 1921. The entity mention of “Einstein” should be linked to the entity of Albert Einstein.

+ entity alignment

  entity alignment (EA) aims to fuse knowledge among heterogeneous knowledge graphs.



### relation extraction



### knowledge completion

Knowledge graph completion completes missing links between existing entities or infers entities given entity and relation queries.



Summary:

+ embedding-based models

  Embedding-based KGC methods generally rely on triple representation learning to capture semantics, and do candidate ranking for completion.

  disadvantage:

  1. lack of interpretability
  2. failed to capture multi-step relation paths/complex reasoning 

+ rule-based reasoning

  **Interpretability** - 

  Hybrid methods with symbolics and embedding incorporate rule based reasoning, overcome the sparsity of knowledge graph to improve the quality of embedding, facilitate efficient rule injection, and induce interpretable rules.

  Example:
  Given relations sonOf, hasChild and gender, and entities X and Y , there is a rule in the reverse form of logic programming as:
  (Y, sonOf, X)  $\leftarrow$ (X, hasChild, Y) $\wedge$ (Y, gender, Male)  

  

+ relational path reasoning/RL-based path finding

  **Multi-step relation paths** - 

  With the observation of graphical nature of knowledge graphs, path search and neural path representation learning are studied, but they suffer from connectivity deficiency when traverses
  over large-scale graphs. 



+ meta relational learning

  The emerging direction of meta relational learning aims to learn fast adaptation over unseen
  relations in low-resource settings.

  

+ triple classification



## temporal knowledge graph

The temporal information is of great importance because the structured knowledge only holds within a specific period, and the evolution of facts follows a time sequence.



### Temporal Information Embedding

Temporal information is considered in temporal aware embedding by extending triples into temporal quadruple as $(h; r; t; \tau)$, where $\tau$ provides additional temporal information about when the fact held.



### Entity Dynamics

Real-world events change entities’ state, and consequently, affect the corresponding relations.



### Temporal Relational Dependency

There exists temporal dependencies in relational chains following the timeline, for example, $wasBornIn \rightarrow graduateFrom \rightarrow workAt \rightarrow diedIn$.



### Temporal Logical Reasoning

Logical rules are also studied for temporal reasoning.



## knowledge-aware applications

Some real-world products, for example, Microsoft’s Satori and Google’s Knowledge Graph, have shown a strong capacity to provide more efficient services.



### Natural Language Understanding



### Question Answering



### Recommender Systems





