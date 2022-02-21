---
language:
- ky
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- ky
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-kyrgyz
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ky
    metrics:
       - name: Test WER
         type: wer
         value: 25.24
       - name: Test CER
         type: cer
         value: 6.25
---
# sammy786/wav2vec2-xlsr-kyrgyz

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - ky dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 43.06
- Wer: 39.19

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
| 200  | 5.357800      | 2.700367        | 1.000000 |
| 400  | 1.513600      | 0.642542        | 0.598820 |
| 600  | 0.961900      | 0.530665        | 0.502739 |
| 800  | 0.776000      | 0.507709        | 0.462705 |
| 1000 | 0.646100      | 0.453115        | 0.444164 |
| 1200 | 0.581200      | 0.454797        | 0.438264 |
| 1400 | 0.437900      | 0.459389        | 0.426464 |
| 1600 | 0.348600      | 0.401247        | 0.416351 |
| 1800 | 0.312800      | 0.436135        | 0.409608 |
| 2000 | 0.294100      | 0.440911        | 0.398651 |
| 2200 | 0.281400      | 0.432729        | 0.394016 |
| 2400 | 0.258400      | 0.429860        | 0.393595 |
| 2600 | 0.263700      | 0.432689        | 0.395280 |
| 2800 | 0.256900      | 0.430672        | 0.391909 |


### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-kyrgyz --dataset mozilla-foundation/common_voice_8_0 --config ky --split test
```