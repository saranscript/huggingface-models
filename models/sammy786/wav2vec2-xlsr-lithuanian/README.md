---
language:
- lt
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- lt
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-lithuanian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: lt
    metrics:
       - name: Test WER
         type: wer
         value: 14.67
       - name: Test CER
         type: cer
         value: 2.77
---
# sammy786/wav2vec2-xlsr-lithuanian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - lt dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 13.1811
- Wer: 24.2570

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
- num_epochs: 40
- mixed_precision_training: Native AMP


### Training results


| Step  | Training Loss | Validation Loss | Wer      |
|:-----:|:-------------:|:---------------:|:--------:|
| 200   | 5.718700      | 2.897032        | 1.000000 |
| 400   | 1.340000      | 0.309548        | 0.507284 |
| 600   | 0.799100      | 0.220205        | 0.402098 |
| 800   | 0.494400      | 0.185093        | 0.352855 |
| 1000  | 0.370800      | 0.165869        | 0.334207 |
| 1200  | 0.312500      | 0.159801        | 0.324009 |
| 1400  | 0.276100      | 0.148066        | 0.321678 |
| 1600  | 0.250100      | 0.153748        | 0.311626 |
| 1800  | 0.226400      | 0.147437        | 0.302885 |
| 2000  | 0.206900      | 0.141176        | 0.296037 |
| 2200  | 0.189900      | 0.142161        | 0.288170 |
| 2400  | 0.192100      | 0.138029        | 0.286568 |
| 2600  | 0.175600      | 0.139496        | 0.283654 |
| 2800  | 0.156900      | 0.138609        | 0.283217 |
| 3000  | 0.149400      | 0.140468        | 0.281906 |
| 3200  | 0.144600      | 0.132472        | 0.278263 |
| 3400  | 0.144100      | 0.141028        | 0.277535 |
| 3600  | 0.133000      | 0.134287        | 0.275495 |
| 3800  | 0.126600      | 0.149136        | 0.277681 |
| 4000  | 0.123500      | 0.132180        | 0.266463 |
| 4200  | 0.113000      | 0.137942        | 0.268211 |
| 4400  | 0.111700      | 0.140038        | 0.272873 |
| 4600  | 0.108600      | 0.136756        | 0.264132 |
| 4800  | 0.103600      | 0.137541        | 0.263403 |
| 5000  | 0.098000      | 0.140435        | 0.264860 |
| 5200  | 0.095800      | 0.136950        | 0.262383 |
| 5400  | 0.094000      | 0.128214        | 0.263986 |
| 5600  | 0.085300      | 0.125024        | 0.259761 |
| 5800  | 0.078900      | 0.128575        | 0.260198 |
| 6000  | 0.083300      | 0.135496        | 0.258887 |
| 6200  | 0.078800      | 0.131706        | 0.259178 |
| 6400  | 0.073800      | 0.128451        | 0.255390 |
| 6600  | 0.072600      | 0.131245        | 0.252768 |
| 6800  | 0.073300      | 0.131525        | 0.249417 |
| 7000  | 0.069000      | 0.128627        | 0.255536 |
| 7200  | 0.064400      | 0.127767        | 0.250583 |
| 7400  | 0.065400      | 0.129557        | 0.247815 |
| 7600  | 0.061200      | 0.129734        | 0.250146 |
| 7800  | 0.059100      | 0.135124        | 0.249709 |
| 8000  | 0.057000      | 0.132850        | 0.249126 |
| 8200  | 0.056100      | 0.128827        | 0.248252 |
| 8400  | 0.056400      | 0.130229        | 0.246795 |
| 8600  | 0.052800      | 0.128939        | 0.245775 |
| 8800  | 0.051100      | 0.131892        | 0.248543 |
| 9000  | 0.052900      | 0.132062        | 0.244464 |
| 9200  | 0.048200      | 0.130988        | 0.244172 |
| 9400  | 0.047700      | 0.131811        | 0.242570 |
| 9600  | 0.050000      | 0.133832        | 0.245484 |
| 9800  | 0.047500      | 0.134340        | 0.243881 |
| 10000 | 0.048400      | 0.133388        | 0.243590 |
| 10200 | 0.047800      | 0.132729        | 0.244464 |
| 10400 | 0.049000      | 0.131695        | 0.245047 |
| 10600 | 0.044400      | 0.132154        | 0.245484 |
| 10800 | 0.050100      | 0.131575        | 0.245192 |
| 11000 | 0.047700      | 0.131211        | 0.245192 |
| 11200 | 0.046000      | 0.131293        | 0.245047 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-lithuanian --dataset mozilla-foundation/common_voice_8_0 --config lt --split test
```