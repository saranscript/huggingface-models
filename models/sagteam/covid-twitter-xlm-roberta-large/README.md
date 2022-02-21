# COVID-twitter-XLM-Roberta-large 

## Model description

This is a model based on the [XLM-RoBERTa large](https://huggingface.co/xlm-roberta-large) topology (provided by Facebook, see original [paper](https://arxiv.org/abs/1911.02116)) with additional training on a corpus of unmarked tweets.

For more details, please see, our [GitHub repository](https://github.com/sag111/COVID-19-tweets-Russia).


## Training data

We formed a corpus of unlabeled twitter messages. 

The data on keyword "covid" was expanded with texts containing  other words often occurred in hashtags on the Covid-19 pandemic: "covid", "stayhome", and "coronavirus" (hereinafter, these are translations of Russian words into English). 

Separately, messages were collected from Twitter users from large regions of Russia. The search was provided using different word forms of 58 manually selected keywords on Russian related to the topic of coronavirus infection (including: "PCR", "pandemic", "self-isolation", etc.).

The unlabeled corpus includes all unique Russian-language tweets from the collected data (>1M tweets). Since modern language models are usually multilingual, about 1M more tweets in other languages were added to this corpus using filtering procedures described above. Thus, in the unlabeled part of the collected data, there were about 2 million messages.


### BibTeX entry and citation info

Our GitHub repository: https://github.com/sag111/COVID-19-tweets-Russia

If you have found our results helpful in your work, feel free to cite our publication and this repository as:

```
coming soon
```
