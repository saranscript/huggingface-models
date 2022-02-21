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
- name: wav2vec2-large-xlsr-53-ja
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7.0
      type: mozilla-foundation/common_voice_8_0
      args: ja
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 15.37
       - name: Test CER (with LM)
         type: cer
         value: 6.91
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
         value: 16.09
       - name: Test CER (with LM)
         type: cer
         value: 7.15
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
         value: 37.96
       - name: Test CER (with LM)
         type: cer
         value: 21.11 
---

## Model description

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - JA dataset.

### Benchmark WER result:
| | [COMMON VOICE 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | [COMMON VOICE 8.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)
|---|---|---|
|without LM| 15.74 | 25.10 |
|with 4-grams LM| 15.37 | 16.09 |

### Benchmark CER result:
| | [COMMON VOICE 7.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | [COMMON VOICE 8.0](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0)
|---|---|---|
|without LM| 9.51 | 9.95 |
|with 4-grams LM| 6.91 | 7.15 |

## Evaluation

Please use the eval.py file to run the evaluation:

```python
python eval.py --model_id vutankiet2901/wav2vec2-large-xlsr-53-ja --dataset mozilla-foundation/common_voice_7_0 --config ja --split test --log_outputs
```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 4.7776        | 4.73  | 1500  | 2.9540          | 0.9772 | 0.8489 |
| 1.9076        | 9.46  | 3000  | 0.7146          | 0.5371 | 0.2484 |
| 1.507         | 14.2  | 4500  | 0.5843          | 0.4689 | 0.2196 |
| 1.3742        | 18.93 | 6000  | 0.5286          | 0.4321 | 0.1988 |
| 1.2776        | 23.66 | 7500  | 0.5007          | 0.4056 | 0.1870 |
| 1.2003        | 28.39 | 9000  | 0.4676          | 0.3848 | 0.1802 |
| 1.1281        | 33.12 | 10500 | 0.4524          | 0.3694 | 0.1720 |
| 1.0657        | 37.85 | 12000 | 0.4449          | 0.3590 | 0.1681 |
| 1.0129        | 42.59 | 13500 | 0.4266          | 0.3423 | 0.1617 |
| 0.9691        | 47.32 | 15000 | 0.4214          | 0.3375 | 0.1587 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
