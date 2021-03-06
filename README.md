# Adversarial Examples

Just learning about and implementing some simple examples of adversarial examples in the MNIST dataset. 

The code is written using Lasagne and Theano, some of it adapted from Tensorflow examples found elsewhere. 

# Breaking Classifiers

This is a summary to:

[a andrei karpathy's blog](http://karpathy.github.io/2015/03/30/breaking-convnets/) 

[a Ian Goodfellow's paper](https://arxiv.org/pdf/1412.6572v3.pdf)

just so I have something to refer to in the future. 

We train a convnet by sampling data, calculating parameter gradients and updating the parameters. If you feed in an image of a cat, it wiggles the parameters and finds which "wiggles" lead to a lower cost function. For example if one gradient was -3.0, we'd expect that with an lr of 0.0001, then the negative influence on the score would be 0.0003 which is used to perform an update. In a simple example, you can therefore you backpropagation to find the most damaging pixel (i.e. the one with the largest gradient) and nudge it to a different class output. 

It is the linear nature of machine learning algorithms that make them susceptible to these attacks. Even deep learning networks contain largely, linear components, though they are obviously more immune than a softmax classifier for example. However the higher dimensionality of deep learning models may also have a weakness because the large number of inputs into each perceptron means small tweaks in a large number of input nodes can result in a much larger change in the perception. In the case of a simple linear classifier, the score is a dot product of s = W(T)x, where (T) is a transpose function. The gradient of s with respect to x is simply W. To modify an image you take the weight of the desired class and add some fraction to the weights of the desired class.