methods

#### Deep Reinforcement Learning



### paper

+ Paraphrase Generation with Deep Reinforcement Learning, EMNLP 2018, [arxiv](https://arxiv.org/abs/1711.00279v3) | [pdf](http://www.hangli-hl.com/uploads/3/4/4/6/34465961/li_et_al_emnlp_2018.pdf) 
  + [x] generation model

    <details><summary>notes</summary>
        The generator, built as a sequence-to-sequence learning model, can produce paraphrases given a sentence. <br>
        The evaluator, constructed as a deep matching model, can judge whether two sentences are paraphrases of each other.<br>
        The generator is first trained by deep learning and then further fine-tuned by reinforcement learning in which the reward is given by the evaluator.

