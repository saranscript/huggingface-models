---

model-index:
- name: wav2vec2-large-xlsr-arabic-common_voice-10_epochs
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-arabic-common_voice-10_epochs

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3581
- Wer: 0.4555

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.1701        | 0.9   | 400  | 3.1599          | 1.0    |
| 0.8933        | 1.8   | 800  | 0.7198          | 0.7877 |
| 0.5849        | 2.7   | 1200 | 0.5046          | 0.6253 |
| 0.3858        | 3.6   | 1600 | 0.4247          | 0.5561 |
| 0.3083        | 4.49  | 2000 | 0.4026          | 0.5251 |
| 0.2556        | 5.39  | 2400 | 0.4010          | 0.5051 |
| 0.2221        | 6.29  | 2800 | 0.3765          | 0.4861 |
| 0.2026        | 7.19  | 3200 | 0.3652          | 0.4794 |
| 0.1996        | 8.09  | 3600 | 0.3627          | 0.4660 |
| 0.1755        | 8.99  | 4000 | 0.3582          | 0.4619 |
| 0.1697        | 9.89  | 4400 | 0.3581          | 0.4555 |


### Framework versions

- Transformers 4.6.0
- Pytorch 1.8.1+cu102
- Datasets 1.6.2
- Tokenizers 0.10.2
