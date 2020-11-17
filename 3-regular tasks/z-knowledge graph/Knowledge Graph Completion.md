## Challenge

+ few shot relational learning/Meta Relational Learning

  The long-tail phenomena exist in the relations of knowledge graphs. Meanwhile, the real-world scenario of knowledge is dynamic, where unseen triples are usually acquired. The new scenario, called as meta relational learning or few-shot relational learning, requires models to predict new relational facts with only a very few samples.

+ 



 ## Embedding based

refer knowledge graph embedding



Drawbacks:

Most of them, however, failed to capture multi-step relationship, and can't provide interpretable explanations.



## Path based 

Relation path reasoning/finding turns to leverage path information over the graph structure.

### Rule-based 

symbol and logic + statistical relational learning: graphical models like Bayesian Networks or Markov Logic Networks (MLN)...

Drawbacks:

neither tractable nor robust when dealing with long range reasoning over a real large scale knowledge graph, and usually suffer from scalability issues.



### RL-based 

Deep reinforcement learning (RL) is introduced for multi-hop reasoning by formulating path-finding between entity pairs as sequential decision making, specifically a Markov decision process (MDP).



## Unified 

### PathCon 2020

Entity Context and Relational Paths for Knowledge Graph Completion. Hongwei Wang, Hongyu Ren, Jure Leskovec 2020.02 [arxiv](https://arxiv.org/abs/2002.06757) 



**Message-passing  or embedding propogation**



PathCon combines relational context and relational paths for KG completion. PathCon models **relations** rather than entities which makes the model explainable and generalizable to inductive settings.



1. relational context

   We design a multi-layer edge-based message passing scheme to aggregate messages from the k-hop neighborhood edges of a given entity.

   1）mean neighbor aggregator

   2）cross neighbor aggregator

2. relational paths

   We identify all paths from the head entity to the tail entity in the KG. Each path is represented by its relation types.

   1）attention-based path aggreggator

   2）mean path aggreggator

3. Attention

   adaptively integrating the Relational Context and Relational Path through a learnable attention mechanism. 











