### Question

+ Why it needs pre-training ?

+ How to discriminate the entities in one sentence (避免实体混乱) ?

+ Why need annotate 'O_B'/'O_I' for the entities that are not associated with the predicted relation type ?

  在当前关系下，降低无关实体的影响

### Architecture

a semi-Markov decision process: 1) a high-level RL process that detects a relation indicator in a sentence; 2) a low-level RL process that identifies the associated entities for the corresponding relation.

image???

