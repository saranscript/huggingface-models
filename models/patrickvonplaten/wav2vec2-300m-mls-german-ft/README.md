---
license: apache-2.0
tags:
- automatic-speech-recognition
- multilingual_librispeech
- generated_from_trainer
datasets:
- multilingual_librispeech
model-index:
- name: wav2vec2-300m-mls-german-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-300m-mls-german-ft

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MULTILINGUAL_LIBRISPEECH - GERMAN 10h dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2398
- Wer: 0.1520

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
| 3.0132        | 7.25   | 500   | 2.9393          | 1.0    |
| 2.9241        | 14.49  | 1000  | 2.8734          | 1.0    |
| 1.0766        | 21.74  | 1500  | 0.2773          | 0.2488 |
| 0.8416        | 28.99  | 2000  | 0.2224          | 0.1990 |
| 0.8048        | 36.23  | 2500  | 0.2063          | 0.1792 |
| 0.7664        | 43.48  | 3000  | 0.2088          | 0.1748 |
| 0.6571        | 50.72  | 3500  | 0.2042          | 0.1668 |
| 0.7014        | 57.97  | 4000  | 0.2136          | 0.1649 |
| 0.6171        | 65.22  | 4500  | 0.2139          | 0.1641 |
| 0.6609        | 72.46  | 5000  | 0.2144          | 0.1621 |
| 0.6318        | 79.71  | 5500  | 0.2129          | 0.1600 |
| 0.6222        | 86.96  | 6000  | 0.2124          | 0.1582 |
| 0.608         | 94.2   | 6500  | 0.2255          | 0.1639 |
| 0.6099        | 101.45 | 7000  | 0.2265          | 0.1622 |
| 0.6069        | 108.7  | 7500  | 0.2246          | 0.1593 |
| 0.5929        | 115.94 | 8000  | 0.2323          | 0.1617 |
| 0.6218        | 123.19 | 8500  | 0.2287          | 0.1566 |
| 0.5751        | 130.43 | 9000  | 0.2275          | 0.1563 |
| 0.5181        | 137.68 | 9500  | 0.2316          | 0.1579 |
| 0.6306        | 144.93 | 10000 | 0.2372          | 0.1556 |
| 0.5874        | 152.17 | 10500 | 0.2362          | 0.1533 |
| 0.5546        | 159.42 | 11000 | 0.2342          | 0.1543 |
| 0.6294        | 166.67 | 11500 | 0.2381          | 0.1536 |
| 0.5989        | 173.91 | 12000 | 0.2360          | 0.1527 |
| 0.5697        | 181.16 | 12500 | 0.2399          | 0.1526 |
| 0.5379        | 188.41 | 13000 | 0.2375          | 0.1523 |
| 0.5022        | 195.65 | 13500 | 0.2395          | 0.1519 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
