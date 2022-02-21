---
tags:
- generated_from_trainer
model-index:
- name: bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets

This model is a further pre-trained version of [vinai/bertweet-covid19-base-uncased](https://huggingface.co/vinai/bertweet-covid19-base-uncased) on masked language modeling using [a kaggle dataset](https://www.kaggle.com/kaushiksuresh147/covidvaccine-tweets) with tweets up until early December. 
It achieves the following results on the evaluation set (15% from the dataset randomly selected to serve as a test set):
- Loss: 1.5089
- Perplexity: 4.64

To use the model, use the inference API.

Alternatively, to run locally
```
from transformers import pipeline
model = "justinqbui/bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets"
pipe = pipeline("fill-mask", model = model)
seq = "covid vaccines are <mask> and effective"
pipe(seq)
```

## Model description

This model is a further pretrained version of bertweet, which both follow objectives in the [RoBERTa paper](https://arxiv.org/pdf/1907.11692.pdf). While bertweet was only trained with 23M tweets until September, 2020, this model was further pre-trained using 300k tweets with #CovidVaccine. 

The tokenizer requires the emoji library to be installed.
```
!pip install nltk emoji
```

## Intended uses & limitations

The intended use of this model is for fine-tuning on a downstream task on tasks that are closely related to covid and covid vaccines. This model has many potential biases and limitations, since the model is trained on public tweets, it is bound to recreate biases that people tweet. 

In order to load the model and tokenizer, run 
```
from transformers import AutoTokenizer, AutoModelForMaskedLM

tokenizer = AutoTokenizer.from_pretrained("justinqbui/bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets")

model = AutoModelForMaskedLM.from_pretrained("justinqbui/bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets")

```


## Training and evaluation data

This model was further pre-trained on 300k tweets containing #covidvaccines from this [kaggle dataset](https://www.kaggle.com/kaushiksuresh147/covidvaccine-tweets). The evaluation set was 15% of the tweets that were held out from the training data. 

## Training procedure

See the training notebook found [here]().

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.5775        | 1.0   | 8931  | 1.5852          |
| 1.5715        | 2.0   | 17862 | 1.5701          |
| 1.5394        | 3.0   | 26793 | 1.5089          |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
