---
language:
- sah
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- sah
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Sakha
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: sah
    metrics:
       - name: Test WER
         type: wer
         value: 44.196
       - name: Test CER
         type: cer
         value: 10.271
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-sakha

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - SAH dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4995
- Wer: 0.4421

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
- train_batch_size: 32
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.8597        | 8.47  | 500  | 0.7731          | 0.7211 |
| 1.2508        | 16.95 | 1000 | 0.5368          | 0.5989 |
| 1.1066        | 25.42 | 1500 | 0.5034          | 0.5533 |
| 1.0064        | 33.9  | 2000 | 0.4686          | 0.5114 |
| 0.9324        | 42.37 | 2500 | 0.4927          | 0.5056 |
| 0.876         | 50.85 | 3000 | 0.4734          | 0.4795 |
| 0.8082        | 59.32 | 3500 | 0.4748          | 0.4799 |
| 0.7604        | 67.8  | 4000 | 0.4949          | 0.4691 |
| 0.7241        | 76.27 | 4500 | 0.5090          | 0.4627 |
| 0.6739        | 84.75 | 5000 | 0.4967          | 0.4452 |
| 0.6447        | 93.22 | 5500 | 0.5071          | 0.4437 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
