---
language:
- sv-SE
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- sv
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Swedish - CV7 - v2
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: sv-SE
    metrics:
       - name: Test WER
         type: wer
         value: 15.99
       - name: Test CER
         type: cer
         value: 5.2
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: sv
    metrics:
       - name: Test WER
         type: wer
         value: 24.41
       - name: Test CER
         type: cer
         value: 11.88
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - SV-SE dataset.
It achieves the following results on the evaluation set:

- Loss: 0.2604
- Wer: 0.2334

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- gradient_accumulation_steps: 1
- total_train_batch_size: 32
- total_eval_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

See Tensorboard

### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id patrickvonplaten/xls-r-300-sv-cv7 --dataset mozilla-foundation/common_voice_7_0 --config sv-SE --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id patrickvonplaten/xls-r-300-sv-cv7 --dataset speech-recognition-community-v2/dev_data --config sv --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.18.4.dev0
- Tokenizers 0.10.3
