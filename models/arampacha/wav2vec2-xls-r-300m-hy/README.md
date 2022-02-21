---
language:
- hy-AM
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-hy
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice hy-AM
      args: hy-AM
    metrics:
      - type: wer
        value: 13.192818110850899
        name: WER LM
      - type: cer
        value: 2.7870510875063228
        name: CER LM
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: hy
    metrics:
       - name: Test WER
         type: wer
         value: 22.246048764990867
       - name: Test CER
         type: cer
         value: 7.59406739840239
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the /WORKSPACE/DATA/HY/NOIZY_STUDENT_3/ - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2293
- Wer: 0.3333
- Cer: 0.0602

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7e-05
- train_batch_size: 64
- eval_batch_size: 64
- seed: 842
- gradient_accumulation_steps: 2
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.98) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.1
- training_steps: 4000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 3.1471        | 7.02  | 400  | 3.1599          | 1.0    | 1.0    |
| 1.8691        | 14.04 | 800  | 0.7674          | 0.7361 | 0.1686 |
| 1.3227        | 21.05 | 1200 | 0.3849          | 0.5336 | 0.1007 |
| 1.163         | 28.07 | 1600 | 0.3015          | 0.4559 | 0.0823 |
| 1.0768        | 35.09 | 2000 | 0.2721          | 0.4032 | 0.0728 |
| 1.0224        | 42.11 | 2400 | 0.2586          | 0.3825 | 0.0691 |
| 0.9817        | 49.12 | 2800 | 0.2458          | 0.3653 | 0.0653 |
| 0.941         | 56.14 | 3200 | 0.2306          | 0.3388 | 0.0605 |
| 0.9235        | 63.16 | 3600 | 0.2315          | 0.3380 | 0.0615 |
| 0.9141        | 70.18 | 4000 | 0.2293          | 0.3333 | 0.0602 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
