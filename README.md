# Lyrics-Generation-RNN


## Table of Contents  
  * [Authors](#authors)
  * [Introduction](#introduction)
  * [Instructions](#instructions)
  * [Dataset Analysis](#dataset-analysis)
  * [Code Design](#code-design)
  * [Melody Feature Integration](#melody-feature-integration)
  * [Architecture](#architecture)
  * [Results Evaluation](#results-evaluation)
  * [Full Experimental Setup](#full-experimental-setup)
  * [Analysis of how the Seed and Melody Effects the Generated Lyrics](#analysis-of-how-the-seed-and-melody-effects-the-generated-lyrics)
  
## Authors
* **Chen Harel** - [Chen Harel](https://github.com/Chenharelz)
* **Omer Rosenberg** - [Omer Rosenberg](https://github.com/Chenharelz)

## Introduction
In this assignment, we were tasked with creating a Recurrent Neural Network that can learn song lyrics and their melodies and then given a melody and a few words to start with, predict the rest of the song. This is essentially done by generating new words for the song and attempting to be as “close” as possible to the original lyrics. However, this is quite subjective leading the evaluation of generated words to use imaginative methods. For the training phase, however, we used Crossed Entropy loss.
The melody files and lyrics for each song were given to us and the train / test sets were predefined. 20% of the training data was used as a validation set in order to track our progress between training iterations.

We implemented this using an LSTM network. LSTMs have proven in the past to be successful in similar tasks because of their ability to remember previous data, which in our case is relevant because each lyric depends on the words (and melody) that preceded it.
The network receives as input a sequence of lyrics and predicts the next word to appear. The length of this sequence greatly affects the network’s predicting abilities since 5 words in a row work much better than just a single word. We tried using different values to see how this changes the accuracy of the model. During the training phase, sequences from the actual lyrics are fed into the network to train. After fitting the model, we can generate the lyrics for a whole song by beginning with an initial “seed” which is a sequence of words, predicting a word and then using it to advance the sequence like a moving window.
