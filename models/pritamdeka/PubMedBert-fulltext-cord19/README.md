---
license: mit
tags:
- generated_from_trainer
datasets:
- pritamdeka/cord-19-fulltext
metrics:
- accuracy
model-index:
- name: pubmedbert-fulltext-cord19
  results:
  - task:
      name: Masked Language Modeling
      type: fill-mask
    dataset:
      name: pritamdeka/cord-19-fulltext
      type: pritamdeka/cord-19-fulltext
      args: fulltext
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.7175316733550737
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pubmedbert-fulltext-cord19

This model is a fine-tuned version of [microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext) on the pritamdeka/cord-19-fulltext dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2667
- Accuracy: 0.7175

## Model description

The model has been trained using a maximum train sample size of 300K and evaluation size of 25K due to GPU limitations

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 10000
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 1.7985        | 0.27  | 5000  | 1.2710          | 0.7176   |
| 1.7542        | 0.53  | 10000 | 1.3359          | 0.7070   |
| 1.7462        | 0.8   | 15000 | 1.3489          | 0.7034   |
| 1.8371        | 1.07  | 20000 | 1.4361          | 0.6891   |
| 1.7102        | 1.33  | 25000 | 1.3502          | 0.7039   |
| 1.6596        | 1.6   | 30000 | 1.3341          | 0.7065   |
| 1.6265        | 1.87  | 35000 | 1.3228          | 0.7087   |
| 1.605         | 2.13  | 40000 | 1.3079          | 0.7099   |
| 1.5731        | 2.4   | 45000 | 1.2986          | 0.7121   |
| 1.5602        | 2.67  | 50000 | 1.2929          | 0.7136   |
| 1.5447        | 2.93  | 55000 | 1.2875          | 0.7143   |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
