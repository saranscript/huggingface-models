---
language:
- rm-vallader
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- rm-vallader
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-romansh_vallader
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: rm-vallader
    metrics:
       - name: Test WER
         type: wer
         value: 28.54
       - name: Test CER
         type: cer
         value: 6.57
---
# sammy786/wav2vec2-xlsr-romansh_vallader

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - rm-vallader dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 30.31
- Wer: 26.32

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 13
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 40
- mixed_precision_training: Native AMP


### Training results


| Step | Training Loss | Validation Loss | Wer      |
|------|---------------|-----------------|----------|
| 200  | 5.895100      | 3.136624        | 0.999713 |
| 400  | 1.545700      | 0.445069        | 0.471584 |
| 600  | 0.693900      | 0.340700        | 0.363088 |
| 800  | 0.510600      | 0.295432        | 0.289610 |
| 1000 | 0.318800      | 0.286795        | 0.281860 |
| 1200 | 0.194000      | 0.307468        | 0.274110 |
| 1400 | 0.151800      | 0.304849        | 0.264351 |
| 1600 | 0.148300      | 0.303112        | 0.263203 |



### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-romansh_vallader --dataset mozilla-foundation/common_voice_8_0 --config rm-vallader --split test
```