---
tags:
- video-prediction
- moving-mnist
- video-to-video
license: cc0-1.0
---
## Tensorflow Keras Implementation of Next-Frame Video Prediction with Convolutional LSTMs 📽️

This repo contains the models and the notebook [on How to build and train a convolutional LSTM model for next-frame video prediction](https://keras.io/examples/vision/conv_lstm/).

Full credits to [Amogh Joshi](https://github.com/amogh7joshi)

## Background Information
The [Convolutional LSTM](https://papers.nips.cc/paper/2015/file/07563a3fe3bbe7e3ba84431ad9d055af-Paper.pdf) architectures bring together time series processing and computer vision by introducing a convolutional recurrent cell in a LSTM layer. This model uses the Convolutional LSTMs in an application to next-frame prediction, the process of predicting what video frames come next given a series of past frames.

![preview](https://keras.io/img/examples/vision/conv_lstm/conv_lstm_13_0.png)

## Training Dataset
This model was trained on the [Moving MNIST dataset](http://www.cs.toronto.edu/~nitish/unsupervised_video/).

For next-frame prediction, our model will be using a previous frame, which we'll call `f_n`, to predict a new frame, called `f_(n + 1)`. To allow the model to create these predictions, we'll need to process the data such that we have "shifted" inputs and outputs, where the input data is frame `x_n`, being used to predict frame `y_(n + 1)`.

![result](https://i.imgur.com/UYMTsw7.gif)
