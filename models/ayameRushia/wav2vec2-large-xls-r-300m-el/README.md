---
language:
- el
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: 'wav2vec2-large-xls-r-300m-el'
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: el
    metrics:
       - name: Test WER using LM
         type: wer
         value: 20.7340
       - name: Test CER using LM
         type: cer
         value: 6.0466
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - EL dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3218
- Wer: 0.3095

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

Evaluation is conducted in Notebook, you can see within the repo "notebook_evaluation_wav2vec2_el.ipynb"

Test WER without LM
wer = 31.1294 %
cer = 7.9509 %

Test WER using LM
wer = 20.7340 %
cer = 6.0466 %

How to use eval.py
```
huggingface-cli login #login to huggingface for getting auth token to access the common voice v8
#running with LM
python eval.py --model_id ayameRushia/wav2vec2-large-xls-r-300m-el --dataset mozilla-foundation/common_voice_8_0 --config el --split test --lm

# running without LM
python eval.py --model_id ayameRushia/wav2vec2-large-xls-r-300m-el --dataset mozilla-foundation/common_voice_8_0 --config el --split test
```
## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 400
- num_epochs: 80.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 6.3683        | 8.77  | 500  | 3.1280          | 1.0    |
| 1.9915        | 17.54 | 1000 | 0.6600          | 0.6444 |
| 0.6565        | 26.32 | 1500 | 0.4208          | 0.4486 |
| 0.4484        | 35.09 | 2000 | 0.3885          | 0.4006 |
| 0.3573        | 43.86 | 2500 | 0.3548          | 0.3626 |
| 0.3063        | 52.63 | 3000 | 0.3375          | 0.3430 |
| 0.2751        | 61.4  | 3500 | 0.3359          | 0.3241 |
| 0.2511        | 70.18 | 4000 | 0.3222          | 0.3108 |
| 0.2361        | 78.95 | 4500 | 0.3205          | 0.3084 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
