## SunBERT

Sunbert is a variant of bert trained on Ugandan text data for the tasks of ``Covid/Non Covid`` tweet classification as well as classification of Social Media news articles as either ``Organic, Promotional or Editorial``

Information has become more abundant with the internet. Specifically, people communicate in natural language over social media. Machine learning offers a good way to analyze natural language. We utilized methods from deep learning to analyze text from social media. We build models based on deep learning architectures - Bidirectional Encoder Representations from Transformers (BERT) to perform two downstream tasks: 
1. Analyze posts from social media as promotional, editorial or Organic and
2. To identify tweets as either covid19 related or not. Both tasks show the ability of machine learning to be used to analyze large data and be used to support decision making.

We open source the dataset and source code of our model called SunBERT so that other people can utilize these techniques to their needs.

## Datasets:
We use data from Twitter and Facebook. The dataset contained tweets and posts from both social networks collected through CrowdTangle - a tool from facebook to help follow, analyze and report on what’s happening across social media.

## Models:
BERT (Bidirectional Encoder Representations from Transformers is a deep learning model published by researchers at Google AI. It presented state of the art performance in different Natural Language Processing tasks including Question Answering, Text Classification and Language Modelling. The key technical innovation is that BERT applies a bidirectional training of the Transformer - a popular Attention-based model to language processing.

## Use Cases:
We have shown the application of SunBERT to three use cases, Covid19 classification, News Classification and Language adaptation for Machine Learning research and development. However, SunBERT can be extended to perform other tasks; these include; Question Answering, Masked Language Modelling, Next Sentence Prediction. 
Our code and datasets can be used as a starting point for any of these tasks, with minor modification to the model architecture.
