more:

<http://www.cs.columbia.edu/~mcollins/courses/6998-2011/lectures/yarowsky.pdf>

<http://www.cs.columbia.edu/~mcollins/courses/6998-2011/lectures/cotrain.pdf>

<http://www.cs.columbia.edu/~mcollins/courses/6998-2012/lectures/cotrain.pdf>



[IEpaper_presentation](http://www.cs.cmu.edu/~yimengz/papers/IEpaper_presentation.ppt)

<https://en.wikipedia.org/wiki/Co-training>

<https://github.com/jjrob13/sklearn_cotraining>

https://github.com/aritter/twitter_nlp/blob/master/hbc/python/DL-Cotrain.py



### Application

+ NLP&CC 2013 跨语言情感分类 [site](<http://tcci.ccf.org.cn/conference/2013/pages/page04_eva.html>) 

  https://github.com/Jianbo-Gao/CoTrain

  <https://github.com/kegumingxin422/coTraining>

  



### Question

+ How to understand the "Justification for the Separation of Contextual and Spelling Features" ?

+ Why "minimize the number of examples for which $f_1(x_1,i) \neq f_2(x_2,i)$ " ？

  For some examples, if there are two features (the spelling or context features),  either the spelling or context alone should be sufficient to determine the types, so it's important to minimize the discrepancy of this two features !



### Papers

+ D. Yarowsky. 1995. Unsupervised Word Sense Disambiguation Rivaling Supervised Methods.In Proceedings of the 33rd Annual Meeting of the Association for Computational Linguistics. Cambridge, MA, pp. 189-196. 

  The decision list method

  <div align="center">
  <img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/decision_list_method.png" width="600" height="400" alt="decision_list_method"></img>
  </div>

  
+ A. Blum and T. Mitchell. 1998. Combining Labeled and Unlabeled Data with Co-Training. In Proceedings of the 11 th Annual Conference on Computational Learning Theory (COLT-98). [paper](<http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.125.6074&rep=rep1&type=pdf>) 

  co-training
  
  基本思想: 两个非常自信的人之间交流, 他们的背景差异越大, 获得的提升越大
  
  
  
  



### Contribution

Making use of the redundancy in the unlabeled data: for many named-entity instances both the **spelling** of the name and the **context** in which it appears are sufficient to determine its type. 

Theoretical analysis of the Separation of Contextual and Spelling Features !



### Methods

Use just 7 simple "seed" rules (spelling and contextual rules) to classify the named entity types.

A spelling rule might be a simple look-up for the string (e.g., a rule that Honduras is a location) or a rule that looks at words within a string (e.g., a rule that any string containing Mr. is a person).

A contextual rule considers words surrounding the string in the sentence in which it appears (e.g., a rule that any proper name modified by an appositive whose head is president is a person).



#### Yarowsky 95

Features used in the model:

+ Word found in +/- k word window
+ Word immediately to the right (+1 W)
+ Word immediately to the left (-1 W)
+ Pair of words at offsets -2 and -1
+ Pair of words at offsets -1 and +1
+ Pair of words at offsets +1 and +2
+ Also maps words to parts of speech, and general classes (e.g., WEEKDAY, MONTH etc.)
+ Local features including word classes are added:
  – Pair of tags at offsets -2 and -1
  – Tag at position -2, word at position -1
  – etc.



The property of a large amount of unlabeled data:

A Key Property: Redundancy, There are often many features which indicate the sense of the word

Another Useful Property: “One Sense per Discourse”, Yarowsky observes that if the same word appears more than once in a document, then it is very likely to have the same sense every time.



A Partially Supervised Method

(an approach that uses a small amount of labeled data, and a large amount of unlabeled data)

Step 1 of the Method: Collecting Seed Examples

Step 2 Training New Rules

1. From the seed data, learn a decision list of all rules with weight
   above some threshold (e.g., all rules with weight )
2. Using the new rules, relabel the data
   (usually we will now end up with more data being labeled)
3. Induce a new set of rules with weight above the threshold from
   the labeled data
4. If some examples are still not labeled, return to step 2



#### Cotrain

We assume each example $x_i$ splits into two views, $x_{1i}$ (Spelling Features) and $x_{2i}$ (Contextual Features).

Two Assumptions Behind Cotraining:

Assumption 1: Either view is sufficient for learning

Redundancy - Either **Spelling** or **Context** alone is often sufficient to determine an entity’s type

There are functions $F_1$ and $F_2$ such that $F(x)=F_1(x_1)=F_2(x_2)=y$ for all $(x,y)$ pairs.

Assumption 2: Some notion of independence between the two views

The Conditional-independence-given-label assumption: If $D(x_1,x_2,y)$ is the distribution over examples, then $D(x_1,x_2,y) = D_0(y)D_1(x_1|y)D_2(x_2|y)$ for some distributions $D_0$, $D_1$ and $D_2$.



Why are these Assumptions Useful ?

Two examples/scenarios:

+ Rote learning vs A graph interpretation

  Rote learning (死记硬背) - In a rote learner, functions $F_1$ and $F_2$ are look-up tables, no chance to learn generalizations such as “any name containing Mr. is a person”.

  

  Graph interpretation - 

  Each node in the graph is a spelling or context

  Each $(x_{1i}, x_{2i})$ pair is an edge in the graph

  An edge between two nodes mean they have the same label (relies on assumption 1: each view is sufficient for classification)

  As quantity of unlabeled data increases, graph becomes more connected (relies on assumption 2: some independence between the two views)

+ Constraints on hypothesis spaces

  (Basic idea: we don’t know the label for an unlabeled example, but we do know that the two functions must agree on it)



Objective Functions 
$$
\begin{align}
L(W^1, W^2) 
&=  \sum^n_{i=1} \sum_{y \neq y_i} e^{\Phi^1(x_{1i},y) \cdot W^1 - \Phi^1(x_{1i},y_i) \cdot W^1}\\
&+ \sum^n_{i=1} \sum_{y \neq y_i} e^{\Phi^2(x_{2i},y) \cdot W^2 - \Phi^2(x_{2i},y_i) \cdot W^2} \\
&+ \sum^{n+m}_{i=n+1} \sum_{y \neq z_{2i}} e^{\Phi^1(x_{1i},y) \cdot W^1 - \Phi^1(x_{1i},z_{2i}) \cdot W^1}\\
&+ \sum^{n+m}_{i=n+1} \sum_{y \neq z_{1i}} e^{\Phi^2(x_{2i},y) \cdot W^2 - \Phi^2(x_{2i},z_{1i}) \cdot W^2}\\
\end{align}
$$
question: what's the motivation of this objective function ? a ranking loss ? a boosting approach ?

Greedily minimize
$$
L(W) = \sum_i \sum_{y \neq y_i} e^{-m(y_i,y,W)}
$$


where $m(y_i,y,W) = \Phi(x_i,y_i) \cdot W - \Phi(x_i,y) \cdot W$.



Optimization Method

Need to minimize $L(W^1,W^2)$, do this by greedily minimizing w.r.t. first $W^1$, then $W^2$.





Algorithm boils down to:
1. Start with labeled data alone
2. Induce a contextual feature for each class (person/location/organization) from the current set of labelled data
3. Label unlabeled examples using contextual rules
4. Induce a spelling feature for each class (person/location/organization) from the current set of labelled data
5. Label unlabeled examples using spelling rules
6. Return to step 2



Cotraining suggests training two classifiers that “agree” as much as possible on unlabeled examples.







#### DL-CoTrain

–DL-CoTrain, based on Decision List Learning

The first method builds on results from (Yarowsky 95) and (Blum and Mitchell 98). 



The input is an initial, "seed" set of rules. 

The following algorithm was then used to induce new rules: 

...

Use the labeled examples to induce a decision list of spelling/contextual rules, using the Yarowsky 95 method.

...





##### DL-CoTrain vs. Yarowsky 95

+ cautiously add rules

  imposing a gradually increasing limit on the number of rules that can be added at each iteration.

  Taking only the highest frequency rules is much "safer", as they tend to be very accurate. This **intuition** is born out by the experimental results. 

+ separated the rules 

  separated the spelling and contextual features, alternating be-tween labeling and learning with the two types of features. 

  Thus an explicit **assumption** about the redundancy of the features -- that either the spelling or context alone should be sufficient to build a classifier -- has been built into the algorithm.





#### CoBoost

–CoBoost, based on AdaBoost algorithm

The second algorithm builds on a boosting algorithm called AdaBoost (Freund and Schapire 97; Schapire and Singer 98). 



CoBoost algorithm builds two additive models in parallel, with an objective function that bounds the rate of agreement.















