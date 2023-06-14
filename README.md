# Sentence Reordering using Transformer networks
This task was the subject of my Deep Learning's exam of 02/06/23 of the Master's degree course in Artificial Intelligence of the University of Bologna.<br>
The purpose of this project is to take in input a sequence of words corresponding to a random permutation of a given english sentence, and reconstruct the original sentence. 

In this work, I propose a Transformer model for the task of sentence shuffling, which can generate shuffled sentences that preserve the meaning and grammaticality of the original sentences. I compare the performance of the proposed Transformer model with other alternative methods that use Seq2Seq models or positional vectors.

## Dataset
The dataset was taken from a Wikipedia dataset, made of 100k sentences of max 30 words. The vocabulary size is 10k words (the most common in the dataset).<br>
The processed dataset consists of around 120k ordered sentences.

## Metrics
The quality of the results will be measured according to the following metric:
1. look for the longest substring w between s and p
2. compute $|w|/max(|s|,|p|)$
If the match is exact, the score is 1.

## Constraints
- No pretrained model can be used.
- The neural network model should have less than 20M parameters.

# The Model
For this task, it was implemented a Transformer model, following as much as possible the implementation described in the original paper _["Attention is all you need"](https://arxiv.org/pdf/1706.03762.pdf)_ (Vaswani et al., 2017).

<img src="https://github.com/danielenapo/Sentence-reordering-with-Transformers/assets/33985608/e92492f2-f7b2-482a-89fe-f6346dea61de" height="500"/>

## Hyperparameters
Here are some of the most important hyperparameters and their meaning:

- `embedding_dim` -> **256** (The dimensionality of the model's hidden states and embeddings)
- `num_heads` -> **10** (The number of attention heads used in the multi-head attention mechanism)
- `num_layers` -> **5** (The number of layers in the encoder and decoder stacks)
- `intermediate_dim` -> **1640** (The number of units in the feedforward sublayer of the encoder and decoder layers)
- `dropout_rate` -> **0.1** (The dropout rate used in the encoder and decoder layers)
- `batch_size` -> **512** (The number of samples processed in each training batch)
- `optimizer` -> **Adam**, with the same parameters of the paper (The optimizer used to train the model)
- `learning_rate` -> The learning rate followed a custom schedule, taken by the original paper
- `warmup_steps` -> **1000** (The number of warmup steps used in the learning rate schedule)

**Total trainable parameters: 19,990,034**

# Results
After computing autoregressive inference for 1000 random test set datapoints, the average score was:<br> **0.4856412631262165**.

### Example of prediction
note: the test shuffled sentence is omitted but it's just random shuffles of the original sentence words

- **test sentence:** _"on august 6 1928 in pittsburgh pennsylvania"_
- **prediction:** _"pittsburgh pennsylvania on august 6 1928"_
- **score:** 0.5348837209302325


