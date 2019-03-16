https://en.wikipedia.org/wiki/Paraphrasing_(computational_linguistics)



methods:

Deep Reinforcement Learning

VAE



### Literature review

+ A Survey of Paraphrasing and Textual Entailment Methods, 2010 [arxiv](https://arxiv.org/abs/0912.3747) 

### paper

+ Dictionary-Guided Editing Networks for Paraphrase Generation, AAAI 2019, [arxiv](https://arxiv.org/abs/1806.08077) 

  

+ Paraphrase Generation with Deep Reinforcement Learning, EMNLP 2018, [arxiv](https://arxiv.org/abs/1711.00279v3) | [pdf](http://www.hangli-hl.com/uploads/3/4/4/6/34465961/li_et_al_emnlp_2018.pdf) | [code](https://github.com/leechihahchiu/DRLParaphrase) 

  + [x] generation model

    <details><summary>notes</summary>
        The generator, built as a sequence-to-sequence learning model, can produce paraphrases given a sentence. <br>
        The evaluator, constructed as a deep matching model, can judge whether two sentences are paraphrases of each other.<br>
        The generator is first trained by deep learning and then further fine-tuned by reinforcement learning in which the reward is given by the evaluator.

+ A Deep Generative Framework for Paraphrase Generation, AAAI 2018, [arxiv](https://arxiv.org/abs/1709.05074) | [blog](https://ldzhangyx.github.io/2018/09/26/deep-para-generation/) | [code](https://github.com/ale3otik/paraphrases-generator) | [code](https://github.com/paulx3/keras_generative_pg) 

  

+ Neural Paraphrase Generation with Stacked Residual LSTM Networks, COLING 2016 [arxiv](https://arxiv.org/abs/1610.03098) | [code](https://github.com/iamaaditya/neural-paraphrase-generation/tree/add-license-1) 



### tools

+ [paraphraser](https://github.com/vsuthichai/paraphraser) 
+ 

