---
thumbnail: "url to a thumbnail used in social sharing"
tags:
- graph neural networks
license:
- cc0-1.0
---

## Keras Implementation of Graph Attention Networks for Node Classification 🕸

This repo contains the model and the notebook [to this Keras example on Graph Attention Networks for Node Classification](https://keras.io/examples/graph/gat_node_classification/).

Full credits to: [Alexander Kensert](https://github.com/akensert)

## Background Information 
Graph neural networks is the preferred neural network architecture for processing data structured as graphs (for example, social networks or molecule structures), yielding better results than fully-connected networks or convolutional networks.

This tutorial implements a specific graph neural network known as a [Graph Attention Network (GAT)](https://arxiv.org/abs/1710.10903) to predict labels of scientific papers based on the papers they cite (using the [Cora dataset](https://linqs.soe.ucsc.edu/data)).

References
For more information on GAT, see the original paper [Graph Attention Networks](https://arxiv.org/abs/1710.10903) as well as [DGL's Graph Attention Networks](https://docs.dgl.ai/en/0.4.x/tutorials/models/1_gnn/9_gat.html) documentation.
