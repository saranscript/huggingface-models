---
language:
- es
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- es
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-cls-r-300m-es
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: es
    metrics:
       - name: Test WER
         type: wer
         value: 37.37
       - name: Test CER
         type: cer
         value: 7.11
  # - task: 
  #     name: Automatic Speech Recognition
  #     type: automatic-speech-recognition
  #   dataset:
  #     name: Robust Speech Event - Dev Data
  #     type: speech-recognition-community-v2/dev_data
  #     args: es
  #   metrics:
  #      - name: Test WER
  #        type: wer
  #        value: 
  #      - name: Test CER
  #        type: cer
  #        value: 
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-cls-r-300m-es

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - ES dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5160
- Wer: 0.4016

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 8.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.1277        | 1.14  | 500  | 2.0259          | 0.9999 |
| 1.4111        | 2.28  | 1000 | 1.1251          | 0.8894 |
| 0.8461        | 3.42  | 1500 | 0.8205          | 0.7244 |
| 0.5042        | 4.57  | 2000 | 0.6116          | 0.5463 |
| 0.3072        | 5.71  | 2500 | 0.5507          | 0.4506 |
| 0.2181        | 6.85  | 3000 | 0.5213          | 0.4177 |
| 0.1608        | 7.99  | 3500 | 0.5161          | 0.4019 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id samitizerxu/wav2vec2-xls-r-300m-es --dataset mozilla-foundation/common_voice_7_0 --config es --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id samitizerxu/wav2vec2-xls-r-300m-es --dataset speech-recognition-community-v2/dev_data --config es --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```