Analyses :star::star::star::star::star:<br>(recommend reading the analyses part of this paper)



#### Word representation

non-contextual word representation



contextual word representation<br>contextual word representations learned supervisedly (e.g., through machine translation; McCann et al., 2017) or unsupervisedly (typically through language modeling; Peters et al., 2018)

#### Sentence embedding

Learn sentence representations via different pretraining objectives such as previous/next sentence prediction (Kiros et al., 2015; Logeswaran and Lee, 2018), NLI (Conneau et al., 2017), or a combination of objectives (Subramanian et al., 2018). This is typically used as **feature extraction**.

LM pretraining with **fine-tuning** has also been successfully applied to <u>sentence level tasks</u>. Howard and Ruder (2018, ULMFiT) propose techniques for fine-tuning a LM, including triangular learning rate schedules and discriminative finetuning, which uses lower learning rates for lower layers. Radford et al. (2018) extend LM- to <u>additional sentence and sentence-pair tasks</u>.

#### Combined

BERT (Devlin et al., 2018) combines both word and sentence representations (via masked LM and next sentence prediction objectives) in a single very large pretrained transformer (Vaswani et al., 2017). It is adapted to <u>both word and sentence level tasks</u> by with task-specific layers.



#### feature extraction ELMo  and BERT

For both ELMo and BERT, we extract contextual representations of the words from all layers. During adaptation, we learn a linear weighted combination of the layers (Peters et al., 2018) which is used as input to a task specific model. When extracting features, it is important to expose the internal layers as they typically encode the most transferable representations.



**more feature extraction details for each tasks in this paper: "A Experimental details" part.**



#### fine-tuning ELMo  and BERT

ELMo<br>We max-pool over the LM states and add a softmax layer for <u>text classification</u>. For <u>the sentence pair tasks</u>, we compute cross-sentence bi-attention between the LM states (Chen et al., 2017), apply a pooling operation, then add a softmax layer. For <u>NER</u>, we add a CRF layer on top of the LSTM states.

Fine-tuning the ELMo LSTM to be initially difficult and required careful hyper-parameter tuning. Once tuned for one task, other tasks have similar hyperparameters. Our best models used slanted tri-angular learning rates and discriminative fine-tuning (Howard and Ruder, 2018) and in some cases gradual unfreezing (Howard and Ruder, 2018) to match performance of feature extraction.

BERT<br>We feed the sentence representation into a softmax layer for <u>text classification</u> and <u>sentence pair tasks</u> following Devlin
et al. (2018). For <u>NER</u>, we extract the representation of the first word piece for each token and add a softmax layer.



**more fine-tuning details for each tasks in this paper: "A Experimental details" part.**



#### analyses (explanations)

... measure this information in two ways: a) with diagnostic classifiers (Adi et al., 2017); and b) with mutual information (MI; Noshad et al., 2018). Both methods allow us to associate the hidden activations of our model with a linguistic property....





#### summary

#### 

<div align="center">
<img src="https://github.com/bifeng/nlp_paper_notes/raw/master/image/elmo_bert_fe_ft.png" width="800" height="600" alt="elmo_bert_fe_ft"></img>
</div>

SA - sentiment analysis

For ELMo, we find the largest differences for sentence pair tasks where <u>feature extraction</u> consistently outperforms <u>fine-tuning</u>. 

For BERT, we obtain nearly the opposite result: <u>fine-turning</u> significantly outperforms <u>feature extraction</u> on all STS tasks, with much smaller differences for the others.

Feature extraction, the transferability of features decreases as the distance between the pretraining and target task increases.

Fine-tuning, strong performance for closely aligned tasks (next-sentence prediction in BERT and STS tasks) and poor performance for more distant tasks (LM in ELMo and sentence pair tasks).













