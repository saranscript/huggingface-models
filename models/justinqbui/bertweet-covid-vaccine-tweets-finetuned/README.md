---
tags:

model-index:
- name: bertweet-covid--vaccine-tweets-finetuned
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets

This model is a fine-tuned version of [justinqbui/bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets](https://huggingface.co/justinqbui/bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets) which was finetuned by using [this google fact check](https://huggingface.co/datasets/justinqbui/covid_fact_checked_google_api) ~3k dataset size and webscraped data from [polifact covid info](https://huggingface.co/datasets/justinqbui/covid_fact_checked_polifact) ~ 1200 dataset size and ~1200 tweets pulled from the CDC with tweets containing the words covid or vaccine.
It achieves the following results on the evaluation set (20% from the dataset randomly shuffled and selected to serve as a test set):
- Validation Loss: 0.267367
- Accuracy: 91.1370%

To use the model, use the inference API.

Alternatively, to run locally
```
from transformers import AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("justinqbui/bertweet-covid-vaccine-tweets-finetuned")

model = AutoModelForSequenceClassification.from_pretrained("justinqbui/bertweet-covid-vaccine-tweets-finetuned")
```

## Model description

This model is a fine-tuned version of pretrained version [justinqbui/bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets](https://huggingface.co/justinqbui/bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets). Click on [this](https://huggingface.co/justinqbui/bertweet-covid19-base-uncased-pretraining-covid-vaccine-tweets) to see how the pre-training was done.

This model was fine-tuned with a dataset of ~5500. A web scraper was used to scrape polifact and a script was used to pull from the google fact check API. Because ~80% of both these datasets were either false or misleading, I pulled about ~1200 tweets from the CDC related to covid and labelled them as true. ~30% of this dataset is considered true and the rest false or misleading. Please see the published datasets above for more detailed information.

The tokenizer requires the emoji library to be installed.
```
!pip install nltk emoji
```

## Intended uses & limitations

The intended use of this model is to detect if the contents of a covid tweet is potentially false or misleading. This model is not an end all be all. It has many limitations. For example, if someone makes a post containing an image, but has attached a satirical image, this model would not be able to distinguish this. If a user links a website, the tokenizer allocates a special token for links, meaning the contents of the linked website is completely lost. If someone tweets a reply, this model can't look at the parent tweets, and will lack context.

This model's dataset relies on the crowd-sourcing annotations being accurate. This data is only accurate of up until early December 2021. For example, it probably wouldn't do very ell with tweets regarded the new omicron variant.

Example true inputs:
```
Covid vaccines are safe and effective. -> 97% true
Vaccinations are safe and help prevent covid. -> 97% true
```

Example false inputs:
```
Covid vaccines will kill you. -> 97% false
covid vaccines make you infertile. -> 97% false
```



## Training and evaluation data

This model was finetuned by using [this google fact check](https://huggingface.co/datasets/justinqbui/covid_fact_checked_google_api) ~3k dataset size and webscraped data from [polifact covid info](https://huggingface.co/datasets/justinqbui/covid_fact_checked_polifact) ~ 1200 dataset size and ~1200 tweets pulled from the CDC with tweets containing the words covid or vaccine.


### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-5
- train_batch_size: 128
- eval_batch_size: 128
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0
- 

### Training results

| Training Loss | Epoch | Validation Loss | Accuracy |
|:-------------:|:-----:|:---------------:|:--------:|
| 0.435500      | 1.0   | 0.401900        | 0.906893 |
| 0.309700      | 2.0   | 0.265500        | 0.907789 |
| 0.266200      | 3.0   | 0.216500        | 0.911370 |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
