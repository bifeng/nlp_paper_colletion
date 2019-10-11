### Question

+ 它是怎样影响下一个词语的生成？描述这个过程？

+ How to deal with the discrepancy of training and testing ?

  At test time, word generation process is heavily skewed towards copying ! The disparity is likely due to the fact that during training, the model receives word-by-word supervision in the form of the reference summary, but at test time it does not.

  

+ why the extractive systems tend to obtain higher scores than abstractive ?

  metric preference

  article style



### Contribution

The network, which can be viewed as a balance between extractive and abstractive approaches, is similar to Gu
et al.’s (2016) CopyNet and Miao and Blunsom’s (2016) Forced-Attention Sentence Compression, that were applied to short-text summarization.



### Architecture





+ coverage vector and coverage loss

  Zhaopeng Tu, Zhengdong Lu, Yang Liu, Xiaohua Liu, and Hang Li. 2016. Modeling coverage for neural
  machine translation. In Association for Computational Linguistics.

  

  Reduce the repeating phenomenon 

+ pointing

  Oriol Vinyals, Meire Fortunato, and Navdeep Jaitly. 2015. Pointer networks. In Neural Information Processing
  Systems.

  

  Deal with out-of-vocabulary (OOV) words



### Strategy

1. data truncate strategy 

   truncate the article to 400 tokens and limit the length of the summary to 100 tokens for training and 120 tokens at test time. 

   This is done to expedite (加速) training and testing, but we also found that truncating the article can raise the performance of the model.

   For training, we found it efficient to start with highly-truncated sequences, then raise the maximum length once
   converged. At test time our summaries are produced using beam search with beam size 4.

   (explanation for the improved performance by truncated article: news articles tend to be structured with the most important information at the start)

2. two - stage training strategy 

   First, training the pointer-generator model.

   Second, To obtain our final coverage model, we added the coverage mechanism with coverage loss weighted
   to $\lambda = 1$, and trained for a further 3000 iterations.

   We also tried training with coverage from the first iteration rather than as a separate training phase, but found that in the early phase of training, the coverage objective **interfered** with the main objective, reducing overall performance.

### Metric

+ ROUGE

  Due to the subjectivity of the task and thus the diversity of valid summaries, it seems that ROUGE rewards safe strategies such as selecting the first-appearing content, or preserving original phrasing.

+ METEOR 

  the METEOR metric, which rewards not only exact word matches, but also matching stems, synonyms and paraphrases (from a predefined list).



