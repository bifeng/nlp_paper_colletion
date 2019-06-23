[code](https://github.com/yagays/all_but_the_top/blob/master/src/all_but_the_top.py) 



### Summary

+ eliminate <u>the common mean vector</u> and <u>a few top dominating directions</u> from the word vectors

  (the variances explained by the leading principal components (PCs) “encode the frequency of the word to a significant degree”. Since word frequencies are arguably unrelated to lexical semantics, they recommend removing such leading PCs from word vectors using a PCA reconstruction)



### Motivation

Observation:

+ The word representations have non-zero mean – indeed, word vectors share a large common vector (with norm up to a half of the average norm of word vector).
+ After removing the common mean vector, the representations are far from isotropic (各向同性) – indeed, much of the energy of most word vectors is contained in a very low dimensional subspace (say, 8 dimensions out of 300).

Implication:

For **the common vector** - removing the nonzero mean vector from all word vectors, effectively reducing the energy;

For **the dominating directions** - projecting the representations away from the dominating $D$ directions, effectively reducing the dimension. (a rule of thumb of choosing $D$ around $d/100$, where $d$ is the dimension of the word representations)

The proposed postprocessing is <u>counter intuitive</u> – typically denoising by dimensionality reduction is done by **eliminating the weakest directions** (in a singular value decomposition of the stacked word vectors), and not the dominating ones. Yet, such postprocessing yields a “purified” and more “isotropic” word representation.



#### Question

+ This paper claimed that this postprocessing using dimensionality reduction is done by **eliminating the weakest directions**, but in the code it's eliminating the dominating ones. why?

   





### Algorithm

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/all_but_the_top.png" width="800" height="300" alt="all_but_the_top"></img>
</div>









