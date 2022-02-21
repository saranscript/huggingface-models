---

language:
- en
tags:
- t5
- qa
- askscience
- lfqa
- information retrieval
datasets:
- eli5
metrics:
- rouge
widget:
- text: "why aren't there more planets in our solar system?"
  example_title: "solar system"
- text: "question: what is a probability distribution? context: I am just learning about statistics."
  example_title: "probability distribution"
- text: "question: how does exercise help us lose weight? context: I started working out two weeks ago and already feel a lot better, and started to think about it and became deeply confused."
  example_title: "pumpen"
- text: "what is a neural network?"
  example_title: "deep learning"
- text: "How can computers understand human language?"
  example_title: "NLP"
  
inference:
  parameters:
    max_length: 64
    no_repeat_ngram_size: 2
    encoder_no_repeat_ngram_size: 3
    repetition_penalty: 3.51
    length_penalty: 0.8
    num_beams: 4
    early_stopping: True
    
---

# t5 - base- askscience

- [t5-v1_1](https://huggingface.co/google/t5-v1_1-base) trained on the entirety of the _askscience_ sub-section of the eli5 dataset for one epoch.
- compare to bart on eli5 [here](https://huggingface.co/yjernite/bart_eli5)
- note that for the inference API, the model is restricted to outputting 64 tokens - by using the model in python with the transformers library, you can get longer outputs.

## training 

- for inputs, the model was presented with the post title and the post selftext encoded as: `question: <post title> context: <post selftext>`. You may see better results if queries are posed in this fashion.
- The top two replies were aggregated and presented to the model as the output text.
- Training for longer will be explored, but given that the dataset has 127k examples and the loss flatlines at 0.5 epochs so this model should be fairly viable.