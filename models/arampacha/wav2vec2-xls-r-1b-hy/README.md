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
- common_voice
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
        value: 10.811865729898516
        name: WER LM
      - type: cer
        value: 2.2205361659079412
        name: CER LM
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: hy
    metrics:
       - name: Test WER
         type: wer
         value: 18.219363037089986
       - name: Test CER
         type: cer
         value: 7.075988867335752
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the /WORKSPACE/DATA/HY/NOIZY_STUDENT_4/ - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1693
- Wer: 0.2373
- Cer: 0.0429

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 64
- seed: 842
- gradient_accumulation_steps: 8
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.98) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.1
- training_steps: 5000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 1.255         | 7.24  | 500  | 0.2978          | 0.4294 | 0.0758 |
| 1.0058        | 14.49 | 1000 | 0.1883          | 0.2838 | 0.0483 |
| 0.9371        | 21.73 | 1500 | 0.1813          | 0.2627 | 0.0457 |
| 0.8999        | 28.98 | 2000 | 0.1693          | 0.2373 | 0.0429 |
| 0.8814        | 36.23 | 2500 | 0.1760          | 0.2420 | 0.0435 |
| 0.8364        | 43.47 | 3000 | 0.1765          | 0.2416 | 0.0419 |
| 0.8019        | 50.72 | 3500 | 0.1758          | 0.2311 | 0.0398 |
| 0.7665        | 57.96 | 4000 | 0.1745          | 0.2240 | 0.0399 |
| 0.7376        | 65.22 | 4500 | 0.1717          | 0.2190 | 0.0385 |
| 0.716         | 72.46 | 5000 | 0.1700          | 0.2147 | 0.0382 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
