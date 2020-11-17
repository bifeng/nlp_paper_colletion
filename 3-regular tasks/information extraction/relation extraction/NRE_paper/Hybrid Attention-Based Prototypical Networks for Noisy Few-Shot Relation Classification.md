### Contribution

a hybrid attention consisting of an instance-level attention and a feature-level attention.

The instance-level attention module is able to select more <u>informative instances in the support set</u> (focus more attention on those query-related instances) and denoise those noisy instances during training.

The feature-level attention module can highlight important dimensions in the feature space and formulate <u>specific distance functions</u> for different relations, which enables our model to alleviate the problem of feature sparsity.

### Hyperparameters

Prototypical Networks:

According to Snell, Swersky, and Zemel (2017), feeding more classes than test settings during training leads to better
results, we thus randomly choose 20 classes for each batch when training.

We tune all other hyperparameters of all models by **grid search** using the validation set, especially for determining
the best initial learning rate and weight decay.

we use step policy to decay the learning rate. That is to say, the learning rate will be multiplied by $\gamma$ every $s$ steps.





