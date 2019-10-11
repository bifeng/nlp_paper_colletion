[code](https://github.com/wuzhiye7/Induction-Network-on-FewRel) there are bugs!

### Question

+ What's parameter will be update in optimization about dynamic routing ?
+ why use sigmoid in the relation module ?  not softmax ?
+ why use mse in the objective function ?



### Motivation

in previous studies, class-level representations are calculated by simply summing or averaging representations of samples in the support set. In doing so, key information may be lost in the noise brought by various forms of samples in the same class. This problem will be more serious when the support set becomes larger.

Instead, a better learning approach may be induction on a class-wise level: ignoring irrelevant details and encapsulating general semantic information from samples with various linguistic forms in the same class.

### Architecture

#### Encoder module

#### Induction module

The main purpose of the induction module is to design a non-linear mapping from sample vector $e^s_{ij}$ to class vector $c_i$.



1. a weight-sharable transformation across all sample vectors in the support set is employed. All of the sample vectors in the support set share the same transformation weights $W_s$, so that the model is flexible enough to handle the support set at any scale.
2. To ensure the class vector encapsulate the sample feature vectors of this class automatically, dynamic routing is
   applied iteratively. In each iteration, the process dynamically amends the connection strength and makes sure that the coupling coefficients $d_i$ sum to 1 between class $i$ and all support samples in this class by a “routing softmax”.
3. a non-linear "squashing" function is applied to ensure that length of the vector output of the routing process will
   not exceed 1. The short vectors get shrunk to almost zero length and the long vectors get shrunk to a length slightly below 1. The squash function leaves the direction of the vector unchanged but decreases its magnitude.
4. in every iteration is to adjust the logits of coupling coefficients $b_{ij}$ by a “routing by agreement” method. If the produced class candidate vector has a large scalar output with one sample prediction vector, there is a top-down feedback which increases the coupling coefficient for that sample and decreases it for other samples.





##### dynamic routing

Sara Sabour, Nicholas Frosst, and Geoffrey E Hinton. Dynamic routing between capsules. In Advances in Neural Information Processing Systems, pages 3856–3866, 2017. [arxiv](https://arxiv.org/abs/1710.09829) | [code](https://github.com/naturomics/CapsNet-Tensorflow) 

<https://www.zhihu.com/question/67287444/answer/251460831>

<https://jhui.github.io/2017/11/03/Dynamic-Routing-Between-Capsules/>

Investigating Capsule Networks with Dynamic Routing for Text Classification, Wei Zhao, Jianbo Ye, Min Yang, Zeyang Lei, Suofei Zhang, Zhou Zhao, [arxiv](https://arxiv.org/abs/1804.00538) | [code](https://github.com/andyweizhao/capsule_text_classification) 



#### Relation module



##### neural tensor layer
Richard Socher, Danqi Chen, Christopher D Manning, and Andrew Ng. Reasoning with neural tensor networks for
knowledge base completion. In Advances in neural information processing systems, pages 926–934, 2013. [code](https://github.com/dddoss/tensorflow-socher-ntn) 



#### Objective function







