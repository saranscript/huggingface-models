---
language:
- cs
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- cs
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
      args: cs
    metrics:
       - name: Test WER
         type: wer
         value: 11.22
       - name: Test CER
         type: cer
         value: 2.52
  
---
# sammy786/wav2vec2-xlsr-czech

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - cs dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 7.26
- Wer: 19.32

## Model description
"facebook/wav2vec2-xls-r-1b" was finetuned.

## Intended uses & limitations
More information needed
## Training and evaluation data
Training data - 
Common voice Finnish train.tsv, dev.tsv, invalidated.tsv and other.tsv

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
- num_epochs: 7
- mixed_precision_training: Native AMP


### Training results

| Step | Training Loss | Validation Loss | Wer      |
|:----:|:-------------:|:---------------:|:--------:|
| 200  | 6.654600      | 3.329486        | 1.000000 |
| 400  | 1.700600      | 0.317266        | 0.409446 |
| 600  | 0.767400      | 0.211371        | 0.313981 |
| 800  | 0.718600      | 0.167771        | 0.280676 |
| 1000 | 0.661700      | 0.142229        | 0.258938 |
| 1200 | 0.594400      | 0.137321        | 0.256275 |
| 1400 | 0.583900      | 0.132922        | 0.248418 |
| 1600 | 0.565100      | 0.117214        | 0.238640 |
| 1800 | 0.369600      | 0.116954        | 0.238291 |
| 2000 | 0.292800      | 0.109973        | 0.227509 |
| 2200 | 0.255400      | 0.104955        | 0.228120 |
| 2400 | 0.266800      | 0.097268        | 0.220525 |
| 2600 | 0.232700      | 0.096055        | 0.213584 |
| 2800 | 0.213700      | 0.097770        | 0.218866 |
| 3000 | 0.209900      | 0.091633        | 0.210485 |
| 3200 | 0.196800      | 0.090342        | 0.208739 |
| 3400 | 0.200500      | 0.082326        | 0.204767 |
| 3600 | 0.176800      | 0.085491        | 0.204068 |
| 3800 | 0.170000      | 0.081289        | 0.201231 |
| 4000 | 0.166200      | 0.080762        | 0.200227 |
| 4200 | 0.161700      | 0.076671        | 0.198001 |
| 4400 | 0.147000      | 0.077383        | 0.196997 |
| 4600 | 0.141900      | 0.076057        | 0.195862 |
| 4800 | 0.144800      | 0.074612        | 0.195120 |
| 5000 | 0.138900      | 0.073138        | 0.193985 |
| 5200 | 0.143900      | 0.072802        | 0.192894 |
| 5400 | 0.131100      | 0.072764        | 0.193723 |
| 5600 | 0.137000      | 0.072697        | 0.193679 |
| 5800 | 0.133300      | 0.072651        | 0.193286 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-czech --dataset mozilla-foundation/common_voice_8_0 --config cs --split test
```