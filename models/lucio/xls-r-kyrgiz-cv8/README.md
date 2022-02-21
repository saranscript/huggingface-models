---
language:
- ky
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M Kyrgiz CV8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ky
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 19.01
       - name: Test CER (with LM)
         type: cer
         value: 5.38
       - name: Test WER (no LM)
         type: wer
         value: 31.28
       - name: Test CER (no LM)
         type: cer
         value: 7.66
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M Kyrgiz CV8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - KY dataset.
It achieves the following results on the validation set:
- Loss: 0.5497
- Wer: 0.2945
- Cer: 0.0791

## Model description

For a description of the model architecture, see [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m)

The model vocabulary consists of the cyrillic alphabet with punctuation removed.

The kenlm language model is built using the text of the train and invalidated corpus splits.

## Intended uses & limitations

This model is expected to be of some utility for low-fidelity use cases such as:
- Draft video captions
- Indexing of recorded broadcasts

The model is not reliable enough to use as a substitute for live captions for accessibility purposes, and it should not be used in a manner that would infringe the privacy of any of the contributors to the Common Voice dataset nor any other speakers.

## Training and evaluation data

The combination of `train`, `dev` and `other` of common voice official splits were used as training data. The half of the official `test` split was used as validation data, as and the full `test` set was used for final evaluation.

## Training procedure

The featurization layers of the XLS-R model are frozen while tuning a final CTC/LM layer on the Kyrgiz CV8 example sentences. A ramped learning rate is used with an initial warmup phase of 500 steps, a max of 0.0001, and cooling back towards 0 for the remainder of the 8100 steps (300 epochs).

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 300.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:------:|:----:|:---------------:|:------:|:------:|
| 3.1079        | 18.51  | 500  | 2.6795          | 0.9996 | 0.9825 |
| 0.8506        | 37.04  | 1000 | 0.4323          | 0.3718 | 0.0961 |
| 0.6821        | 55.55  | 1500 | 0.4105          | 0.3311 | 0.0878 |
| 0.6091        | 74.07  | 2000 | 0.4281          | 0.3168 | 0.0851 |
| 0.5429        | 92.58  | 2500 | 0.4525          | 0.3147 | 0.0842 |
| 0.5063        | 111.11 | 3000 | 0.4619          | 0.3144 | 0.0839 |
| 0.4661        | 129.62 | 3500 | 0.4660          | 0.3039 | 0.0818 |
| 0.4353        | 148.15 | 4000 | 0.4695          | 0.3083 | 0.0820 |
| 0.4048        | 166.65 | 4500 | 0.4909          | 0.3085 | 0.0824 |
| 0.3852        | 185.18 | 5000 | 0.5074          | 0.3048 | 0.0812 |
| 0.3567        | 203.69 | 5500 | 0.5111          | 0.3012 | 0.0810 |
| 0.3451        | 222.22 | 6000 | 0.5225          | 0.2982 | 0.0804 |
| 0.325         | 240.73 | 6500 | 0.5270          | 0.2955 | 0.0796 |
| 0.3089        | 259.25 | 7000 | 0.5381          | 0.2929 | 0.0793 |
| 0.2941        | 277.76 | 7500 | 0.5565          | 0.2923 | 0.0794 |
| 0.2945        | 296.29 | 8000 | 0.5495          | 0.2951 | 0.0789 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
