---
tags:
- generated_from_trainer
datasets:
- null
metrics:
- rouge
model_index:
- name: bart-CNN-Dailymail-summ
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    metric:
      name: Rouge1
      type: rouge
      value: 16.856
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-CNN-Dailymail-summ

This model is a fine-tuned version of [mwesner/bart-mlm](https://huggingface.co/mwesner/bart-mlm) on the CNN/Dailymail dataset.
It achieves the following results on the evaluation set:
- Loss: 2.8336
- Rouge1: 16.856
- Rouge2: 2.8599
- Rougel: 13.0133
- Rougelsum: 15.7707
- Gen Len: 20.0

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
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 3.3997        | 0.56  | 5000  | 3.5252          | 10.2679 | 0.6562 | 8.9324  | 9.9688    | 19.9981 |
| 3.0884        | 1.11  | 10000 | 3.1885          | 11.2165 | 1.3817 | 9.1731  | 10.6776   | 20.0    |
| 2.8898        | 1.67  | 15000 | 2.9911          | 15.8473 | 2.4004 | 12.2613 | 14.8364   | 20.0    |
| 2.7702        | 2.23  | 20000 | 2.8708          | 16.778  | 2.7622 | 12.9313 | 15.7391   | 20.0    |
| 2.7615        | 2.79  | 25000 | 2.8336          | 16.856  | 2.8599 | 13.0133 | 15.7707   | 20.0    |


### Framework versions

- Transformers 4.8.1
- Pytorch 1.9.0
- Datasets 1.11.0
- Tokenizers 0.10.3
