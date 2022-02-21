---
language:
- et
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
- et
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: ''
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: et
    metrics:
       - name: Test WER
         type: wer
         value: 0.34753420299077314
       - name: Test CER
         type: cer
         value: 0.07542956089330906 
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - ET dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4835
- Wer: 0.3475

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
- train_batch_size: 72
- eval_batch_size: 72
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 144
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.3825        | 12.5  | 500  | 0.4022          | 0.5059 |
| 0.1592        | 25.0  | 1000 | 0.4585          | 0.4456 |
| 0.1215        | 37.5  | 1500 | 0.4550          | 0.4164 |
| 0.0972        | 50.0  | 2000 | 0.4725          | 0.4088 |
| 0.0731        | 62.5  | 2500 | 0.4568          | 0.3824 |
| 0.0527        | 75.0  | 3000 | 0.4712          | 0.3653 |
| 0.0428        | 87.5  | 3500 | 0.4813          | 0.3520 |
| 0.0383        | 100.0 | 4000 | 0.4835          | 0.3475 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
