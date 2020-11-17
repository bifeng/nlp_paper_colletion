- How to introduce traditional features into neural network models?

- 

- 如何避免某类别的强特征(dominant)导致的过拟合问题?

  1-将强特征涉及的词语随机替换

  2-

  

- 类别样本特征重叠，导致难以区分？

  margin loss -  https://spaces.ac.cn/archives/5743/comment-page-1

- 非平衡样本的评价指标？

  macro, micro - http://zhpmatrix.github.io/2019/06/29/sklearn-classification-report/

3. Using the classify model as the feature extractor, and calculate the similarity of between samples. Like in the face detection, which there is a face not in the repository. 



### 负样本构建

负样本，主要为无效问题，包括领域相关但类别无关问题、领域无关问题。

1. 从正样本出发，寻找能够主导某些类别的强特征（可能是某些词语足以判断类别）
2. 从badcase出发，寻找badcase的强特征且该特征属于正样本的弱特征

基于特征，利用语言模型（最好是当前分类相关领域的）生成序列，该序列作为负样本。



### 无效问题-区分

more refer:

<https://stackoverflow.com/questions/43578715/how-best-to-deal-with-none-of-the-above-in-image-classification>

> You really have these two options indeed--thresholding the posterior probabilities (softmax values), and adding a garbage class.
>
> In my area (speech), both approaches are their place:
>
> If "none of the above" inputs are of the same nature as the "above" (e.g. non-grammatical inputs), thresholding works fine. Note that the posterior probability for a class is equal to one minus an estimate of the error rate for choosing this class. Rejecting anything with posterior < 50% would be rejecting all cases where you are more likely wrong than right. As long as your none-of-the-above classes are of similar nature, the estimate may be accurate enough to make this correct for them as well.
>
> If "none of the above" inputs are of similar nature but your number of classes is very small (e.g. 10 digits), or if the inputs are of a totally different nature (e.g. a sound of a door slam or someone coughing), thresholding typically fails. Then, one would train a "garbage model." In our experience, it is OK to include the training data for the correct classes. Now the none-of-the-above class may match a correct class as well. But that's OK as long as the none-of-the-above class is not overtrained--its distribution will be much flatter, and thus even if it matches a known class, it will match it with a lower score and thus not win against the actual known class' softmax output.
>
> In the end, I would use both. Definitely use a threshold (to catch the cases that the system can rule out) *and* use a garbage model, which I would just train it on whatever you have. I would expect that including the correct examples in training will not harm, even if it is the only data you have. It may also make sense to try to synthesize data, e.g. by randomly combining patches from different images.
>
> 
>
> There's one recent paper by [Zhang and LeCun](https://arxiv.org/abs/1511.03719), that addresses the question for image classification in particular. They use large quantities of unlabelled data to create an additional "none of the above" class. The catch though is that, in some cases, their unlabelled data is not completely unlabelled, and they have means of removing "unlabelled" images that are actually in one of their labelled classes. Having said that, the authors report that apart from solving the "none of the above" problem, they even see performance gains even on their test sets.





keyword: nonsense, 无效问题

How to classify 'other class' which is not in the label set？

Solution:

1. Common method is add a `NA` label. 
2. Using (1/num_labels) as the probability of `NA` (:question:)
3. one class classification problem







