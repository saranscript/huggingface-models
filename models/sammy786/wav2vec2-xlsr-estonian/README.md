---
language:
- et
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- et
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-estonian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: et
    metrics:
       - name: Test WER
         type: wer
         value: 23.61
       - name: Test CER
         type: cer
         value: 4.60
---
# sammy786/wav2vec2-xlsr-estonian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - et dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 17.94
- Wer: 30.38

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
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP


### Training results


| Step | Training Loss | Validation Loss | Wer      |
|------|---------------|-----------------|----------|
| 200  | 3.729100      | 1.096018        | 0.959867 |
| 400  | 0.996900      | 0.310228        | 0.443600 |
| 600  | 0.762900      | 0.210873        | 0.346117 |
| 800  | 0.621400      | 0.200381        | 0.331513 |
| 1000 | 0.408000      | 0.196382        | 0.322014 |
| 1200 | 0.320200      | 0.176281        | 0.312515 |
| 1400 | 0.315300      | 0.179433        | 0.303847 |
| 1600 | 0.445800      | 0.420985        | 0.315839 |
| 1800 | 0.644600      | 0.433833        | 0.354904 |
| 2000 | 0.550900      | 0.327117        | 0.336500 |
| 2200 | 0.498600      | 0.289830        | 0.325457 |
| 2400 | 0.488300      | 0.294309        | 0.314177 |
| 2600 | 0.491700      | 0.311175        | 0.318689 |
| 2800 | 0.508500      | 0.314744        | 0.320470 |
| 3000 | 0.499900      | 0.314834        | 0.320589 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-estonian --dataset mozilla-foundation/common_voice_8_0 --config et --split test
```