---
title: "Notes on NamedTensor"
date: 2019-02-03T16:55:34-05:00
draft: false
summary: ""
---

[NamedTensor](http://nlp.seas.harvard.edu/NamedTensor) is a PyTorch library that tries to fix some broken parts of Tensor. As part of [CS 287R](https://harvard-ml-courses.github.io/cs287-web/) this year, our class gets to be beta-testing guinea pigs for it.\\

While I haven't really worked extensively in PyTorch before, in this post (perhaps the first of many) I'll try to document notes on Tensors and NamedTensor alternatives. Sources will mainly be the [NamedTensor blog post](http://nlp.seas.harvard.edu/NamedTensor) written by Sasha Rush's group, and the [official PyTorch documentation](https://pytorch.org/docs/stable/).

Also as a quick note, while I'm posting this live, it's by no means complete, and the ending quickly degenerates to my usual self-intended note style. That being said, it's nice to have things up. Hopefully will add to this soon.

## Tensor Intro

For some quick background, NamedTensor tries to make working with tensors better. What exactly are tensors? They're sort of like multi-dimensional arrays, often used in deep learning frameworks like Torch or TensorFlow.

For example, we can do
{{< highlight python3 "linenos=inline" >}}
import torch
import numpy as np

ims = torch.tensor(np.load('test*img.npy'))
ims.shape
{{< / highlight >}}
which should output something along the lines of `torch.Size([b, h, w, c])` noting 4 dimensions corresponding to \_batch size*, _height_, _width_, _channels_.

### `torch.transpose(input, dim0, dim1) $\rightarrow$ Tensor`

### Broadcasting

Binary operations can be performed on arrays of the same size on an element-by-element basis.

Broadcasting allows these operations to be performed on arrays of different sizes. For example, if we had

```{python}
import numpy as np
a = np.array([4, 5, 6])
a + 5
```

This would return `array([9, 10, 11])`. Mentally, we can think of broadcasting as converting `5` to the array `[5, 5, 5]`, but this doesn't actually happen in NumPy.

### `View`

View is a method belonging to the `torch.Tensor` object that returns a new tensor in a different shape, dictated by its parameters.

The product of dimensions needs to be consistent for both shapes.

Using `-1` in place of a number can be used to automatically determine what this dimension value should be. This comes in handy in situations where we might not know how many rows we want (or are too lazy to calculate this beforehand), but do know the number of columns.

### `Squeeze`

Called with `torch.squeeze(_input_, _dim_=None, _out=None_) $\rightarrow$ Tensor`

Returns a new tensor with all dimensions of size 1 removed. For example, if the input is of shape $(A \times 1 \times B)$, calling `squeeze` will return a tensor with shape $(A \times B)$.

If `dim` is present, then we only squeeze on that given dimension. For example, if the input is of shape $(A \times 1 \times B)$ and we call `squeeze(input, 0)`, this won't do anything. But calling `squeeze(input)` or `squeeze(input, 1)` will return the "squeezed" tensor of shape $(A \times B)$.

Squeeze can be undone with `unsqueeze`, which takes in an `input` but also requires a `dim`. The method returns a new tensor with `dime` 1 inserted at the specific position, but still shares the input data. Example: with `x = torch.tensor([1, 2, 3])`, `torch.unsqueeze(x, 0)` will output a tensor with `dim` $(1 \times 3)$, and `torch.unsqueeze(x, -1)` will output a tensor with `dim` $(3 \times 1)$.

## NamedField

Documentation notes for implementing `NamedField`.

- `NamedField` inherits from `torchtext.data.Field`
  - Most (all except names?) of its parameters come from this  
    The additional param `name` is used to specify a `names` property, which might be useful? Defaults to `"seqlen",`

#### `torchtext.data.Field`

According to the docs, this defines a datatype and instructions for converting to Tensor

- `Vocab` obj defines set of possible values for elements

Parameters:

- `sequential`: whether datatype should be sequential. Default is `True`.
- `use_vocab`: whether to use vocab object. If False, data should already be numerical. Default is `True`.
- `unk_token`: string token to represent words not in the vocab: Default is `'<unk>'`, but in the 287 pset is set to `None`.

### `torchtext.datasets.SST.splits`

This should create dataset objects for splits of the SST dataset

- We specify which fields are used for the sentence and labels
  - So this determines how we process the dataset
- Params are opinionated for SST, because we only have the sentence and the sentiment / label, so we just need to specify the fields for these

### `torchtext.data.Field.build_vocab`

Constructs the Vocab object for this field from one or more datasets

- Calling `TEXT.build_vocab(train)` goes through all elements in the training set, checks contents for the `TEXT` field (sentences), and registers words to the vocab

`vocab` is an object used to numericalize a field.

- Holds mapping from word to id in `stoi` attribute, and mapping from id to word in `itos` attribute.
  - Can also automatically build an embedding matrix with pretrained embeddings (word2vec)
  - Other params:  
     _ `max_size`: sets the max size of the vocab. Default: `None`.  
     _ `min_freq`: sets lower bound for number of times word needs to appear to be considered in the vocab. Default: `1`.  
    **\_Question**: what is vocab?\_  
    This is the set of words we're allowed to work with

When feeding sentences into the model, we feed a batch of them at a time

- More than one, but all sentences need to be the same size, so any shorter than the longest are padded with `<pad>`

Labels denote a 0 for positive and 1 for negative, which is weird.

<!-- ## List of things not implemented:
nn.torch.functional
* Sigmoid (nn.torch.Sigmoid)
* LogSoftmax (nn.torch.LogSoftmax)
* BCELoss -->
