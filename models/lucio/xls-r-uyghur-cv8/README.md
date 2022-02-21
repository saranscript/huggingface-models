---
language:
- ug
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- ug
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M Uyghur CV8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ug
    metrics:
       - name: Test WER
         type: wer
         value: 30.50
       - name: Test CER
         type: cer
         value: 5.80
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M Uyghur CV8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - UG dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2026
- Wer: 0.3248

## Model description

For a description of the model architecture, see [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m)

The model vocabulary consists of the alphabetic characters of the [Perso-Arabic script for the Uyghur language](https://omniglot.com/writing/uyghur.htm), with punctuation removed.

## Intended uses & limitations

This model is expected to be of some utility for low-fidelity use cases such as:
- Draft video captions
- Indexing of recorded broadcasts

The model is not reliable enough to use as a substitute for live captions for accessibility purposes, and it should not be used in a manner that would infringe the privacy of any of the contributors to the Common Voice dataset nor any other speakers.

## Training and evaluation data

The combination of `train` and `dev` of common voice official splits were used as training data. The official `test` split was used as validation data as well as for final evaluation.

## Training procedure

The featurization layers of the XLS-R model are frozen while tuning a final CTC/LM layer on the Uyghur CV8 example sentences. A ramped learning rate is used with an initial warmup phase of 2000 steps, a max of 0.0001, and cooling back towards 0 for the remainder of the 9400 steps (100 epochs).

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.3036        | 5.32  | 500  | 3.2628          | 1.0    |
| 2.9734        | 10.63 | 1000 | 2.5677          | 0.9980 |
| 1.3466        | 15.95 | 1500 | 0.4455          | 0.6306 |
| 1.2424        | 21.28 | 2000 | 0.3603          | 0.5301 |
| 1.1655        | 26.59 | 2500 | 0.3165          | 0.4740 |
| 1.1026        | 31.91 | 3000 | 0.2930          | 0.4400 |
| 1.0655        | 37.23 | 3500 | 0.2675          | 0.4159 |
| 1.0239        | 42.55 | 4000 | 0.2580          | 0.3913 |
| 0.9938        | 47.87 | 4500 | 0.2373          | 0.3698 |
| 0.9655        | 53.19 | 5000 | 0.2379          | 0.3675 |
| 0.9374        | 58.51 | 5500 | 0.2486          | 0.3795 |
| 0.9065        | 63.83 | 6000 | 0.2243          | 0.3405 |
| 0.888         | 69.15 | 6500 | 0.2157          | 0.3277 |
| 0.8646        | 74.47 | 7000 | 0.2103          | 0.3288 |
| 0.8602        | 79.78 | 7500 | 0.2088          | 0.3238 |
| 0.8442        | 85.11 | 8000 | 0.2045          | 0.3266 |
| 0.8335        | 90.42 | 8500 | 0.2038          | 0.3241 |
| 0.8288        | 95.74 | 9000 | 0.2024          | 0.3280 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
