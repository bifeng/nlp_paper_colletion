## Tasks

A well-known *document image analysis* product is the Optical Character Recognition (OCR) software that recognizes characters in a scanned *document*.



## Challenge

the diversity of layouts and formats

poor quality of scanned document images 

the complexity of template structures.



## Keywords

Document Image Understanding

Document Image Analysis

Document AI

Document Intelligence

visually rich documents



## Workshop

+ Workshop on Document Intelligence (DI 2019) at NeurIPS 2019 [site](<https://sites.google.com/view/di2019>) 



## Literature Review

+ LayoutLM: Pre-training of Text and Layout for Document Image Understanding

  > The research of Document Analysis and Recognition (DAR) dates to the early 1990s. The mainstream approaches can be divided into three categories: rule-based approaches, conventional machine learning approaches and deep learning approaches.
  >
  > ...

  







## Paper

+ LayoutLM: Pre-training of Text and Layout for Document Image Understanding
  Yiheng Xu, Minghao Li, Lei Cui, Shaohan Huang, Furu Wei, Ming Zhou [arxiv](https://arxiv.org/abs/1912.13318) [code](https://github.com/microsoft/unilm/tree/master/layoutlm) 

  > 1. pre-trained NLP models
  >
  >    OCR 
  >
  >    fine-tuning - sequential labeling
  >
  >    
  >
  > 2. a joint training of textual and layout information
  >
  >    OCR ->  the bounding box of each word
  >
  >    pre-training
  >
  >    fine-tuning - sequential labeling
  >
  >    
  >
  >    we use the BERT architecture as the backbone and add two types of new input embeddings: a 2-D
  >    position embedding and an image embedding.
  >
  >    2-D position embedding aims to model the relative spatial position in a document. 
  >
  >    image embedding aims to align the image feature with the text. - The Faster R-CNN model (generate the image region features with these pieces of images as the token image embeddings, and produce
  >    embeddings using the whole scanned document image as the Region of Interest (ROI) and the [CLS] token embedding.)
  >
  >    
  >
  > 3. 数据集的每张图片必须是独立的，例如单据，必须在一张图片上？
  >
  >    
  >
  > 4. 





“BERTGrid: Contextualized Embedding for 2D Document Representation and Understanding”, by Timo I. Denk and Christian Reisswig.  The Best Paper Award of the DI'2019 Workshop. 



LAMBERT: Layout-Aware language Modeling using BERT for information extraction
Łukasz Garncarek, Rafał Powalski, Tomasz Stanisławek, Bartosz Topolski, Piotr Halama, Filip Graliński [arxiv](<https://arxiv.org/abs/2002.08087>) 



Graph Convolution for Multimodal Information Extraction from Visually Rich Documents
Xiaojing Liu, Feiyu Gao, Qiong Zhang, Huasha Zhao. naacl'19



Berardi, Margherita, Michele Lapi, and Donato Malerba. "An integrated approach for automatic semantic structure extraction in document images." *International Workshop on Document Analysis Systems*. Springer, Berlin, Heidelberg, 2004.

