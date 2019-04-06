---
title: "Neural Machine Translation and Sequence-to-Sequence Models"
date: 2019-02-27T14:44:09-05:00
draft: false
summary: ""
---

What follows are personal notes and any possible insights to help me understand neural machine translation especially in the context of seq2seq models. All content credit goes to Graham Neubig and his tutorial [Neural Machine Translation and Sequence-to-sequence Models: A Tutorial](https://arxiv.org/pdf/1703.01619.pdf) These were done as review for CS 287r.

## n-gram Language Models

The main issue with these is not being able to capture all possible sentence inputs? We can create a simple maximum likelihood estimator by calculating the probabilities for each word $e\_t | e\_{t-1}$, but this is only as strong as if we see these in previous training data examples. N-grams allow us to try to be a bit more flexible.

<!-- MORE TO COME HERE -->

## Log-linear Language Models

We still want to calculate the probability of a word $e\_t$ given context $e\_{t-n+1}^{t-1}. However, we move towards more obviously-looking machine learning models by introducing __features__. We have some feature function $\phi(e\_{t-n+1}^{t-1})$ that takes in context and outputs a real-valued __feature vector__ $\bf x \in \mathbb{R}^N$, that describes the context with $N\$ different features.

In addition to this, we want to use the features to predict probabilities over the output vocabulary $V$, for which we can calculate a score vector $\bf s \in \mathbb{R}^{|V|}$ that corresponds to the likelihood of each word. Looking at our model parameters $\theta$ a bit more explicitly now, we can sort them into those belonging to a **bias vector** $\bf b \in \mathbb{R}^|V|$ and a **weight matrix** $\bf W = \mathbb{R}^{|V| \times N}$. The bias vector tells us how likely a word is overall, and the weight matrix describes the relationship between feature values and scores. We accordingly end up with

$$
\bf s = W \bf x + \bf b
$$

We can then calculate the probabilities for which word to predict (remember our $\bf s$ vector size $= |V|$ = size of our vocab). The scores themselves are arbitrary values, but we just want to figure out in relation to any other word what the probability of our model picking that word should be. Doing this with a softmax activation function, we can then match these probabilities to our data using a **negative log likelihood** (NLL) loss function. We want to find parameters $\bf \theta $ such that the likelihood of our observed training data is maximized, which is the same as minimizing the negative log likelihood mathematically, but easier to calculate computationally.

Some things we can do: adjust learning rate - learning rate decay to drop lr over time; early stopping - note when a model starts overfitting on training data nad stop training then.

## Neural Networks and Feed-forward Language Models

Input embedding group representation?

Neural networks have benefits of being able to learn non-linear representations of the input, which intuitively allow for the capacity to learn more meanings? Seems to be the case that we use embeddings which might learn multiple associations, then feed into standard network architecture.
