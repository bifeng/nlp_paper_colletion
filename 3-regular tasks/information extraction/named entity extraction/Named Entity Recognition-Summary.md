refer:

Chinese NER Using CRFs and Logic for the Fourth SIGHAN Bakeoff, [paper](https://www.aclweb.org/anthology/I08-4016)

Entity Extraction, Linking, Classification, and Tagging for Social Media: A Wikipedia-Based Approach, [paper](http://pages.cs.wisc.edu/~anhai/papers/doctagger-vldb13.pdf)



### Architectures

Commercial approaches to NER are often based on pragmatic combinations of lists and rules, with some smaller amount of supervised machine learning (Chiticariu et al., 2013).

One common approach is to make repeated rule-based passes over a text, allowing the results of one pass to influence the next. **The stages** typically first involve the use of rules that have extremely high precision but low recall. **Subsequent stages** employ more error-prone statistical methods that take the output of the first pass into account.
1. First, use high-precision rules to tag unambiguous entity mentions.
2. Then, search for substring matches of the previously detected names.
3. Consult application-specific name lists to identify likely name entity mentions from the given domain.
4. Finally, apply probabilistic sequence labeling techniques that make use of the tags from previous stages as additional features.

The intuition behind this staged approach is twofold. First, some of the entity mentions in a text will be more clearly indicative of a given entity’s class than others. Second, once an unambiguous entity mention is introduced into a text, it is likely that subsequent shortened versions will refer to the same entity (and thus the same type of entity).

refer: Speech and Language Processing - ed3book

### Method



#### rule and dictionary based

Markov Logic Networks (Error Correction Model)

##### domain knowledge

**1) spelling rules**

**2) context rules**

Example:

人名姓氏用字相对集中

地名前面通常有“去”“在”等词语，并以“县”“街”“开发区”等词结尾

机构名通常以“部”“公司”等词结尾

Example:

- If a chunk (a series of continuous characters) occurs in the training data as a PER or a LOC or an ORG, then this chunk should be a PER or a LOC or an ORG in the testing data. In general, a unique string is defined as a PER, it cannot be a LOC somewhere else.
- If a tagged entity ends with a location salient word, it is a LOC. If a tagged entity ends with an organization salient word, it is an ORG.
- If a tagged entity is close to a subsequent location salient word, probably they should be combined together as a LOC. The closer they are, the more likely that they should be combined.
- If a series of consecutive tagged entities are close to a subsequent organization salient word, they should probably be combined together as an ORG because an ORG may contain multiple PERs, LOCs and ORGs.
- Similarly, if there exists a series of consecutive tagged entities and the last one is tagged as an ORG, it is likely that all of them should be combined as an ORG.
- Entity length restriction: all kinds of tagged entities cannot exceed 25 Chinese characters.
- Stopword restriction: intuitively, all tagged entities cannot comprise any stopword.
- Punctuation restriction: in general, all tagged entities cannot span any punctuation.
- Since all NEs are proper nouns, the tagged entities should end with noun words.
- For a chunk with low conditional probabilities, all the above assumptions are adopted.

------

- Overlapping mentions: For example, a rule may drop a mention if it is subsumed by another mention (e.g., mention (Politics, $n_2$) is subsumed by (Politics of Love, $n_3$)).
  
- Blacklists of strings and IDs: drop a mention if it is a blacklisted string (e.g., stop words, profanities, slangs, etc.; about 127K strings have been blacklisted), or if the mention refers to a blacklisted node in the KB (about 0.5M nodes have been blacklisted).

- Prefix/suffix: drop a mention if it contains certain characters or words as prefixes or suffixes, or if the node name begins with a stop word (e.g., “a”, “an”, “the”).
  
- Size/number: drop a mention if it is a one-letter word (e.g., “a”, “b”) or a number.
  
- Straddling sentence boundaries: drop a mention if it straddles sentence boundaries, such as mention “Indian Cricket teams” from tweet “He’s an Indian. Cricket teams are popular in India.”
  
- Part of a noun: if a mention is one word and the word before or after this mention is a noun phrase, then this mention is likely to be part of that noun phrase. Hence, drop this mention.



#### machine learning based

Conditional Random Fields (Base Model)



#### deep learning based

##### decoding

###### a MLP + softmax layer


a multi-class classification problem.

Tag for each word is independently.

###### a CRF layers

a random field globally conditioned on the observation sequence

CRFs, however, cannot make full use of <u>segment-level</u> (???) information because the inner properties of segments cannot be fully encoded with word-level representations.





###### a LSTM layer



###### a pointer networks :star::star::star:

Pointer networks apply RNNs to learn the conditional probability of an output sequence with elements that are discrete tokens corresponding to the positions in an input sequence. It represents variable length dictionaries by using a softmax probability distribution as a “pointer”.



#### Combined

1. 字符级别的 Bi-LSTM + CRF

   1）分词+实体

   每个字处于词的不同位置作为序列中的一种状态（常见的位置状态有：B（词的开头）、E（词的结尾）、M（词的中间）、S（单个字组成的词）），每种实体类型也是一种状态（常见的实体类型有：人名（PER），机构名（ORG），其他词性（NO）），则实体词的类型联合字在词中的位置，构成了4*3=12种序列状态。

   2）分词+词性

   ...

   3）分词+词性+实体

   ...

   优缺点：

   字符级别，可以避免OOV问题。

   缺点在于它无法利用词性等信息，而这些信息有利于实体的识别。

   

2. 实体词典+规则

   规则主要包括：书名号中的电影名、带分隔符的外国人名等特殊格式。





#### Boosting

利用回标的方法自动标注

利用Boosting的方法减少噪音



- a. 使用已有的开源NER对文章粒度的长文本进行预处理，提取各类实体词，<u>人工结合文章语境，对实体词进行添加和删除</u>。将所标注的实体词放回文章，生成新的训练集进入到NER算法模型，这样可以达到比大部分开源NER更好的效果。

- b. 使用类似boosting的数据采样方案，基于a中标注数据分组产生多个NER模型，对段落粒度的文本进行扫描。如果标注结果不一致，则认为该样本存在较低的置信度，把该段文本投入到逐字逐句的标注流程，进一步提升数据集的准确率。

  



