---
license: apache-2.0
language:
- ja
tags:
- automatic-speech-recognition
- robust-speech-event
- common-voice
- ja
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-1b
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7.0
      type: mozilla-foundation/common_voice_7_0
      args: ja
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 11.77
       - name: Test CER (with LM)
         type: cer
         value: 5.22
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8.0
      type: mozilla-foundation/common_voice_8_0
      args: ja
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 12.23
       - name: Test CER (with LM)
         type: cer
         value: 5.33
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: ja
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 29.35
       - name: Test CER (with LM)
         type: cer
         value: 16.43
---
## Model description

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - JA 

### Benchmark WER result:
| | [COMMON VOICE 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | [COMMON VOICE 8.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)
|---|---|---|
|without LM| 16.97 | 17.95 |
|with 4-grams LM| 11.77 | 12.23|
### Benchmark CER result:
| | [COMMON VOICE 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | [COMMON VOICE 8.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)
|---|---|---|
|without LM| 6.82 | 7.05 |
|with 4-grams LM| 5.22 | 5.33 |
## Evaluation
Please use the eval.py file to run the evaluation:
```python
pip install mecab-python3 unidic-lite pykakasi
python eval.py --model_id vutankiet2901/wav2vec2-xls-r-1b-ja --dataset mozilla-foundation/common_voice_8_0 --config ja --split test --log_outputs
```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 3.484         | 9.49  | 1500  | 1.1849          | 0.7543 | 0.4099 |
| 1.3582        | 18.98 | 3000  | 0.4320          | 0.3489 | 0.1591 |
| 1.1716        | 28.48 | 4500  | 0.3835          | 0.3175 | 0.1454 |
| 1.0951        | 37.97 | 6000  | 0.3732          | 0.3033 | 0.1405 |
| 1.04          | 47.47 | 7500  | 0.3485          | 0.2898 | 0.1360 |
| 0.9768        | 56.96 | 9000  | 0.3386          | 0.2787 | 0.1309 |
| 0.9129        | 66.45 | 10500 | 0.3363          | 0.2711 | 0.1272 |
| 0.8614        | 75.94 | 12000 | 0.3386          | 0.2676 | 0.1260 |
| 0.8092        | 85.44 | 13500 | 0.3356          | 0.2610 | 0.1240 |
| 0.7658        | 94.93 | 15000 | 0.3316          | 0.2564 | 0.1218 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
