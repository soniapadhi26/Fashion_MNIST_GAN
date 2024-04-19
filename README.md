# Fashion-MNIST-GAN-Keras
- Dataset used :- https://keras.io/api/datasets/fashion_mnist/
# Generative Adversal Networks (GAN's)

### Introduction

- Generative Adversarial Networks (GANs) are a powerful class of neural networks that are used for unsupervised learning.
- It was developed and introduced by Ian J. Goodfellow in 2014.
- GANs are basically made up of a system of two competing neural network models which compete with each other and are able to analyze, capture and copy the variations within a dataset.

- GANs are generative models: they create new data instances that resemble your training data.

For example, GANs can create images that look like photographs of human faces, even though the faces don't belong to any real person.

What does "generative" mean in the name "Generative Adversarial Network"? "Generative" describes a class of statistical models that contrasts with discriminative models.
- Generative models can generate new data instances.
- Discriminative models discriminate between different kinds of data instances.
- A generative model could generate new photos of animals that look like real animals, while a discriminative model could tell a dog from a cat. GANs are just one kind of generative model.

More formally, given a set of data instances X and a set of labels Y:
- Generative models capture the joint probability p(X, Y), or just p(X) if there are no labels.
- Discriminative models capture the conditional probability p(Y | X).
- A generative model includes the distribution of the data itself, and tells you how likely a given example is.

For example, models that predict the next word in a sequence are typically generative models (usually much simpler than GANs) because they can assign a probability to a sequence of words.

A discriminative model ignores the question of whether a given instance is likely, and just tells you how likely a label is to apply to the instance.

There are many kinds of generative model. GANs are just one kind of generative model.
### How does GANs work?

Generative Adversarial Networks (GANs) can be broken down into three parts:

- Generative: To learn a generative model, which describes how data is generated in terms of a probabilistic model.
- Adversarial: The training of a model is done in an adversarial setting.
- Networks: Use deep neural networks as the artificial intelligence (AI) algorithms for training purpose.

In GANs, there is a generator and a discriminator.
- The Generator generates fake samples of data(be it an image, audio, etc.) and tries to fool the Discriminator.
- The Discriminator, on the other hand, tries to distinguish between the real and fake samples.
- The Generator and the Discriminator are both Neural Networks and they both run in competition with each other in the training phase.
- The steps are repeated several times and in this, the Generator and Discriminator get better and better in their respective jobs after each repetition. The working can be visualized by the diagram given below:

<img src = https://media.geeksforgeeks.org/wp-content/uploads/gans_gfg.jpg>

- Here, the generative model captures the distribution of data and is trained in such a manner that it tries to maximize the probability of the Discriminator in making a mistake.
- The Discriminator, on the other hand, is based on a model that estimates the probability that the sample that it got is received from the training data and not from the Generator.

The GANs are formulated as a minimax game, where the Discriminator is trying to minimize its reward V(D, G) and the Generator is trying to minimize the Discriminator’s reward or in other words, maximize its loss. It can be mathematically described by the formula below:

<img src = https://media.geeksforgeeks.org/wp-content/uploads/g22-1.png>

where,
- G = Generator
- D = Discriminator
- Pdata(x) = distribution of real data
- P(z) = distribution of generator
- x = sample from Pdata(x)
- z = sample from P(z)
- D(x) = Discriminator network
- G(z) = Generator network

So, basically, training a GAN has two parts:

- Part 1: The Discriminator is trained while the Generator is idle. In this phase, the network is only forward propagated and no back-propagation is done. The Discriminator is trained on real data for n epochs, and see if it can correctly predict them as real. Also, in this phase, the Discriminator is also trained on the fake generated data from the Generator and see if it can correctly predict them as fake.

- Part 2: The Generator is trained while the Discriminator is idle. After the Discriminator is trained by the generated fake data of the Generator, we can get its predictions and use the results for training the Generator and get better from the previous state to try and fool the Discriminator.

The above method is repeated for a few epochs and then manually check the fake data if it seems genuine. If it seems acceptable, then the training is stopped, otherwise, its allowed to continue for few more epochs.
