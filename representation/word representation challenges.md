refer: Contextual Word Representations: A Contextual Introduction, Noah A. Smith, February 2019, [arxiv](https://arxiv.org/pdf/1902.06006.pdf) 





#### Challenges

It is an open and exciting question how much of the work of understanding can be done at the level of words.

##### Polysemy (一词多义)

solution:

1. training a contextual word vectors, such as ELMo. Solved totally?
2. each word token’s type vector is passed into a function that transforms it based on the words in its nearby context, giving a new version of the word vector, now specific to the token in its particular context.



##### Word vectors are biased

corpus-derived word vectors will reflect what's in the data, such as cultural biases.

Methods for detecting and correcting unwanted associations is an active area of research (Bolukbasi et al., 2016; Caliskan et al., 2017). The advent of contextual word vectors offers some possibility of new ways to avoid unwanted generalization from distributional patterns.















