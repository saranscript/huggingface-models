---
language:
- hsb
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
- xlsr-fine-tuning-week
datasets:
- common_voice
model-index:
- name: Upper Sorbian comodoro Wav2Vec2 XLSR 300M CV8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: hsb
    metrics:
    - name: Test WER
      type: wer
      value: 56.3
    - name: Test CER
      type: cer 
      value: 14.3
---

# Upper Sorbian wav2vec2-xls-r-300m-hsb-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9643
- Wer: 0.5037
- Cer: 0.1278

## Evaluation

The model can be evaluated using the attached `eval.py` script:
```
python eval.py --model_id comodoro/wav2vec2-xls-r-300m-hsb-cv8 --dataset mozilla-foundation/common-voice_8_0 --split test --config hsb
```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 200
- num_epochs: 500
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|:------:|
| 4.3121        | 19.35  | 1200  | 3.2059          | 1.0    | 1.0    |
| 2.6525        | 38.71  | 2400  | 1.1324          | 0.9387 | 0.3204 |
| 1.3644        | 58.06  | 3600  | 0.8767          | 0.8099 | 0.2271 |
| 1.093         | 77.42  | 4800  | 0.8739          | 0.7603 | 0.2090 |
| 0.9546        | 96.77  | 6000  | 0.8454          | 0.6983 | 0.1882 |
| 0.8554        | 116.13 | 7200  | 0.8197          | 0.6484 | 0.1708 |
| 0.775         | 135.48 | 8400  | 0.8452          | 0.6345 | 0.1681 |
| 0.7167        | 154.84 | 9600  | 0.8551          | 0.6241 | 0.1631 |
| 0.6609        | 174.19 | 10800 | 0.8442          | 0.5821 | 0.1531 |
| 0.616         | 193.55 | 12000 | 0.8892          | 0.5864 | 0.1527 |
| 0.5815        | 212.9  | 13200 | 0.8839          | 0.5772 | 0.1503 |
| 0.55          | 232.26 | 14400 | 0.8905          | 0.5665 | 0.1436 |
| 0.5173        | 251.61 | 15600 | 0.8995          | 0.5471 | 0.1417 |
| 0.4969        | 270.97 | 16800 | 0.8633          | 0.5325 | 0.1334 |
| 0.4803        | 290.32 | 18000 | 0.9074          | 0.5253 | 0.1352 |
| 0.4596        | 309.68 | 19200 | 0.9159          | 0.5146 | 0.1294 |
| 0.4415        | 329.03 | 20400 | 0.9055          | 0.5189 | 0.1314 |
| 0.434         | 348.39 | 21600 | 0.9435          | 0.5208 | 0.1314 |
| 0.4199        | 367.74 | 22800 | 0.9199          | 0.5136 | 0.1290 |
| 0.4008        | 387.1  | 24000 | 0.9342          | 0.5174 | 0.1303 |
| 0.4051        | 406.45 | 25200 | 0.9436          | 0.5132 | 0.1292 |
| 0.3861        | 425.81 | 26400 | 0.9417          | 0.5084 | 0.1283 |
| 0.3738        | 445.16 | 27600 | 0.9573          | 0.5079 | 0.1299 |
| 0.3768        | 464.52 | 28800 | 0.9682          | 0.5062 | 0.1289 |
| 0.3647        | 483.87 | 30000 | 0.9643          | 0.5037 | 0.1278 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
