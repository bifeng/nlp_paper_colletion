more refer:

[Anaphora](https://en.wikipedia.org/wiki/Anaphora_%28linguistics%29#Anaphor_resolution)

CS 4705: Introduction to Natural Language Processing, Fall 2009 - [Kathy McKeown](http://www.cs.columbia.edu/~kathy)

http://www1.cs.columbia.edu/~kathy/NLP/index.htm



refer:<br>[CS 4705 Pronouns and Reference Resolution](http://www.cs.columbia.edu/~kathy/NLP/ClassSlides/Slides09/Class19-Pronouns/myref.pdf)



### Types of Reference

Entities, concepts, places, propositions, events, ...



### Discourse Analysis

+ Discourse Model

  When a referent is first mentioned in a discourse, a representation is evoked in the
  model
  ◦ Information predicated of it is stored also in the model
  ◦ On subsequent mention, it is accessed from the model

+ Referents of pronouns usually require some degree of salience in the discourse (as opposed to definite and indefinite NPs, e.g.)
  How do items become salient in discourse?<br>Salience via Simple Recency<br>Salience via Structural Recency



### Constraints on Co-reference

Number agreement <br>Person and case agreement<br>Gender agreement <br>Syntactic constraints<br>Selectional restrictions



### Factors of Reference Resolution

+ Lexical factors
  ◦ Reference type: Inferrability, discontinuous set,
  generics, one anaphora, pronouns,…
+ Discourse factors:
  ◦ Recency
  ◦ Focus/topic structure, digression
  ◦ Repeated mention
+ Syntactic factors:
  ◦ Agreement: gender, number, person, case
  ◦ Parallel construction
  ◦ Grammatical role<br>◦ Selectional restrictions
+ Semantic/lexical factors
  ◦ Verb semantics, thematic role
+ Pragmatic factors

### Algorithms

Lappin & Leas ‘94: weighting via recency and syntactic preferences. [paper](http://www.aclweb.org/anthology/J/J94/J94-4002.pdf)


Weights candidate antecedents by recency and syntactic preference (86% accuracy)

Two major functions to perform:
◦ Update the discourse model when an NP that evokes a new entity is found in the text, computing the salience of this entity for future anaphora resolution
◦ Find most likely referent for current anaphor by considering possible antecedents and their salience values

Partial example for 3P, non-reflexives

+ Saliency Factor Weights

  Sentence recency (in current sentence?) 100<br>Subject emphasis (is it the subject?) 80<br>Existential emphasis (existential prednom?) 70<br>Accusative emphasis (is it the dir obj?) 50<br>Indirect object/oblique comp emphasis 40<br>Non-adverbial emphasis (not in PP,) 50<br>Head noun emphasis (is head noun) 80

Implicit ordering of arguments:
subj/exist pred/obj/indobjoblique/dem.advPP

Update:
◦ Weights accumulate over time
◦ Cut in half after each sentence processed
◦ Salience values for subsequent referents accumulate for equivalence class of coreferential items (exceptions, e.g. multiple references in same sentence)<br>◦ Additional salience weights for grammatical role
parallelism (35) and cataphora (-175) calculated
when pronoun to be resolved
◦ Additional constraints on gender/number
agrmt/syntax

+ Reference Resolution

  Collect potential referents (up to four sentences back): `{sofa,cat,bonbons}`
  Remove those that don’t agree in number/gender with pronoun `{bonbons}`
  Remove those that don’t pass intra-sentential syntactic coreference constraints
  `The cat washed it. (it≠cat)`
  Add applicable values for role parallelism (+35) or cataphora (-175) to current salience
  value for each potential antecedent
  Select referent with highest salience; if tie, select closest referent in string



#### Example

On the sofa, the cat was eating bonbons.
sofa: 100+80=180
cat: 100+80+50+80=310
bonbons: 100+50+50+80=280

The bonbons were clearly very tasty.
sofa: 180/2=90
cat: 310/2=155
bonbons: 280/2 +(100+80+50+80)=450

They were a gift from an unknown admirer.
sofa: 90/2=45
cat: 155/2=77.5
bonbons: 450/2=225 (+35) = 260….

---

Hobbs ‘78: syntax tree-based referential search



### Tools

[JavaRAP](http://wing.comp.nus.edu.sg/~qiu/NLPTools/JavaRAP.html) | [code](https://github.com/WING-NUS/JavaRAP)

[Stanford Deterministic Coreference Resolution System](https://nlp.stanford.edu/software/dcoref.shtml)

[ArkRef](http://www.ark.cs.cmu.edu/ARKref/) 

[SuperSense tagger](http://medialab.di.unipi.it/wiki/SuperSense_Tagger)

[Pronoun_Annotator](https://github.com/philgooch/Pronoun_Annotator)

https://www.minvolai.com/coreference-resolution-tools-a-first-look/ - 2010



