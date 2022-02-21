---
language:
- cv
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- cv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-chuvash
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: cv
    metrics:
       - name: Test WER
         type: wer
         value: 27.81
       - name: Test CER
         type: cer
         value: 5.79
---
# sammy786/wav2vec2-xlsr-chuvash

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - cv dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 18.02
- Wer: 29.22

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
| 200  | 6.559100      | 2.274687        | 1.000000 |
| 400  | 1.346100      | 0.508268        | 0.681995 |
| 600  | 0.797500      | 0.391174        | 0.572876 |
| 800  | 0.556300      | 0.308620        | 0.489283 |
| 1000 | 0.435800      | 0.273956        | 0.454014 |
| 1200 | 0.388700      | 0.311027        | 0.499415 |
| 1400 | 0.338300      | 0.243977        | 0.413874 |
| 1600 | 0.294000      | 0.214134        | 0.385230 |
| 1800 | 0.276000      | 0.245991        | 0.397311 |
| 2000 | 0.253900      | 0.208324        | 0.363016 |
| 2200 | 0.233600      | 0.222156        | 0.370811 |
| 2400 | 0.219700      | 0.202602        | 0.364186 |
| 2600 | 0.205000      | 0.241339        | 0.384451 |
| 2800 | 0.176000      | 0.263558        | 0.384061 |
| 3000 | 0.166700      | 0.211768        | 0.333398 |
| 3200 | 0.160600      | 0.198677        | 0.321512 |
| 3400 | 0.154600      | 0.208655        | 0.328722 |
| 3600 | 0.146800      | 0.188022        | 0.317810 |
| 3800 | 0.133200      | 0.181083        | 0.313133 |
| 4000 | 0.134200      | 0.190084        | 0.316251 |
| 4200 | 0.114200      | 0.193034        | 0.312159 |
| 4400 | 0.117300      | 0.194122        | 0.312354 |
| 4600 | 0.112300      | 0.191111        | 0.305534 |
| 4800 | 0.107800      | 0.185930        | 0.302611 |
| 5000 | 0.100400      | 0.178625        | 0.299883 |
| 5200 | 0.099800      | 0.176442        | 0.294622 |
| 5400 | 0.100800      | 0.177935        | 0.294427 |
| 5600 | 0.096300      | 0.182903        | 0.293843 |
| 5800 | 0.094200      | 0.181041        | 0.293453 |
| 6000 | 0.097600      | 0.179865        | 0.290725 |
| 6200 | 0.091600      | 0.180327        | 0.292868 |
| 6400 | 0.093100      | 0.180275        | 0.292284 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-chuvash --dataset mozilla-foundation/common_voice_8_0 --config cv --split test
```