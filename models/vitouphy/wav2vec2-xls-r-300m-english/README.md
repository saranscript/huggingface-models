---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- librispeech_asr
- robust-speech-event
- en
- generated_from_trainer
datasets:
- librispeech_asr
model-index:
- name: XLS-R-300M - English
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: LibriSpeech ASR
      type: librispeech_asr
      args: clean
    metrics:
       - name: Test WER
         type: wer
         value: 12.29
       - name: Test CER
         type: cer
         value: 3.34
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: en
    metrics:
       - name: Validation WER
         type: wer
         value: 36.75
       - name: Validation CER
         type: cer
         value: 14.83
---

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the librispeech_asr dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1444
- Wer: 0.1167


## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9365        | 4.17  | 500  | 2.9398          | 0.9999 |
| 1.5444        | 8.33  | 1000 | 0.5947          | 0.4289 |
| 1.1367        | 12.5  | 1500 | 0.2751          | 0.2366 |
| 0.9972        | 16.66 | 2000 | 0.2032          | 0.1797 |
| 0.9118        | 20.83 | 2500 | 0.1786          | 0.1479 |
| 0.8664        | 24.99 | 3000 | 0.1641          | 0.1408 |
| 0.8251        | 29.17 | 3500 | 0.1537          | 0.1267 |
| 0.793         | 33.33 | 4000 | 0.1525          | 0.1244 |
| 0.785         | 37.5  | 4500 | 0.1470          | 0.1184 |
| 0.7612        | 41.66 | 5000 | 0.1446          | 0.1177 |
| 0.7478        | 45.83 | 5500 | 0.1449          | 0.1176 |
| 0.7443        | 49.99 | 6000 | 0.1444          | 0.1167 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
