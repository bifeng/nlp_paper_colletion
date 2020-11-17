#### Task

The dialogue state is an encoding of the machine’s understanding of the whole conversation.
Traditionally, it is usually factorized into three distinct components (Young et al., 2013): the user’s goal, the user’s action, and the dialogue history.



Steve Young, Milica Gasic, Blaise Thomson, and Jason D. Williams. 2013. POMDP-based statistical spoken dialog systems: A review. Proceedings of the IEEE, 101(5):1160–1179.



#### conference

+ SIGDIAL
+ 

#### SOTA

<http://nlpprogress.com/english/dialogue.html>

<https://paperswithcode.com/task/dialogue-state-tracking>



#### dataset

+ https://research.fb.com/downloads/babi/

  https://github.com/facebook/bAbI-tasks

  

+ https://www.microsoft.com/en-us/research/event/dialog-state-tracking-challenge/

  https://www.microsoft.com/en-us/research/event/dialog-state-tracking-challenge/#!overview-publications

+ 

#### literature review

+ 




#### Tools

https://github.com/voicy-ai/DialogStateTracking

https://github.com/vyraun/chatbot-MemN2N-tensorflow



#### Paper

+ Towards Universal Dialogue State Tracking, Liliang Ren, Kaige Xie, Lu Chen and Kai Yu, EMNLP 2018, [arxiv](<https://arxiv.org/abs/1810.09587v1>) 

  We focus on the tracking of the user’s goal.

  Previous work limitations: 1) some models can only work on a fixed domain ontology, i.e. the slots and values are defined in advance, and can’t change dynamically. 2) in many approaches the models for every slot are different. Therefore, the number of parameters is proportional to the number of slots. 3) some models extract features based on text delexicalisation (Henderson et al., 2014b), which depends on predefined semantic dictionaries.

  **StateNet** shares parameters among all slots, through which we can not only transfer knowledge among slots but also reduce the number of parameters.



















