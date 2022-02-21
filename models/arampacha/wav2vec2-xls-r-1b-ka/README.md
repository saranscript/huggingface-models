
---
language:
- ka
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-1b-ka
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice ka
      args: ka
    metrics:
      - type: wer
        value: 7.39778066580026
        name: WER LM
      - type: cer
        value: 1.1882089427096435
        name: CER LM
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-1b-ka

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the /WORKSPACE/DATA/KA/NOIZY_STUDENT_2/ - KA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1022
- Wer: 0.1527
- Cer: 0.0221

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7e-05
- train_batch_size: 16
- eval_batch_size: 64
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.98) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.1
- training_steps: 4000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 1.2839        | 6.45  | 400  | 0.2229          | 0.3609 | 0.0557 |
| 0.9775        | 12.9  | 800  | 0.1271          | 0.2202 | 0.0317 |
| 0.9045        | 19.35 | 1200 | 0.1268          | 0.2030 | 0.0294 |
| 0.8652        | 25.8  | 1600 | 0.1211          | 0.1940 | 0.0287 |
| 0.8505        | 32.26 | 2000 | 0.1192          | 0.1912 | 0.0276 |
| 0.8168        | 38.7  | 2400 | 0.1086          | 0.1763 | 0.0260 |
| 0.7737        | 45.16 | 2800 | 0.1098          | 0.1753 | 0.0256 |
| 0.744         | 51.61 | 3200 | 0.1054          | 0.1646 | 0.0239 |
| 0.7114        | 58.06 | 3600 | 0.1034          | 0.1573 | 0.0228 |
| 0.6773        | 64.51 | 4000 | 0.1022          | 0.1527 | 0.0221 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
