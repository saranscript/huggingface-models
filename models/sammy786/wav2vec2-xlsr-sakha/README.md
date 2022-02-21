---
language:
- sah
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- sah
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-sakha
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sah
    metrics:
       - name: Test WER
         type: wer
         value: 36.15
       - name: Test CER
         type: cer
         value: 8.06
---
# sammy786/wav2vec2-xlsr-sakha

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - sah dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 21.39
- Wer: 30.99

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
- num_epochs: 15
- mixed_precision_training: Native AMP


### Training results


| Step | Training Loss | Validation Loss | Wer      |
|------|---------------|-----------------|----------|
| 200  | 4.541600      | 1.044711        | 0.926395 |
| 400  | 1.013700      | 0.290368        | 0.401758 |
| 600  | 0.645000      | 0.232261        | 0.346555 |
| 800  | 0.467800      | 0.214120        | 0.318340 |
| 1000 | 0.502300      | 0.213995        | 0.309957 |



### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-sakha --dataset mozilla-foundation/common_voice_8_0 --config sah --split test
```