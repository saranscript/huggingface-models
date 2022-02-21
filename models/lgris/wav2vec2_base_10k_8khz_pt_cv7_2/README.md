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
- name: wav2vec2_base_10k_8khz_pt_cv7_2
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: pt
    metrics:
       - name: Test WER
         type: wer
         value: 36.90
       - name: Test CER
         type: cer
         value: 14.82
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
         value: 40.53
       - name: Test CER
         type: cer
         value: 16.95
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2_base_10k_8khz_pt_cv7_2

This model is a fine-tuned version of [lgris/seasr_2022_base_10k_8khz_pt](https://huggingface.co/lgris/seasr_2022_base_10k_8khz_pt) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 76.3426
- Wer: 0.1979

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- training_steps: 10000

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 189.1362      | 0.65  | 500   | 80.6347         | 0.2139 |
| 174.2587      | 1.3   | 1000  | 80.2062         | 0.2116 |
| 164.676       | 1.95  | 1500  | 78.2161         | 0.2073 |
| 176.5856      | 2.6   | 2000  | 78.8920         | 0.2074 |
| 164.3583      | 3.25  | 2500  | 77.2865         | 0.2066 |
| 161.414       | 3.9   | 3000  | 77.8888         | 0.2048 |
| 158.283       | 4.55  | 3500  | 77.3472         | 0.2033 |
| 159.2265      | 5.19  | 4000  | 79.0953         | 0.2036 |
| 156.3967      | 5.84  | 4500  | 76.6855         | 0.2029 |
| 154.2743      | 6.49  | 5000  | 77.7785         | 0.2015 |
| 156.6497      | 7.14  | 5500  | 77.1220         | 0.2033 |
| 157.3038      | 7.79  | 6000  | 76.2926         | 0.2027 |
| 162.8151      | 8.44  | 6500  | 76.7602         | 0.2013 |
| 151.8613      | 9.09  | 7000  | 77.4777         | 0.2011 |
| 153.0225      | 9.74  | 7500  | 76.5206         | 0.2001 |
| 157.52        | 10.39 | 8000  | 76.1061         | 0.2006 |
| 145.0592      | 11.04 | 8500  | 76.7855         | 0.1992 |
| 150.0066      | 11.69 | 9000  | 76.0058         | 0.1988 |
| 146.8128      | 12.34 | 9500  | 76.2853         | 0.1987 |
| 146.9148      | 12.99 | 10000 | 76.3426         | 0.1979 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
