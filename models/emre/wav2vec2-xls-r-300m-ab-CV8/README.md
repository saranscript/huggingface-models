---
license: apache-2.0
language: ab
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-ab-CV8
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice ab
      type: common_voice
      args: ab
    metrics:
       - name: Test WER
         type: wer
         value: 54.74
---


# wav2vec2-xls-r-300m-ab-CV8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2105
- Wer: 0.5474

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 300
- num_epochs: 15
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 4.7729        | 0.63  | 500   | 3.0624          | 1.0021 |
| 2.7348        | 1.26  | 1000  | 1.0460          | 0.9815 |
| 1.2756        | 1.9   | 1500  | 0.4618          | 0.8309 |
| 1.0419        | 2.53  | 2000  | 0.3725          | 0.7449 |
| 0.9491        | 3.16  | 2500  | 0.3368          | 0.7345 |
| 0.9006        | 3.79  | 3000  | 0.3014          | 0.6936 |
| 0.8519        | 4.42  | 3500  | 0.2852          | 0.6767 |
| 0.8243        | 5.06  | 4000  | 0.2701          | 0.6504 |
| 0.7902        | 5.69  | 4500  | 0.2641          | 0.6221 |
| 0.7767        | 6.32  | 5000  | 0.2549          | 0.6192 |
| 0.7516        | 6.95  | 5500  | 0.2515          | 0.6179 |
| 0.737         | 7.59  | 6000  | 0.2408          | 0.5963 |
| 0.7217        | 8.22  | 6500  | 0.2429          | 0.6261 |
| 0.7101        | 8.85  | 7000  | 0.2366          | 0.5687 |
| 0.6922        | 9.48  | 7500  | 0.2277          | 0.5680 |
| 0.6866        | 10.11 | 8000  | 0.2242          | 0.5847 |
| 0.6703        | 10.75 | 8500  | 0.2222          | 0.5803 |
| 0.6649        | 11.38 | 9000  | 0.2247          | 0.5765 |
| 0.6513        | 12.01 | 9500  | 0.2182          | 0.5644 |
| 0.6369        | 12.64 | 10000 | 0.2128          | 0.5508 |
| 0.6425        | 13.27 | 10500 | 0.2132          | 0.5514 |
| 0.6399        | 13.91 | 11000 | 0.2116          | 0.5495 |
| 0.6208        | 14.54 | 11500 | 0.2105          | 0.5474 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.10.3
