---
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: sbert_large-finetuned-sent_in_news_sents_3lab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sbert_large-finetuned-sent_in_news_sents_3lab

This model is a fine-tuned version of [sberbank-ai/sbert_large_nlu_ru](https://huggingface.co/sberbank-ai/sbert_large_nlu_ru) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9443
- Accuracy: 0.8580
- F1: 0.6199

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 17

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 264  | 0.6137          | 0.8608   | 0.3084 |
| 0.524         | 2.0   | 528  | 0.6563          | 0.8722   | 0.4861 |
| 0.524         | 3.0   | 792  | 0.7110          | 0.8494   | 0.4687 |
| 0.2225        | 4.0   | 1056 | 0.7323          | 0.8608   | 0.6015 |
| 0.2225        | 5.0   | 1320 | 0.9604          | 0.8551   | 0.6185 |
| 0.1037        | 6.0   | 1584 | 0.8801          | 0.8523   | 0.5535 |
| 0.1037        | 7.0   | 1848 | 0.9443          | 0.8580   | 0.6199 |
| 0.0479        | 8.0   | 2112 | 1.0048          | 0.8608   | 0.6168 |
| 0.0479        | 9.0   | 2376 | 0.9757          | 0.8551   | 0.6097 |
| 0.0353        | 10.0  | 2640 | 1.0743          | 0.8580   | 0.6071 |
| 0.0353        | 11.0  | 2904 | 1.1216          | 0.8580   | 0.6011 |


### Framework versions

- Transformers 4.11.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
