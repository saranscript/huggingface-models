---
tags:
- generated_from_trainer
model-index:
- name: timit-demo-wavlm-large
---



# timit-demo-wavlm-large

This model is a fine-tuned version of [microsoft/wavlm-large](https://huggingface.co/microsoft/wavlm-large) on the [Timit dataset](https://huggingface.co/datasets/timit_asr).

It achieves the following results on the evaluation set:
- Loss: 0.3784
- Wer: 0.2746

## Model description

Fine tunes `microsoft/wavlm-large` on the [Timit dataset](https://huggingface.co/datasets/timit_asr) for 100 epochs to see results / compare to wav2vec2.

## Intended uses & limitations

This should be used primarily for benchmarking / comparison purposes, the Timit dataset **does not** generalize well as you will quickly see from testing inference API.

## Training and evaluation data

[Timit](https://huggingface.co/datasets/timit_asr) using standard splits.

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 4.2656        | 4.0   | 500   | 2.9768          | 1.0    |
| 1.8004        | 8.0   | 1000  | 0.6151          | 0.6046 |
| 0.5425        | 12.0  | 1500  | 0.3802          | 0.4330 |
| 0.2647        | 16.0  | 2000  | 0.3015          | 0.3587 |
| 0.1697        | 20.0  | 2500  | 0.3225          | 0.3439 |
| 0.1164        | 24.0  | 3000  | 0.3162          | 0.3277 |
| 0.0951        | 28.0  | 3500  | 0.3102          | 0.3098 |
| 0.076         | 32.0  | 4000  | 0.3201          | 0.3052 |
| 0.0647        | 36.0  | 4500  | 0.3346          | 0.2990 |
| 0.0544        | 40.0  | 5000  | 0.3323          | 0.2955 |
| 0.0515        | 44.0  | 5500  | 0.3377          | 0.2898 |
| 0.045         | 48.0  | 6000  | 0.3268          | 0.2881 |
| 0.0393        | 52.0  | 6500  | 0.3404          | 0.2822 |
| 0.0364        | 56.0  | 7000  | 0.3337          | 0.2805 |
| 0.0329        | 60.0  | 7500  | 0.3485          | 0.2823 |
| 0.0327        | 64.0  | 8000  | 0.3362          | 0.2795 |
| 0.0287        | 68.0  | 8500  | 0.3768          | 0.2845 |
| 0.0284        | 72.0  | 9000  | 0.3736          | 0.2805 |
| 0.0292        | 76.0  | 9500  | 0.3761          | 0.2806 |
| 0.0251        | 80.0  | 10000 | 0.3735          | 0.2768 |
| 0.0224        | 84.0  | 10500 | 0.3741          | 0.2773 |
| 0.0232        | 88.0  | 11000 | 0.3760          | 0.2772 |
| 0.0213        | 92.0  | 11500 | 0.3729          | 0.2740 |
| 0.0204        | 96.0  | 12000 | 0.3722          | 0.2739 |
| 0.0199        | 100.0 | 12500 | 0.3784          | 0.2746 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
