# MentalRoBERTa

[MentalRoBERTa](https://arxiv.org/abs/2110.15621) is a model initialized with RoBERTa-Base (`cased_L-12_H-768_A-12`) and trained with mental health-related posts collected from Reddit. 

We follow the standard pretraining protocols of BERT and RoBERTa with [Huggingface’s Transformers library](https://github.com/huggingface/transformers).

We use four Nvidia Tesla v100 GPUs to train the two language models. We set the batch size to 16 per GPU, evaluate every 1,000 steps, and train for 624,000 iterations. Training with four GPUs takes around eight days. 

## Usage
Load the model via [Huggingface’s Transformers library](https://github.com/huggingface/transformers):
```
from transformers import AutoTokenizer, AutoModel
tokenizer = AutoTokenizer.from_pretrained("mental/mental-roberta-base")
model = AutoModel.from_pretrained("mental/mental-roberta-base")
```

## Paper

For more details, refer to the paper [MentalBERT: Publicly Available Pretrained Language Models for Mental Healthcare](https://arxiv.org/abs/2110.15621).

```
@article{ji2021mentalbert,
  title   = {{MentalBERT: Publicly Available Pretrained Language Models for Mental Healthcare}},
  author  = {Shaoxiong Ji and Tianlin Zhang and Luna Ansari and Jie Fu and Prayag Tiwari and Erik Cambria},
  year    = {2021},
  journal = {arXiv preprint arXiv:2110.15621}
}
```

## Social Impact
We train and release masked language models for mental health to facilitate the automatic detection of mental disorders in online social content for non-clinical use. 
The models may help social workers find potential individuals in need of early prevention. 
However, the model predictions are not psychiatric diagnoses. 
We recommend anyone who suffers from mental health issues to call the local mental health helpline and seek professional help if possible.

Data privacy is an important issue, and we try to minimize the privacy impact when using social posts for model training.
During the data collection process, we only use anonymous posts that are manifestly available to the public. 
We do not collect user profiles even though they are also manifestly public online. 
We have not attempted to identify the anonymous users or interact with any anonymous users. 
The collected data are stored securely with password protection even though they are collected from the open web.
There might also be some bias, fairness, uncertainty, and interpretability issues during the data collection and model training. 
Evaluation of those issues is essential in future research. 