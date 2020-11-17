《Data Noising As Smoothing in Neural Network Language Models》，ICLR2017

1. unigram noising

   for each word, with probability $\gamma$ replace it with a sample from the unigram frequency distribution

2. blank noising

   for each word, with probability $\gamma$ replace it with a placeholder token "_"

3. 