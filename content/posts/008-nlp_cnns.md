---
title: "CNNs for NLP"
date: 2019-02-02T17:25:11-05:00
draft: false
summary: "An intuitive look at one 3-letter acronym ML concept applied to another"
---

I've always believed that a better way to learn things is to explain them to others. It's part of why I teach in college. When I started thinking about the merits of a blog, writing about more technical things as a way to ground concepts for myself was definitely a plus. \\

This semester, I'm taking [CS 287R](https://harvard-ml-courses.github.io/cs287-web/), a class at Harvard that deals with NLP and increasingly deep learning. Aside from this class, there are also

Think of filters as ways to build up higher-level features, which can then aid in classification at the end

# Location Invariance

- Convolutions just slide over entire image. Doesn't matter where objects occur. Pooling

# Compositionality

Filters compose local patch of lower-level features to higher level ones. Pixels $\rightarrow$ edges $\rightarrow$ shapes $\rightarrow$ objects

Input for NLP = sentences, documents in a matrix.

- Each row is one token (word / character)
- Vectors are word embeddings (low-dimension representations) or one-hot vectors (word is index in vocab)
- e.g. 10 word sentence w/ 100D embedding $\rightarrow 10 \times 100$ as input

NLP, use filters that are same width as image. Height / region size is based on number of words (2 - 5) typical.

- Filters are not usually square then. Also can be variable height. \* Feature maps will be (height $\times$ 1). Example:

$$7 \times 5 \rightarrow (2 \times 5, 3 \times 5, 4 \times 5) \rightarrow (6 \times 1, 5 \times 1, 4 \times 1) $$

Then max pool $\rightarrow$ takes the largest value. Then concatenate. Final softmax takes this feature, uses it to classify.

Location invariance and compositionality don't apply obviously?

- It does matter where words are. Also words build up, not obvious how so like pixels to edges.
- CNNs still work? Motivation for RNNs

Why CNNs

- Very fast, efficient in representation. Conv filters leran good reps automatically w/o represented entire vocab

## CNN parameters

### Zero Padding

Can help preserve shape of feature map. In general, output size is
$$n\_{\text{out}} = (n\_{\text{in}} - n\_{\text{filter size}} + 2n\_{\text{padding_size}}) / n\_{\text{stride}} + 1$$

- Especially apparent around the edges. How to capture them?

### Stride size

Larger stride leads to fewer applications of filter and smaller output.

- Larger stride size helps build model similar to RNN / looks like a tree?
- In practice stride is 1

### Pooling

Subsample their input. Common: max operation to each filter. Can also just pool over a window.

- Fixed size output matrix (req. for classification)
  - 1000 filters, with max pooling to each $\rightarrow$ 1000 output (regardless of filter or input size)

Max pool helps retain info for if feature appeared in sentence

- Lose info on where it appeared. This is still useful, but tradeoff. (Sim. to bag of words). Lose global info about locality, but keep local info caught by filters.

### Channels

Different views of input data (r, g, b) for images.

- Separate channels could be useful for different embeddings.

---

References:

1. [Understanding Convolutional Neural Networks for NLP - Denny Britz]
2. Anecdote shared by Kanjun Qin, founder at Sourceress.
