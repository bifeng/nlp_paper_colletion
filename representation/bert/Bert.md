### Awesome

https://github.com/Jiakui/awesome-bert





#### reg

http://fancyerii.github.io/2019/03/20/bert-reg/

https://github.com/google-research/bert/issues/74



#### rank

https://github.com/nyu-dl/dl4marco-bert

#### multi-task



#### Visualization

A Multiscale Visualization of Attention in the Transformer Model
Jesse Vig

<https://github.com/jessevig/bertviz>





### Paperlist

+ Bert Evolution

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/bert_evolution.jpg" width="600" height="400" alt="bert_evolution"></img>
</div>


+ 8篇论文梳理BERT相关模型进展与反思 [site](<https://www.msra.cn/zh-cn/news/features/bert>) 



### paper

+ Yoav Goldberg. Assessing BERT’s syntactic abilities, 2019. arXiv:1901.05287.

+ BERT has a Mouth, and It Must Speak: BERT as a Markov Random Field Language Model, Alex Wang, Kyunghyun Cho, 2019 [arxiv](https://arxiv.org/abs/1902.04094) | [code](https://github.com/nyu-dl/bert-gen)  

+ To Tune or Not to Tune? Adapting Pretrained Representations to Diverse Tasks, Matthew Peters, Sebastian Ruder, Noah A. Smith, 2019 [arxiv](https://arxiv.org/abs/1903.05987) 

+ Linguistic Knowledge and Transferability of Contextual Representations-1903.08855

+ Distilling Task-Specific Knowledge from BERT into Simple Neural Networks, Raphael Tang, Yao Lu, Linqing Liu, Lili Mou, Olga Vechtomova, Jimmy Lin, [arxiv](https://arxiv.org/abs/1903.12136) 

  

+ How to Fine-Tune BERT for Text Classification?-1905.05583 [arxiv](https://arxiv.org/pdf/1905.05583.pdf)

+ Simple BERT Models for Relation Extraction and Semantic Role Labeling-1904.05255 [arxiv](https://arxiv.org/pdf/1904.05255.pdf) 

+ Pretraining-Based Natural Language Generation for Text Summarization-1902.09243

+ Toward Fast and Accurate Neural Chinese Word Segmentation with Multi-Criteria Learning [arxiv](https://arxiv.org/pdf/1903.04190.pdf) 

  BERT + model compression + multi-criterial learing 


#### explain

+ Revealing the Dark Secrets of BERT [paper](<https://www.aclweb.org/anthology/D19-1445.pdf>) [blog](<https://text-machine-lab.github.io/blog/2020/bert-secrets/>) 
  
+ BERT Rediscovers the Classical NLP Pipeline
  Ian Tenney, Dipanjan Das, Ellie Pavlick.  ACL 2019 [arxiv](<https://arxiv.org/abs/1905.05950>) 

+ What do you learn from context? Probing for sentence structure in contextualized word representations.

  Ian Tenney, Patrick Xia, Berlin Chen, Alex Wang, Adam Poliak, R. Thomas McCoy, Najoung Kim, Benjamin Van Durme, Samuel R. Bowman, Dipanjan Das, and Ellie Pavlick. ICLR 2019. https://openreview.net/forum?id=SJzSgnRcKX



### blogs

+ <http://jalammar.github.io/illustrated-bert/>
+ [8篇论文梳理BERT相关模型进展与反思](<https://www.msra.cn/zh-cn/news/features/bert>) 
+ 从语言模型看Bert的善变与GPT的坚守 [site](https://mp.weixin.qq.com/s/zqlWx3e4LOJ3_Zy2DEbCjw) 
  穆文MuWen 数据挖掘机养成记 2019-05-20

### code

https://github.com/google-research/bert

https://github.com/huggingface/pytorch-pretrained-BERT



multi-label classification:<br>https://github.com/yuanxiaosc/Entity-Relation-Extraction







### datasets

[multilingual](https://github.com/google-research/bert/blob/master/multilingual.md) Chinese

The entire Wikipedia dump for each language (excluding user and talk pages) was taken as the training data for each language.

we performed <u>exponentially smoothed weighting</u> of the data during pre-training data creation (and WordPiece vocab creation). So, high-resource languages like English will be under-sampled, and low-resource languages like Icelandic will be over-sampled.



### excise

- bert for ranking
- bert for text generation
- 