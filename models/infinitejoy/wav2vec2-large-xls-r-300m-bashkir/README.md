---
language:
- ba
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Bashkir
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: ba
    metrics:
       - name: Test WER
         type: wer
         value: 24.2
       - name: Test CER
         type: cer
         value: 5.08
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-bashkir

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - BA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1892
- Wer: 0.2421

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
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.4792        | 0.5   | 2000  | 0.4598          | 0.5404 |
| 1.449         | 1.0   | 4000  | 0.4650          | 0.5610 |
| 1.3742        | 1.49  | 6000  | 0.4001          | 0.4977 |
| 1.3375        | 1.99  | 8000  | 0.3916          | 0.4894 |
| 1.2961        | 2.49  | 10000 | 0.3641          | 0.4569 |
| 1.2714        | 2.99  | 12000 | 0.3491          | 0.4488 |
| 1.2399        | 3.48  | 14000 | 0.3151          | 0.3986 |
| 1.2067        | 3.98  | 16000 | 0.3081          | 0.3923 |
| 1.1842        | 4.48  | 18000 | 0.2875          | 0.3703 |
| 1.1644        | 4.98  | 20000 | 0.2840          | 0.3670 |
| 1.161         | 5.48  | 22000 | 0.2790          | 0.3597 |
| 1.1303        | 5.97  | 24000 | 0.2552          | 0.3272 |
| 1.0874        | 6.47  | 26000 | 0.2405          | 0.3142 |
| 1.0613        | 6.97  | 28000 | 0.2352          | 0.3055 |
| 1.0498        | 7.47  | 30000 | 0.2249          | 0.2910 |
| 1.021         | 7.96  | 32000 | 0.2118          | 0.2752 |
| 1.0002        | 8.46  | 34000 | 0.2046          | 0.2662 |
| 0.9762        | 8.96  | 36000 | 0.1969          | 0.2530 |
| 0.9568        | 9.46  | 38000 | 0.1917          | 0.2449 |
| 0.953         | 9.96  | 40000 | 0.1893          | 0.2425 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
