---
license: apache-2.0
language:
- vi
tags:
- automatic-speech-recognition
- robust-speech-event
- common-voice
- vi
model-index:
- name: xls-asr-vi-40h-1B
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7.0
      type: mozilla-foundation/common_voice_7_0

      args: vi
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 25.846
       - name: Test CER (with LM)
         type: cer
         value: 12.961
         
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8.0
      type: mozilla-foundation/common_voice_8_0

      args: vi
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 31.158
       - name: Test CER (with LM)
         type: cer
         value: 16.179
---


# xls-asr-vi-40h-1B

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on 40 hours of FPT Open Speech Dataset (FOSD) and Common Voice 7.0.

### Benchmark WER result:
| | [VIVOS](https://huggingface.co/datasets/vivos) | [COMMON VOICE 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | [COMMON VOICE 8.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)
|---|---|---|---|
|without LM| 25.93 | 34.21 |
|with 4-grams LM| 24.11 | 25.84 | 31.158 |

### Benchmark CER result:
| | [VIVOS](https://huggingface.co/datasets/vivos) | [COMMON VOICE 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | [COMMON VOICE 8.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)
|---|---|---|---|
|without LM| 9.24 | 19.94 |
|with 4-grams LM| 10.37 | 12.96 | 16.179 |

## Evaluation

Please use the eval.py file to run the evaluation

```python
python eval.py --model_id geninhu/xls-asr-vi-40h-1B --dataset mozilla-foundation/common_voice_7_0 --config vi --split test --log_outputs
```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 4.6222        | 1.85  | 1500  | 5.9479          | 0.5474 |
| 1.1362        | 3.7   | 3000  | 7.9799          | 0.5094 |
| 0.7814        | 5.56  | 4500  | 5.0330          | 0.4724 |
| 0.6281        | 7.41  | 6000  | 2.3484          | 0.5020 |
| 0.5472        | 9.26  | 7500  | 2.2495          | 0.4793 |
| 0.4827        | 11.11 | 9000  | 1.1530          | 0.4768 |
| 0.4327        | 12.96 | 10500 | 1.6160          | 0.4646 |
| 0.3989        | 14.81 | 12000 | 3.2633          | 0.4703 |
| 0.3522        | 16.67 | 13500 | 2.2337          | 0.4708 |
| 0.3201        | 18.52 | 15000 | 3.6879          | 0.4565 |
| 0.2899        | 20.37 | 16500 | 5.4389          | 0.4599 |
| 0.2776        | 22.22 | 18000 | 3.5284          | 0.4537 |
| 0.2574        | 24.07 | 19500 | 2.1759          | 0.4649 |
| 0.2378        | 25.93 | 21000 | 3.3901          | 0.4448 |
| 0.217         | 27.78 | 22500 | 1.1632          | 0.4565 |
| 0.2115        | 29.63 | 24000 | 1.7441          | 0.4232 |
| 0.1959        | 31.48 | 25500 | 3.4992          | 0.4304 |
| 0.187         | 33.33 | 27000 | 3.6163          | 0.4369 |
| 0.1748        | 35.19 | 28500 | 3.6038          | 0.4467 |
| 0.17          | 37.04 | 30000 | 2.9708          | 0.4362 |
| 0.159         | 38.89 | 31500 | 3.2045          | 0.4279 |
| 0.153         | 40.74 | 33000 | 3.2427          | 0.4287 |
| 0.1463        | 42.59 | 34500 | 3.5439          | 0.4270 |
| 0.139         | 44.44 | 36000 | 3.9381          | 0.4150 |
| 0.1352        | 46.3  | 37500 | 4.1744          | 0.4092 |
| 0.1369        | 48.15 | 39000 | 4.2279          | 0.4154 |
| 0.1273        | 50.0  | 40500 | 4.1691          | 0.4133 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
