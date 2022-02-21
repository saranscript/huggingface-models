---
language:
- eo
license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
- common_voice
- generated_from_trainer
- eo
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-eo
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: eo
    metrics:
       - name: Test WER
         type: wer
         value: 34.72
       - name: Test CER
         type: cer
         value: 7.54
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-eo

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - EO dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2584
- Wer: 0.3114

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

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.1701        | 0.8   | 500   | 2.8105          | 1.0    |
| 1.9143        | 1.6   | 1000  | 0.5977          | 0.7002 |
| 1.1259        | 2.4   | 1500  | 0.5063          | 0.6157 |
| 0.9732        | 3.2   | 2000  | 0.4264          | 0.5673 |
| 0.8983        | 4.0   | 2500  | 0.4249          | 0.4902 |
| 0.8507        | 4.8   | 3000  | 0.3811          | 0.4536 |
| 0.8064        | 5.6   | 3500  | 0.3643          | 0.4467 |
| 0.7866        | 6.4   | 4000  | 0.3600          | 0.4453 |
| 0.7773        | 7.2   | 4500  | 0.3724          | 0.4470 |
| 0.747         | 8.0   | 5000  | 0.3501          | 0.4189 |
| 0.7279        | 8.8   | 5500  | 0.3500          | 0.4261 |
| 0.7153        | 9.6   | 6000  | 0.3328          | 0.3966 |
| 0.7           | 10.4  | 6500  | 0.3314          | 0.3869 |
| 0.6784        | 11.2  | 7000  | 0.3396          | 0.4051 |
| 0.6582        | 12.0  | 7500  | 0.3236          | 0.3899 |
| 0.6478        | 12.8  | 8000  | 0.3263          | 0.3832 |
| 0.6277        | 13.6  | 8500  | 0.3139          | 0.3769 |
| 0.6053        | 14.4  | 9000  | 0.2955          | 0.3536 |
| 0.5777        | 15.2  | 9500  | 0.2793          | 0.3413 |
| 0.5631        | 16.0  | 10000 | 0.2789          | 0.3353 |
| 0.5446        | 16.8  | 10500 | 0.2709          | 0.3264 |
| 0.528         | 17.6  | 11000 | 0.2693          | 0.3234 |
| 0.5169        | 18.4  | 11500 | 0.2656          | 0.3193 |
| 0.5041        | 19.2  | 12000 | 0.2575          | 0.3102 |
| 0.4971        | 20.0  | 12500 | 0.2584          | 0.3114 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id samitizerxu/wav2vec2-xls-r-300m-eo --dataset mozilla-foundation/common_voice_7_0 --config eo --split test
```