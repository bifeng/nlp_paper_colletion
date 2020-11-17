Entity linking is also called Named Entity Disambiguation (NED) in the NLP community.

## challenge

name variations and entity ambiguity. 

A named entity may have multiple surface forms, such as its full name, partial names, **aliases**, **abbreviations**, and alternate spellings.

On the other hand, an entity mention could possibly denote different named entities.

## related tasks

entity coreference resolution

word sense disambiguation

record linkage

## architecture 

Generally speaking, a typical entity linking system consists of the following three modules:

+ Candidate Entity Generation

+ Candidate Entity Ranking

+ Unlinkable Mention Prediction

  

### Candidate Entity Generation

Approaches to candidate entity generation are mainly based on string comparison between the surface form of the entity mention and the name of the entity existing in a knowledge base.

#### Name Dictionary Based Techniques

Name dictionary based techniques are the main approaches to candidate entity generation and are leveraged by many entity linking systems.

The dictionary D is constructed by leveraging features from Wikipedia as follows:

+ Entity pages

+ Redirect pages

  Redirect pages often indicate synonym terms, abbreviations, or other variations of the pointed entities.

+ Disambiguation pages

  These disambiguation pages are very useful in extracting abbreviations or other aliases of entities.

+ Bold phrases from the first paragraphs

  Varma et al. [63,64] observed that these bold phrases invariably are nick names, alias names or full names of the entity described in this article.

+ Hyperlinks in Wikipedia articles

  The anchor text of a link pointing to an entity page provides a very useful source of synonyms and other name variations of the pointed entity,

Using these features from Wikipedia described above, entity linking systems could construct a dictionary D. Besides leveraging the features from Wikipedia, there are some studies [80,81,82] that exploit query click logs and Web documents to find **entity synonyms**, which are also helpful for the name dictionary construction.



#### Surface Form Expansion From The Local Document

expansion the acronyms or part of their full names to the full name !

+ Heuristic Based Methods



+ Supervised Learning Methods



#### Methods Based on Search Engines



### Candidate Entity Ranking

We can broadly divide these candidate entity ranking methods into two categories:

+ Supervised ranking methods. These approaches rely on annotated training data to “learn” how to rank the candidate entities in Em. These approaches include binary classification methods, learning to rank methods, probabilistic methods, and graph based approaches.
+ Unsupervised ranking methods. These approaches are based on unlabeled corpus and do not require any manually annotated corpus to train the model. These approaches include Vector Space Model (VSM) based methods and information retrieval based methods.

In addition, we could also categorize the candidate entity ranking methods into another three categories:

+ **Independent ranking methods**. These approaches consider that entity mentions which need to be linked in a document are independent, and <u>do not leverage the relations between the entity mentions in one document</u> to
  help candidate entity ranking. In order to rank the candidate entities, they <u>mainly leverage the context similarity</u> between the text around the entity mention and the document associated with the candidate entity.

  单文本-语境相似

+ **Collective ranking methods**. These methods assume that <u>a document largely refers to coherent entities from one or a few related topics, and entity assignments for entity mentions in one document are interdependent with each other</u>. Thus, in these methods, entity mentions in one document are collectively linked by exploiting this “topical coherence”.

  单文本-主题相关

+ **Collaborative ranking methods**. For an entity mention that needs to be linked, these approaches identify other entity mentions having similar surface forms and similar textual contexts in the other documents. They <u>leverage this cross-document extended context information obtained from the other similar entity mentions and the context information of the entity mention itself to rank candidate entities for the entity mention</u>.

  跨文本-实体相似（别称(alias)）、语境相似等

#### Features

##### context-independent features

+ Name String Comparison

+ **Entity Popularity**

+ **Entity Type**

##### context-dependent features

+ Textual Context

  Bag of words

  Concept vector

Based on these different formulations of representations, each text around the entity mention or associated
with the candidate entity could be converted to a vector.

To calculate the similarity between vectors, different methods have been utilized, including dot-product, cosine similarity, Dice coefficient, word overlap, KL divergence, n-gram based measure, and Jaccard similarity.

+ Coherence Between Mapping Entities

  

##### Summary

when designing features for entity linking systems, the decision needs to be made regarding many aspects, such as the tradeoff between accuracy and efficiency, and the characteristics of the applied data set.



#### Supervised Ranking Methods

##### Binary Classification Methods

For one entity mention, if there are two or more candidate entities that are labeled positive, some techniques are employed to select the most likely one, such as confidence based methods [63,69,104], VSM based methods [65],
and SVM ranking models [66].

For the binary classifier, most systems employ Support Vector Machines (SVM) .

The drawbacks of binary classification approach:<br>Firstly, the training data is very unbalanced since the vast majority of candidate entities are negative examples.
Moreover, when multiple candidate entities for an entity mention are classified as positive by the binary classifier, they have to utilize other techniques to select the most likely one.

##### Learning to Rank Methods

The advantages of learning to rank methods:<br>First,  training data is balanced since we have a single ranking example for each entity mention (take into account relations between candidate entities for the same entity mention). <br>Secondly, methods just need to select the candidate entity which achieves the highest score in the test phase as the
mapping entity for each entity mention, rather than resorting to other techniques to select the most likely one.

Most entity linking systems that leverage the learning to rank framework utilize the ranking SVM framework to learn the ranking model.



##### Probabilistic Methods



##### Graph Based Approaches



##### Model Combination



##### Training Data Generation

One problem with the supervised ranking methods is the requirement of many annotated training examples to train the classifier.

Method: Zhang et al. leveraged the unambiguous entity mention (i.e., the entity mention associated with only one entity in the knowledge base) in the document collection, and replaced it with its ambiguous name variations to create more training data. (<u>Leverage the cross of unambiguous entity mention name and ambiguous name variations</u>)

However, the distribution of the automatically generated annotation data is not consistent with the real entity linking data set.

Zhang et al. used an instance selection strategy (similar to active learning) to select a more balanced and informative subset from the generated instances.

W. Zhang, J. Su, C. L. Tan, and W. T. Wang, “Entity linking leveraging automatically generated annotation,” in COLING,
2010.<br>W. Zhang, Y. C. Sim, J. Su, and C. L. Tan, “Entity linking with effective acronym expansion, instance selection and topic
modeling,” in IJCAI, 2011, pp. 1909–1914.

#### Unsupervised Ranking Methods

##### VSM Based Methods

##### Information Retrieval Based Methods



### Unlinkable Mention Prediction



两类unlinkable实体: 

1. 不能在knowledge base找到

   通过命名实体的规则或多个命名实体识别的集成，对实体进行过滤。

2. 能在knowledge base找到，但不是指称该实体

   方式一：利用候选实体排序的阈值过滤，该阈值也是排序模型可以学习的参数。

   方式二：训练一个二分类unlinkable mention prediction模型，特征也与候选实体排序模型的特征一样，也可以增加一些额外的特征（如排序的分数）。

   方式三：To predict the unlinkable mention, they added a NIL entity into the candidate entity set, and considered NIL as a distinct candidate. If the ranker outputs NIL as the top-ranked entity, this entity mention is considered as unlinkable. Otherwise, the top-ranked entity is returned as the correct mapping entity.（incorporated the unlinkable mention prediction process into the entity ranking process）。

   



## Directions and Conclusions

the entity linking task is highly data dependent and it is unlikely a technique dominates all others across all data sets. For a given entity linking task, it is difficult to determine which techniques are best suited. There are many aspects that affect the design of the entity linking system, such as the system requirement and the characteristics of the data sets.

In the following, we point out some promising research directions in entity linking.

Firstly, entities linking in diverse types of data. such as Web tables (Web tables are semi-structured text and have almost no textual context) [119] , Web lists [92], and **tweets** (tweets are very short and noisy) [22,56,79,96,146].

Secondly, for real-time and large-scale applications, efficiency and scalability are significantly important and essential.

Thirdly, the increasing demand for constructing and populating domain-specific knowledge bases (e.g., in the domains of biomedicine, entertainment, products, finance, tourism, etc.) makes domain-specific entity linking important as well.





## Question

+ question about learning to rank

  there is no need worry about unbalance ?

  how does it the take into account relations between candidate entities ?

  what's the loss ?

+ how to construct the training data for multiple entity mention in one text ? (there are lots of candidate entity for each entity mention)

+ 

+ how to select useful information from context information (long entity description in a document) for ranking ?

+ 

+ how to incorporated the unlinkable mention prediction process into the entity ranking process ?

+ 







