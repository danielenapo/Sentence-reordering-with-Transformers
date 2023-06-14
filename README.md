# Sentence Reordering using Transformer networks
This task was the subject of my Deep Learning's exam of 02/06/23 of the Master's degree course in Artificial Intelligence of the University of Bologna.<br>
The purpose of this project is to take in input a sequence of words corresponding to a random permutation of a given english sentence, and reconstruct the original sentence. <br>

## Dataset
The dataset was taken from a Wikipedia dataset, made of 100k sentences of max 30 words. The vocabulary size is 10k words (the most common in the dataset).<br>
The original sentences were randomly shuffled, the purpose was to reorder them as best as possible, to maximize a custom-defined score given by the professor.

## Constraints
- No pretrained model can be used.
- The neural network models should have less the 20M parameters.

## Method
In this work, I propose a Transformer model for the task of sentence shuffling, which can generate shuffled sentences that preserve the meaning and grammaticality of the original sentences. I compare the performance of the proposed Transformer model with other alternative methods that use Seq2Seq models or positional vectors.
