---
language:
- ka
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- ka
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-czech
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ka
    metrics:
       - name: Test WER
         type: wer
         value: 23.90
       - name: Test CER
         type: cer
         value: 3.59
  
---
# sammy786/wav2vec2-xlsr-georgian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - ka dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 10.54
- Wer: 27.53

## Model description
"facebook/wav2vec2-xls-r-1b" was finetuned.

## Intended uses & limitations
More information needed
## Training and evaluation data
Training data - 
Common voice Finnish train.tsv, dev.tsv and other.tsv

## Training procedure
For creating the train dataset, all possible datasets were appended and 90-10 split was used. 

### Training hyperparameters

The following hyperparameters were used during training:

- learning_rate: 0.000045637994662983496
- train_batch_size: 8
- eval_batch_size: 16
- seed: 13
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP




### Training results


| Step | Training Loss | Validation Loss | Wer      |
|:----:|:-------------:|:---------------:|:--------:|
| 200  | 4.152100      | 0.823672        | 0.967814 |
| 400  | 0.889500      | 0.196740        | 0.444792 |
| 600  | 0.493700      | 0.155659        | 0.366115 |
| 800  | 0.328000      | 0.138066        | 0.358069 |
| 1000 | 0.260600      | 0.119236        | 0.324989 |
| 1200 | 0.217200      | 0.114050        | 0.313366 |
| 1400 | 0.188800      | 0.112600        | 0.302190 |
| 1600 | 0.166900      | 0.111154        | 0.295485 |
| 1800 | 0.155500      | 0.109963        | 0.286544 |
| 2000 | 0.140400      | 0.107587        | 0.277604 |
| 2200 | 0.142600      | 0.105662        | 0.277157 |
| 2400 | 0.135400      | 0.105414        | 0.275369 |



### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-georgian --dataset mozilla-foundation/common_voice_8_0 --config ka --split test
```