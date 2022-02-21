---
language:
- mn
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: 'wav2vec2-large-xls-r-300m-mn'
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: mn
    metrics:
       - name: Test WER using LM
         type: wer
         value: 31.3919
       - name: Test CER using LM
         type: cer
         value: 10.2565
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - MN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5502
- Wer: 0.4042

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

Evaluation is conducted in Notebook, you can see within the repo "notebook_evaluation_wav2vec2_mn.ipynb"


Test WER without LM
wer = 58.2171 %
cer = 16.0670 %

Test WER using 
wer = 31.3919 %
cer = 10.2565 %

How to use eval.py
```
huggingface-cli login #login to huggingface for getting auth token to access the common voice v8
#running with LM
python eval.py --model_id ayameRushia/wav2vec2-large-xls-r-300m-mn --dataset mozilla-foundation/common_voice_8_0 --config mn --split test --lm

# running without LM
python eval.py --model_id ayameRushia/wav2vec2-large-xls-r-300m-mn --dataset mozilla-foundation/common_voice_8_0 --config mn --split test
```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 40.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 6.35  | 400  | 0.9380          | 0.7902 |
| 3.2674        | 12.7  | 800  | 0.5794          | 0.5309 |
| 0.7531        | 19.05 | 1200 | 0.5749          | 0.4815 |
| 0.5382        | 25.4  | 1600 | 0.5530          | 0.4447 |
| 0.4293        | 31.75 | 2000 | 0.5709          | 0.4237 |
| 0.4293        | 38.1  | 2400 | 0.5476          | 0.4059 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
