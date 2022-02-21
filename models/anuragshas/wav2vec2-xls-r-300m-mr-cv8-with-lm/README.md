---
language:
- mr
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - MR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6693
- Wer: 0.5921

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 500.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| 4.9504        | 18.18  | 400   | 4.6730          | 1.0    |
| 3.3766        | 36.36  | 800   | 3.3464          | 1.0    |
| 3.1128        | 54.55  | 1200  | 3.0177          | 0.9980 |
| 1.7966        | 72.73  | 1600  | 0.8733          | 0.8039 |
| 1.4085        | 90.91  | 2000  | 0.5555          | 0.6458 |
| 1.1731        | 109.09 | 2400  | 0.4930          | 0.6438 |
| 1.0271        | 127.27 | 2800  | 0.4780          | 0.6093 |
| 0.9045        | 145.45 | 3200  | 0.4647          | 0.6578 |
| 0.807         | 163.64 | 3600  | 0.4505          | 0.5925 |
| 0.741         | 181.82 | 4000  | 0.4746          | 0.6025 |
| 0.6706        | 200.0  | 4400  | 0.5004          | 0.5844 |
| 0.6186        | 218.18 | 4800  | 0.4984          | 0.5997 |
| 0.5508        | 236.36 | 5200  | 0.5298          | 0.5636 |
| 0.5123        | 254.55 | 5600  | 0.5410          | 0.5110 |
| 0.4623        | 272.73 | 6000  | 0.5591          | 0.5383 |
| 0.4281        | 290.91 | 6400  | 0.5775          | 0.5600 |
| 0.4045        | 309.09 | 6800  | 0.5924          | 0.5580 |
| 0.3651        | 327.27 | 7200  | 0.5671          | 0.5684 |
| 0.343         | 345.45 | 7600  | 0.6083          | 0.5945 |
| 0.3085        | 363.64 | 8000  | 0.6243          | 0.5728 |
| 0.2941        | 381.82 | 8400  | 0.6245          | 0.5580 |
| 0.2735        | 400.0  | 8800  | 0.6458          | 0.5804 |
| 0.262         | 418.18 | 9200  | 0.6566          | 0.5824 |
| 0.2578        | 436.36 | 9600  | 0.6558          | 0.5965 |
| 0.2388        | 454.55 | 10000 | 0.6598          | 0.5993 |
| 0.2328        | 472.73 | 10400 | 0.6700          | 0.6041 |
| 0.2286        | 490.91 | 10800 | 0.6684          | 0.5957 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
