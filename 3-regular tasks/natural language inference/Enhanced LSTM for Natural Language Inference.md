### Question

+ Can exchange the premise and hypothesis in the input ?
+ Why use BiLSTM for aggregate (composition) ? what's the advantage?
+ Attention use for alignment, but most of words in premise and hypothesis is not alignment, how to make use of the information that words correlate but contradiction, such as `sitting` and `standing` ?

![attention](https://github.com/bifeng/daily_book_notes/raw/master/resource/esim_attention.png)

### Summary

+ represent compare aggregate architecture

  represent: BiLSTM

  compare (inference): attention

  aggregate (composition): BiLSTM

  

+ compare (local inference)

  Modeling local inference needs to employ some forms of hard or soft alignment to associate the relevant subcomponents between a premise and a hypothesis.

  In neural network models, this is often achieved with soft attention.

  

+ enhancement of local inference information

  The difference and element-wise product are then concatenated with the original vectors, ¯a and ˜a,
  or ¯b and ˜ b, respectively (Mou et al., 2016; Zhang et al., 2017).

  $m_a = [\bar{a};\tilde{a};\bar{a}-\tilde{a};\bar{a}\odot\tilde{a}]$ 

  $m_b = [\bar{b};\tilde{b};\bar{b}-\tilde{b};\bar{b}\odot\tilde{b}]$ 

+ from compare to aggregate

  We propose to control model complexity in the aggregate layer, since the concatenation we described above
   can significantly increase the overall parameter size to potentially overfit the models.

  we use a 1-layer feedforward neural network with the ReLU activation.

+ from aggregate to classifier

  We consider that summation (Parikh et al., 2016) could be sensitive to the sequence length and hence less robust. We instead suggest the following strategy: compute both average and max pooling, and concatenate all these vectors to form the final fixed length vector v.

  $v = [v_{a,ave};v_{a,max};v_{b,ave};v_{b,max}]$