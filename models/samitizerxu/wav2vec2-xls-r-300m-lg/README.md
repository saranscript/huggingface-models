---
language:
- lg
license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
- common_voice
- lg
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-lg
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: sv-SE
    metrics:
       - name: Test WER
         type: wer
         value: 78.89
       - name: Test CER
         type: cer
         value: 15.16
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-lg

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - LG dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6989
- Wer: 0.8529

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
- num_epochs: 20.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9089        | 6.33  | 500  | 2.8983          | 1.0002 |
| 2.5754        | 12.66 | 1000 | 1.8710          | 1.0    |
| 1.4093        | 18.99 | 1500 | 0.7195          | 0.8547 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id samitizerxu/wav2vec2-xls-r-300m-lg --dataset mozilla-foundation/common_voice_7_0 --config lg --split test
```
