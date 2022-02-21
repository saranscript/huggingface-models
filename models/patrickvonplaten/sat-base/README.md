---
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: sat-base
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sat-base

This model is a fine-tuned version of [microsoft/unispeech-sat-base](https://huggingface.co/microsoft/unispeech-sat-base) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7014
- Wer: 0.5374

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 32
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 20.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 6.9958        | 0.69  | 100  | 6.7171          | 1.0    |
| 3.0453        | 1.38  | 200  | 3.0374          | 1.0    |
| 2.9989        | 2.07  | 300  | 2.9807          | 1.0    |
| 2.969         | 2.76  | 400  | 2.9579          | 1.0    |
| 2.903         | 3.45  | 500  | 2.9072          | 1.0    |
| 2.8565        | 4.14  | 600  | 2.8804          | 1.0    |
| 2.8195        | 4.83  | 700  | 2.7916          | 1.0    |
| 2.3134        | 5.52  | 800  | 2.1456          | 1.0004 |
| 1.5475        | 6.21  | 900  | 1.4663          | 0.9549 |
| 1.1295        | 6.9   | 1000 | 1.1140          | 0.7227 |
| 1.0181        | 7.59  | 1100 | 0.9258          | 0.6497 |
| 1.0252        | 8.28  | 1200 | 0.8430          | 0.6255 |
| 0.835         | 8.97  | 1300 | 0.8063          | 0.6032 |
| 0.662         | 9.66  | 1400 | 0.7595          | 0.5931 |
| 0.5558        | 10.34 | 1500 | 0.7322          | 0.5819 |
| 0.7596        | 11.03 | 1600 | 0.7120          | 0.5708 |
| 0.6169        | 11.72 | 1700 | 0.7073          | 0.5606 |
| 0.4565        | 12.41 | 1800 | 0.7124          | 0.5586 |
| 0.4554        | 13.1  | 1900 | 0.6880          | 0.5501 |
| 0.6216        | 13.79 | 2000 | 0.6783          | 0.5494 |
| 0.5393        | 14.48 | 2100 | 0.7067          | 0.5499 |
| 0.4095        | 15.17 | 2200 | 0.7014          | 0.5438 |
| 0.3551        | 15.86 | 2300 | 0.7000          | 0.5426 |
| 0.5112        | 16.55 | 2400 | 0.6866          | 0.5426 |
| 0.5139        | 17.24 | 2500 | 0.7134          | 0.5446 |
| 0.3638        | 17.93 | 2600 | 0.7130          | 0.5434 |
| 0.3327        | 18.62 | 2700 | 0.6980          | 0.5377 |
| 0.4385        | 19.31 | 2800 | 0.7017          | 0.5390 |
| 0.4986        | 20.0  | 2900 | 0.7014          | 0.5374 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
