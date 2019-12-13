[100 Must-Read NLP Papers](https://github.com/mhagiwara/100-nlp-papers) 

It's nice to look at readings from a good NLP course:

<https://web.stanford.edu/class/cs224n/>

<http://www.cs.columbia.edu/~mcollins/cs4705-spring2019/>

...



| Short Name | Full Name                                                    | CCF Level |
| ---------- | ------------------------------------------------------------ | --------- |
| ICML       | International Conference on Machine Learning                 | A         |
| NeurIPS    | Annual Conference on Neural Information Processing Systems   | A         |
| AAAI       | AAAI Conference on Artificial Intelligence                   | A         |
| IJCAI      | International Joint Conference on Artificial Intelligence    | A         |
| ACL        | Annual Meeting of the Association for Computational Linguistics | A         |
| EMNLP      | Conference on Empirical Methods in Natural Language Processing | B         |
| COLING     | International Conference on Computational Linguistics        | B         |
|            |                                                              |           |
| KDD        | ACM Knowledge Discovery and Data Mining                      | A         |
| SIGIR      | International Conference on Research an Development in Information Retrieval | A         |
| WSDM       | ACM International Conference on Web Search and Data Mining   | B         |
| CIKM       | ACM International Conference on Information and Knowledge Management | B         |
|            |                                                              |           |



Test of time award is much valuable than best paper award !!!

SIGIR - <http://sigir.org/awards/test-of-time-awards/>

<https://www.aminer.cn/bestpaper> <https://jeffhuang.com/best_paper_awards.html> 





:star: - ablation analysis



## Language Modeling

- Joshua Goodman: A bit of progress in language modeling, MSR Technical Report, 2001.

  > describes just about everything related to n-gram language models

- Stanley F. Chen and Joshua Goodman: An Empirical Study of Smoothing Techniques for Language Modeling, ACL 2006.

- Yee Whye Teh: A Hierarchical Bayesian Language Model based on Pitman-Yor Processes, COLING/ACL 2006.

- Yee Whye Teh: A Bayesian interpretation of Interpolated Kneser-Ney, 2006.

  > shows how to get state-of-the art accuracy in a Bayesian framework, opening the path for other applications

  ---

- Yoshua Bengio, et al.: A Neural Probabilistic Language Model, J. of Machine Learning Research, 2003.

- Andrej Karpathy: The Unreasonable Effectiveness of Recurrent Neural Networks, 2015.

- Yoon Kim, et al.: Character-Aware Neural Language Models, 2015.



## Segmentation, Tagging, Parsing

* Donald Hindle and Mats Rooth. Structural Ambiguity and Lexical Relations, Computational Linguistics, 1993.

* Adwait Ratnaparkhi: A Maximum Entropy Model for Part-Of-Speech Tagging, EMNLP 1996.

* Michael Collins: Discriminative Training Methods for Hidden Markov Models: Theory and Experiments with Perceptron Algorithms, EMNLP 2002 [paper](http://www.cs.columbia.edu/~mcollins/papers/tagperc.pdf). **Test of time award at NAACL 2018** 

  > **Justification**: A key element of determining the “Test of Time” paper is: does this paper still influence work today? This paper laid the foundation for how a host of machine learning methods could be used across a range of NLP tasks. The idea behind the paper is simple and beautiful, as it applies the well known, and very old, Perceptron algorithm to structured prediction problems. This simple method achieved remarkably good results, opening the door to a range of complex NLP prediction tasks to use relatively simple ML methods with great results. This work led directly to a few different models that came to dominate a range of NLP tasks, such as information extraction and parsing. While the paper is a strong empirical contribution, it includes a theoretical analysis as well. As a result, this is among the most widely cited papers from the ACL community in the past two decades.

  

  > The paper re-introduced the classic Perceptron algorithm as a simple and powerful tool for structured prediction. The method and idea have been applied to many tasks.

* Dan Klein and Christopher Manning: Accurate Unlexicalized Parsing, ACL 2003.

  > shows that lexicalization is not necessary to achieve reasonably good parsing accuracy

* Dan Klein and Christopher Manning: Corpus-Based Induction of Syntactic Structure: Models of Dependency and Constituency, ACL 2004.

  > a revolution in unsupervised dependency parsing

* Joakim Nivre and Mario Scholz: Deterministic Dependency Parsing of English Text, COLING 2004.

  > shows that deterministic parsing actually works quite well

* Ryan McDonald et al.: Non-Projective Dependency Parsing using Spanning-Tree Algorithms, EMNLP 2005.

  > the other main method of dependency parsing, MST parsing

* Daniel Andor et al.: Globally Normalized Transition-Based Neural Networks, 2016.

* Oriol Vinyals, et al.: Grammar as a Foreign Language, 2015.

  

## Sequential Labeling & Information Extraction

- Marti A. Hearst: Automatic Acquisition of Hyponyms from Large Text Corpora, COLING 1992.

  > The very first paper for all the bootstrapping methods for NLP. It is a hypothetical work in a sense that it doesn't give experimental results, but it influenced it's followers a lot.

- David Yarowsky, Unsupervised word sense disambiguation rivaling supervised methods, ACL 1995.

- Collins and Singer: Unsupervised Models for Named Entity Classification, EMNLP 1999.

  > It applies several variants of co-training like IE methods to NER task and gives the motivation why they did so. Students can learn the logic from this work for writing a good research paper in NLP.

- Gildea and Jurafsky. Automatic Labeling of Semantic Roles. Computational Linguistics 2002

  > It opened up the trends in NLP for semantic role labeling, followed by several CoNLL shared tasks dedicated for SRL. It shows how linguistics and engineering can collaborate with each other. It has a shorter version in ACL 2000.

- Patrick Pantel and Dekang Lin, Discovering Word Senses from Text, SIGKDD, 2002.

  > Supervised WSD has been explored a lot in the early 00's thanks to the senseval workshop, but a few system actually benefits from WSD because manually crafted sense mappings are hard to obtain. These days we see a lot of evidence that unsupervised clustering improves NLP tasks such as NER, parsing, SRL, etc, and this work is one of the roots of unsupervised clustering of words

- Mike Mintz et al.: Distant supervision for relation extraction without labeled data, ACL 2009.

  ---

- Zhiheng Huang et al.: Bidirectional LSTM-CRF Models for Sequence Tagging, 2015.

  

## Machine Learning

- Avrim Blum and Tom Mitchell: Combining Labeled and Unlabeled Data with Co-Training, 1998.

- John Lafferty, Andrew McCallum, Fernando C.N. Pereira: Conditional Random Fields: Probabilistic Models for Segmenting and Labeling Sequence Data, ICML 2001. **Test-of-time Award in ICML 2011** [paper](<http://repository.upenn.edu/cgi/viewcontent.cgi?article=1162&context=cis_papers>) 

- Charles Sutton, Andrew McCallum. An Introduction to Conditional Random Fields for Relational Learning.

  > everyone should know CRFs, and this paper is the easiest to understand

- Kamal Nigam, et al.: Text Classification from Labeled and Unlabeled Documents using EM. Machine Learning, 1999.

- Kevin Knight: Bayesian Inference with Tears, 2009.

  > explains the general idea of bayesian techniques quite well

+ Painless Unsupervised Learning with Features

  > this is from this year and thus a bit of a gamble, but this has the potential to bring the power of discriminative methods to unsupervised learning



## Topic Models

- Thomas Hofmann: Probabilistic Latent Semantic Indexing, SIGIR 1999.
- David Blei, Andrew Y. Ng, and Michael I. Jordan: Latent Dirichlet Allocation, J. Machine Learning Research, 2003.

## Machine Translation & Transliteration, Sequence-to-Sequence Models

+ Peter F. Brown et al.: A Statistical Approach to Machine Translation, Computational Linguistics, 1990.

+ Kevin Knight, Graehl Jonathan. Machine Transliteration. Computational Linguistics, 1992.

+ Dekai Wu: Inversion Transduction Grammars and the Bilingual Parsing of Parallel Corpora, Computational Linguistics, 1997.

  > arguably the first realistic method for biparsing, which is used in many systems

+ Kevin Knight: A Statistical MT Tutorial Workbook, 1999.

  > easy to understand, use instead of the original Brown paper

+ Philipp Koehn, Franz J Och, and Daniel Marcu: Statistical Phrase-Based Translation, NAACL 2003.

+ Philip Resnik and Noah A. Smith: The Web as a Parallel Corpus, Computational Linguistics, 2003.

+ Franz J Och and Hermann Ney: The Alignment-Template Approach to Statistical Machine Translation, Computational Linguistics, 2004.

  > foundations of phrase based systems

+ David Chiang. A Hierarchical Phrase-Based Model for Statistical Machine Translation, ACL 2005.

  > significantly improves accuracy by allowing for gappy phrases

  ---

+ Ilya Sutskever, Oriol Vinyals, and Quoc V. Le: Sequence to Sequence Learning with Neural Networks, NIPS 2014. [arxiv](https://arxiv.org/abs/1409.3215) |  [seq2seq](https://google.github.io/seq2seq/)  :star::star::star::star::star:  

+ Oriol Vinyals, Quoc Le: A Neural Conversation Model, 2015.

+ Dzmitry Bahdanau, et al.: Neural Machine Translation by Jointly Learning to Align and Translate, 2014.

+ Minh-Thang Luong, et al.: Effective Approaches to Attention-based Neural Machine Translation, 2015.

+ Yonghui Wu, et al.: Google’s Neural Machine Translation System: Bridging the Gap between Human and Machine Translation, 2016.

+ Jonas Gehring, et al.: Convolutional Sequence to Sequence Learning, 2017.

+ Ashish Vaswani, et al.: Attention Is All You Need, 2017. [arxiv](https://arxiv.org/abs/1706.03762) | [code](https://github.com/tensorflow/tensor2tensor) | [code](<https://github.com/Kyubyong/transformer>) 

## Automatic Text Summarization

(the year 2007 was a milestone of summarization research, studies of automatic text summarization have been strongly influenced by machine translation)

- Kevin Knight and Daniel Marcu: Summarization beyond sentence extraction. Artificial Intelligence 139, 2002.

  > opens the door to statistical approach to sentence compression

- James Clarke and Mirella Lapata: Modeling Compression with Discourse Constraints. EMNLP-CONLL 2007.

  > shows importance of joint inference

- Ryan McDonald: A Study of Global Inference Algorithms in Multi-Document Summarization, ECIR 2007.

  > formulates summarization task as global optimization problem using integer linear programming

- Wen-tau Yih et al.: Multi-Document Summarization by Maximizing Informative Content-Words. IJCAI 2007.

  > introduces stack decoding to this field

  ---

- Alexander M Rush, et al.: A Neural Attention Model for Sentence Summarization. EMNLP 2015.


## Neural Models

- Richard Socher, et al.: Dynamic Pooling and Unfolding Recursive Autoencoders for Paraphrase Detection, NIPS 2011.

- Ronan Collobert et al.: Natural Language Processing (almost) from Scratch, J. of Machine Learning Research, 2011.  [arxiv](https://arxiv.org/abs/1103.0398) :star::star::star::star::star: 

  **architecture** - neural network for nlp

- Richard Socher, et al.: Recursive Deep Models for Semantic Compositionality Over a Sentiment Treebank, EMNLP 2013.

- Xiang Zhang, Junbo Zhao, and Yann LeCun: Character-level Convolutional Networks for Text Classification, NIPS 2015.

- Yoon Kim: Convolutional Neural Networks for Sentence Classification, 2014.

- Christopher Olah: Understanding LSTM Networks, 2015.

- Matthew E. Peters, et al.: Deep contextualized word representations, 2018. [arxiv](https://arxiv.org/abs/1802.05365?context=cs) 

- Jacob Devlin, et al.: BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding, 2018. [arxiv](https://arxiv.org/abs/1810.04805?context=cs) 

## Other

+ Thumbs up?: Sentiment Classification using Machine Learning Techniques, Bo Pang, Lillian Lee, Shivakumar Vaithyanathan, EMNLP 2002, [arxiv](<https://arxiv.org/abs/cs/0205070>)  **Test of time award at NAACL 2018**

  > **Justification**: Sentiment analysis in one of the earliest NLP tasks that has had direct real-world impact in a number of industries. It now has a widespread and practical application in review mining, customer management, social media analysis, news analysis, healthcare support and decision support in the finance industry. Pang, Lee and Vaithyanathan (2002) ‘s paper is a pioneering work that has enabled NLP to make this impact. It is amongst the first works in sentiment analysis and helped define the subfield of sentiment and opinion analysis and review mining. It has become the go to paper for anyone starting work in this area. This work has had research, application and data impact. The paper introduced a new way to look at document classification, developed the first solutions to it using several machine learning methods and feature combinations, and presented insights into and challenges of sentiment classification. Beyond the task formulation and technical methods, this paper also had significant data impact. The movie review dataset has supported much of the early work in this area and it still is one of the commonly used benchmark evaluation datasets. There are two key reasons for this success: (a) emphasis on making the data widely available; and (b) carefully curating the data, for example to avoid domination of prolific reviewers. The data is extensively used in courses, and is part of NLTK as a core application to start for students interested in NLP. The insights and challenges discussed in this work have provided the basis of many works and is still driving new research today. According to recent statistics it is the highest cited EMNLP paper. With over 6800 Google scholar citations, and over 400 Google scholar citations in 2017 alone, this work has stood the test of time. Given the award time constraints, it is the last opportunity for this paper to be considered.

+ [BLEU: a Method for Automatic Evaluation of Machine Translation](https://www.aclweb.org/anthology/P02-1040.pdf). Papineni et al. ACL 2002. **Test-of-time award at NAACL 2018**

  >**Justification**: It has long-lasting and ongoing impact to the field of machine translation both in research communities and industries. The metric is a standard measure to evaluate translation qualities and it helps advance the state of the art of machine translation systems.

+ An algorithm for suffix stripping, M.F. Porter 1997. Cited by: 9977 [pdf](<https://cl.lingfil.uu.se/~marie/undervisning/textanalys16/porter.pdf>) 

+ Snowball: A language for stemming algorithms, M.F. Porter 2001. [site](<http://snowball.tartarus.org/texts/introduction.html>) 

  

## Scholars

### Michael Collins

Michael Collins: [Head-Driven Statistical Models for Natural Language Parsing](http://www.cs.columbia.edu/~mcollins/papers/thesis.ps), PhD Dissertation, University of Pennsylvania, 1999.