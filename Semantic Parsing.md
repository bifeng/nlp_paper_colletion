more refer:

acl2018-semantic-parsing-tutorial<br>https://github.com/allenai/acl2018-semantic-parsing-tutorial

NLP progress<br>https://github.com/sebastianruder/NLP-progress/blob/master/english/semantic_parsing.md



## Semantic Parsing

### CCG Semantic Parsing

+ Complex discrete learning algorithms

+ But, grammars hopefully generalize to unseen data well!

+ Difficult to engineer: few people can do it and it takes a lot of time

### Neural Semantic Parsing

+ Treat meaning as a string...
+ Apply NMT
+ Close to SOTA performance!!!
+ Much easier to build (with toolkits)

#### Constrained Decoding

##### Token-based Decoding
The output space is tokens, but they are constrained to be relevant at each time step.

###### paper

Dong and Lapata. 2016. Language to Logical Form with Neural Attention. In ACL.
Goldman, Latcinnik, Naveh, Globerson and Berant. 2018. Weakly-supervised Semantic Parsing with Abstract Examples. In ACL.

##### Grammar-based Decoding

The output space is production rules, and a grammar defines the constraints.

###### paper

Xiao, Dymetman, and Gardent. 2016. Sequence-based Structured Prediction for Semantic Parsing. In ACL.
Krishnamurthy, Dasigi, and Gardner. 2017. Neural Semantic Parsing with Type Constraints for Semi-Structured Tables. In EMNLP.

##### Coarse-to-Fine Decoding

###### paper

+ Coarse-to-Fine Decoding for Neural Semantic Parsing, Li Dong, Mirella Lapata, ACL 2018 [arxiv](https://arxiv.org/abs/1805.04793v1) | [code](https://github.com/donglixp/coarse2fine) 

