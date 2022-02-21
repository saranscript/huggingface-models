---
language:
- hy-AM
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-1b-hy-cv
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice hy-AM
      args: hy-AM
    metrics:
      - type: wer
        value: 0.2755659640905542
        name: WER LM
      - type: cer
        value: 0.08659585230146687
        name: CER LM
---


<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - HY-AM dataset.
It achieves the following results on the evaluation set:
- Loss: **0.4521**
- Wer: **0.5141**
- Cer: **0.1100**
- Wer+LM: **0.2756**
- Cer+LM: **0.0866**

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 8e-05
- train_batch_size: 16
- eval_batch_size: 64
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.98) and epsilon=1e-08
- lr_scheduler_type: tristage
- lr_scheduler_ratios: [0.1, 0.4, 0.5]
- training_steps: 1400
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:------:|:----:|:---------------:|:------:|:------:|
| 6.1298        | 19.87  | 100  | 3.1204          | 1.0    | 1.0    |
| 2.7269        | 39.87  | 200  | 0.6200          | 0.7592 | 0.1755 |
| 1.4643        | 59.87  | 300  | 0.4796          | 0.5921 | 0.1277 |
| 1.1242        | 79.87  | 400  | 0.4637          | 0.5359 | 0.1145 |
| 0.9592        | 99.87  | 500  | 0.4521          | 0.5141 | 0.1100 |
| 0.8704        | 119.87 | 600  | 0.4736          | 0.4914 | 0.1045 |
| 0.7908        | 139.87 | 700  | 0.5394          | 0.5250 | 0.1124 |
| 0.7049        | 159.87 | 800  | 0.4822          | 0.4754 | 0.0985 |
| 0.6299        | 179.87 | 900  | 0.4890          | 0.4809 | 0.1028 |
| 0.5832        | 199.87 | 1000 | 0.5233          | 0.4813 | 0.1028 |
| 0.5145        | 219.87 | 1100 | 0.5350          | 0.4781 | 0.0994 |
| 0.4604        | 239.87 | 1200 | 0.5223          | 0.4715 | 0.0984 |
| 0.4226        | 259.87 | 1300 | 0.5167          | 0.4625 | 0.0953 |
| 0.3946        | 279.87 | 1400 | 0.5248          | 0.4614 | 0.0950 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
