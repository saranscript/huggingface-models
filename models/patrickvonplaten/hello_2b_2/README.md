---
language:
- tr
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: hello_2b_2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hello_2b_2

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-2b](https://huggingface.co/facebook/wav2vec2-xls-r-2b) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5324
- Wer: 0.5109

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-06
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 2
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- total_eval_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.3543        | 0.92  | 100  | 3.4342          | 1.0    |
| 3.0521        | 1.85  | 200  | 3.1243          | 1.0    |
| 1.4905        | 2.77  | 300  | 1.1760          | 0.9876 |
| 0.5852        | 3.7   | 400  | 0.7678          | 0.7405 |
| 0.4442        | 4.63  | 500  | 0.7637          | 0.7179 |
| 0.3816        | 5.55  | 600  | 0.7114          | 0.6726 |
| 0.2923        | 6.48  | 700  | 0.7109          | 0.6837 |
| 0.2771        | 7.4   | 800  | 0.6800          | 0.6530 |
| 0.1643        | 8.33  | 900  | 0.6031          | 0.6089 |
| 0.2931        | 9.26  | 1000 | 0.6467          | 0.6308 |
| 0.1495        | 10.18 | 1100 | 0.6042          | 0.6085 |
| 0.2093        | 11.11 | 1200 | 0.5850          | 0.5889 |
| 0.1329        | 12.04 | 1300 | 0.5557          | 0.5567 |
| 0.1005        | 12.96 | 1400 | 0.5964          | 0.5814 |
| 0.2162        | 13.88 | 1500 | 0.5692          | 0.5626 |
| 0.0923        | 14.81 | 1600 | 0.5508          | 0.5462 |
| 0.075         | 15.74 | 1700 | 0.5477          | 0.5307 |
| 0.2029        | 16.66 | 1800 | 0.5501          | 0.5300 |
| 0.0985        | 17.59 | 1900 | 0.5350          | 0.5303 |
| 0.1674        | 18.51 | 2000 | 0.5429          | 0.5241 |
| 0.1305        | 19.44 | 2100 | 0.5645          | 0.5443 |
| 0.0774        | 20.37 | 2200 | 0.5313          | 0.5216 |
| 0.1372        | 21.29 | 2300 | 0.5644          | 0.5392 |
| 0.1095        | 22.22 | 2400 | 0.5577          | 0.5306 |
| 0.0958        | 23.15 | 2500 | 0.5461          | 0.5273 |
| 0.0544        | 24.07 | 2600 | 0.5290          | 0.5055 |
| 0.0579        | 24.99 | 2700 | 0.5295          | 0.5150 |
| 0.1213        | 25.92 | 2800 | 0.5311          | 0.5221 |
| 0.0691        | 26.85 | 2900 | 0.5228          | 0.5095 |
| 0.1729        | 27.77 | 3000 | 0.5340          | 0.5095 |
| 0.0697        | 28.7  | 3100 | 0.5334          | 0.5139 |
| 0.0734        | 29.63 | 3200 | 0.5323          | 0.5140 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
