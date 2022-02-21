---
license: apache-2.0
tags:
- automatic-speech-recognition
- multilingual_librispeech
- generated_from_trainer
datasets:
- multilingual_librispeech
model-index:
- name: wav2vec2-xlsr-53-300m-mls-german-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xlsr-53-300m-mls-german-ft

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the MULTILINGUAL_LIBRISPEECH - GERMAN 10h dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2219
- Wer: 0.1288

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
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 200.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| 2.9888        | 7.25   | 500   | 2.9192          | 1.0    |
| 2.9313        | 14.49  | 1000  | 2.8698          | 1.0    |
| 1.068         | 21.74  | 1500  | 0.2647          | 0.2565 |
| 0.8151        | 28.99  | 2000  | 0.2067          | 0.1719 |
| 0.764         | 36.23  | 2500  | 0.1975          | 0.1568 |
| 0.7332        | 43.48  | 3000  | 0.1812          | 0.1463 |
| 0.5952        | 50.72  | 3500  | 0.1923          | 0.1428 |
| 0.6655        | 57.97  | 4000  | 0.1900          | 0.1404 |
| 0.574         | 65.22  | 4500  | 0.1822          | 0.1370 |
| 0.6211        | 72.46  | 5000  | 0.1937          | 0.1355 |
| 0.5883        | 79.71  | 5500  | 0.1872          | 0.1335 |
| 0.5666        | 86.96  | 6000  | 0.1874          | 0.1324 |
| 0.5526        | 94.2   | 6500  | 0.1998          | 0.1368 |
| 0.5671        | 101.45 | 7000  | 0.2054          | 0.1365 |
| 0.5514        | 108.7  | 7500  | 0.1987          | 0.1340 |
| 0.5382        | 115.94 | 8000  | 0.2104          | 0.1344 |
| 0.5819        | 123.19 | 8500  | 0.2125          | 0.1334 |
| 0.5277        | 130.43 | 9000  | 0.2063          | 0.1330 |
| 0.4626        | 137.68 | 9500  | 0.2105          | 0.1310 |
| 0.5842        | 144.93 | 10000 | 0.2087          | 0.1307 |
| 0.535         | 152.17 | 10500 | 0.2137          | 0.1309 |
| 0.5081        | 159.42 | 11000 | 0.2215          | 0.1302 |
| 0.6033        | 166.67 | 11500 | 0.2162          | 0.1302 |
| 0.5549        | 173.91 | 12000 | 0.2198          | 0.1286 |
| 0.5389        | 181.16 | 12500 | 0.2241          | 0.1293 |
| 0.4912        | 188.41 | 13000 | 0.2190          | 0.1290 |
| 0.4671        | 195.65 | 13500 | 0.2218          | 0.1290 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
