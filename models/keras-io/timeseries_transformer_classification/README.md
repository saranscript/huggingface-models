---
tags:
- time-series
- transformers
dataset:
- FordA
license: cc0-1.0
---
## Timeseries classification with a Transformer model on the 🤗Hub! 
Full credits go to [Theodoros Ntakouris](https://github.com/ntakouris).

This repository contains the model from [this notebook on time-series classification using the attention mechanism](https://keras.io/examples/timeseries/timeseries_classification_transformer/). 

The dataset we are using here is called [FordA](http://www.j-wichard.de/publications/FordPaper.pdf). The data comes from the UCR archive. The dataset contains 3601 training instances and another 1320 testing instances. Each timeseries corresponds to a measurement of engine noise captured by a motor sensor. For this task, the goal is to automatically detect the presence of a specific issue with the engine. The problem is a balanced binary classification task. 