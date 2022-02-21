---
language:
- pt
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- pt
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: wav2vec2-xls-r-pt-cv7
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-pt-cv7

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - PT dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7280
- Wer: 0.4698

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- training_steps: 40000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| 1.7142        | 10.42  | 2000  | 0.8951          | 0.7325 |
| 1.5703        | 20.83  | 4000  | 0.8202          | 0.6916 |
| 1.5028        | 31.25  | 6000  | 0.8049          | 0.6988 |
| 1.4598        | 41.66  | 8000  | 0.7391          | 0.6347 |
| 1.3511        | 52.08  | 10000 | 0.6785          | 0.5926 |
| 1.3271        | 62.5   | 12000 | 0.7235          | 0.6334 |
| 1.2039        | 72.91  | 14000 | 0.6596          | 0.5693 |
| 1.1816        | 83.33  | 16000 | 0.6696          | 0.5633 |
| 1.1137        | 93.75  | 18000 | 0.6595          | 0.5650 |
| 1.0593        | 104.17 | 20000 | 0.6639          | 0.5315 |
| 1.0082        | 114.58 | 22000 | 0.6718          | 0.5234 |
| 0.9576        | 125.0  | 24000 | 0.6703          | 0.5224 |
| 0.9187        | 135.42 | 26000 | 0.6574          | 0.5002 |
| 0.8745        | 145.83 | 28000 | 0.6852          | 0.4990 |
| 0.8418        | 156.25 | 30000 | 0.6893          | 0.4877 |
| 0.7657        | 166.66 | 32000 | 0.7027          | 0.4842 |
| 0.749         | 177.08 | 34000 | 0.7161          | 0.4794 |
| 0.7182        | 187.5  | 36000 | 0.7300          | 0.4795 |
| 0.6766        | 197.91 | 38000 | 0.7279          | 0.4715 |
| 0.6634        | 208.33 | 40000 | 0.7280          | 0.4698 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
