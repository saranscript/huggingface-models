---
language:
- gn
license: apache-2.0
tags:
- automatic-speech-recognition
- generated_from_trainer
- gn
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-300m-gn-cv8-4
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-gn-cv8-4

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5805
- Wer: 0.7545

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- training_steps: 13000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| 9.2216        | 16.65  | 300   | 3.2771          | 1.0    |
| 3.1804        | 33.32  | 600   | 2.2869          | 1.0    |
| 1.5856        | 49.97  | 900   | 0.9573          | 0.8772 |
| 1.0299        | 66.65  | 1200  | 0.9044          | 0.8082 |
| 0.8916        | 83.32  | 1500  | 0.9478          | 0.8056 |
| 0.8451        | 99.97  | 1800  | 0.8814          | 0.8107 |
| 0.7649        | 116.65 | 2100  | 0.9897          | 0.7826 |
| 0.7185        | 133.32 | 2400  | 0.9988          | 0.7621 |
| 0.6595        | 149.97 | 2700  | 1.0607          | 0.7749 |
| 0.6211        | 166.65 | 3000  | 1.1826          | 0.7877 |
| 0.59          | 183.32 | 3300  | 1.1060          | 0.7826 |
| 0.5383        | 199.97 | 3600  | 1.1826          | 0.7852 |
| 0.5205        | 216.65 | 3900  | 1.2148          | 0.8261 |
| 0.4786        | 233.32 | 4200  | 1.2710          | 0.7928 |
| 0.4482        | 249.97 | 4500  | 1.1943          | 0.7980 |
| 0.4149        | 266.65 | 4800  | 1.2449          | 0.8031 |
| 0.3904        | 283.32 | 5100  | 1.3100          | 0.7928 |
| 0.3619        | 299.97 | 5400  | 1.3125          | 0.7596 |
| 0.3496        | 316.65 | 5700  | 1.3699          | 0.7877 |
| 0.3277        | 333.32 | 6000  | 1.4344          | 0.8031 |
| 0.2958        | 349.97 | 6300  | 1.4093          | 0.7980 |
| 0.2883        | 366.65 | 6600  | 1.3296          | 0.7570 |
| 0.2598        | 383.32 | 6900  | 1.4026          | 0.7980 |
| 0.2564        | 399.97 | 7200  | 1.4847          | 0.8031 |
| 0.2408        | 416.65 | 7500  | 1.4896          | 0.8107 |
| 0.2266        | 433.32 | 7800  | 1.4232          | 0.7698 |
| 0.224         | 449.97 | 8100  | 1.5560          | 0.7903 |
| 0.2038        | 466.65 | 8400  | 1.5355          | 0.7724 |
| 0.1948        | 483.32 | 8700  | 1.4624          | 0.7621 |
| 0.1995        | 499.97 | 9000  | 1.5808          | 0.7724 |
| 0.1864        | 516.65 | 9300  | 1.5653          | 0.7698 |
| 0.18          | 533.32 | 9600  | 1.4868          | 0.7494 |
| 0.1689        | 549.97 | 9900  | 1.5379          | 0.7749 |
| 0.1624        | 566.65 | 10200 | 1.5936          | 0.7749 |
| 0.1537        | 583.32 | 10500 | 1.6436          | 0.7801 |
| 0.1455        | 599.97 | 10800 | 1.6401          | 0.7673 |
| 0.1437        | 616.65 | 11100 | 1.6069          | 0.7673 |
| 0.1452        | 633.32 | 11400 | 1.6041          | 0.7519 |
| 0.139         | 649.97 | 11700 | 1.5758          | 0.7545 |
| 0.1299        | 666.65 | 12000 | 1.5559          | 0.7545 |
| 0.127         | 683.32 | 12300 | 1.5776          | 0.7596 |
| 0.1264        | 699.97 | 12600 | 1.5790          | 0.7519 |
| 0.1209        | 716.65 | 12900 | 1.5805          | 0.7545 |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
