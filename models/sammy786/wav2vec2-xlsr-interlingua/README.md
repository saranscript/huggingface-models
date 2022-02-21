---
language:
- ia
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- ia
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0

model-index:
- name: sammy786/wav2vec2-xlsr-interlingua
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ia
    metrics:
       - name: Test WER
         type: wer
         value: 16.81
       - name: Test CER
         type: cer
         value: 4.76
---
# sammy786/wav2vec2-xlsr-interlingua

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - ia dataset.
It achieves the following results on evaluation set (which is 10 percent of train data set merged with other and dev datasets):
- Loss: 5.44
- Wer: 19.78

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
- num_epochs: 30
- mixed_precision_training: Native AMP


### Training results


| Step | Training Loss | Validation Loss | Wer      |
|------|---------------|-----------------|----------|
| 200  | 4.649200      | 0.483339        | 0.511322 |
| 400  | 0.764700      | 0.133428        | 0.251288 |
| 600  | 0.563700      | 0.099292        | 0.227745 |
| 800  | 0.438800      | 0.087545        | 0.217445 |
| 1000 | 0.406800      | 0.072313        | 0.213848 |
| 1200 | 0.237500      | 0.066965        | 0.213766 |
| 1400 | 0.177800      | 0.064419        | 0.208126 |
| 1600 | 0.157100      | 0.065962        | 0.214011 |
| 1800 | 0.146600      | 0.059477        | 0.202076 |
| 2000 | 0.132800      | 0.055015        | 0.201831 |
| 2200 | 0.122000      | 0.055421        | 0.201749 |
| 2400 | 0.115700      | 0.054462        | 0.197826 |



### Framework versions
- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id sammy786/wav2vec2-xlsr-interlingua --dataset mozilla-foundation/common_voice_8_0 --config ia --split test
```