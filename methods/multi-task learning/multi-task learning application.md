refer:

books - Neural Network Methods in NLP



### Sentence Compression, Gaze-prediction, CCG Supertagging

Sigrid Klerke, Yoav Goldberg, and Anders Søgaard. Improving sentence compression by learning to predict gaze. In Proc. of the Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, pages 1528–1533, 2016. http://aclweb.org/anthology/N16-1179 DOI: 10.18653/v1/N16-1179.

### Arc Labeling, Syntactic Parsing

Eliyahu Kiperwasser and Yoav Goldberg. Simple and accurate dependency parsing using bidirectional LSTM feature representations. Transactions of the Association of Computational Linguistics—(Volume 4, Issue 1), pages 313–327, 2016b. http://aclweb.org/anthology/Q16-1023

> Training the joint network for performing both unlabeled arc-scoring and
> arc-labeling, using the same shared biRNN encoder, not only results in accurate arc labeling, but also substantially improves the accuracy of the unlabeled parse trees.

### Preposition Sense Disambiguation, Preposition Translation Prediction

Hila Gonen and Yoav Goldberg. Semi supervised preposition-sense disambiguation using multilingual data. In Proc. of COLING, the 26th International Conference on Computational Linguistics: Technical Papers, pages 2718–2729, Osaka, Japan, December 2016. The COLING 2016 Organizing Committee. http://aclweb.org/anthology/C16-1256

### Conditioned Generation: Multilingual Machine Translation, Parsing, Image Captioning

Minh-Thang Luong, Quoc V. Le, Ilya Sutskever, Oriol Vinyals, and Lukasz Kaiser. Multi-task sequence to sequence learning. In Proc. of ICLR, 2016.

> Luong et al explore different setups of multi-task learning under this system. 
>
> In the first setup (one-to-many), the Encoder component (encoding English sentences into vectors) is shared, and is used with two different decoders: one decoder is generating German translations, and the other decoder is generating linearized parse-trees for the English sentences.
>
> In the second setup (many-to-one), there is a single decoder, but several different encoders. The decoder is tasked at producing English sentences. One encoder is encoding German sentences, while the other is encoding images. The tasks here are machine translation (German to English translation) and image captioning (Image to English description). 

