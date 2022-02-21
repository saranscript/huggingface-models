---
language:
- br
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Breton
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: br
    metrics:
       - name: Test WER
         type: wer
         value: 107.955
       - name: Test CER
         type: cer
         value: 379.33
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-breton

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - BR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6102
- Wer: 0.4455

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9205        | 3.33  | 500  | 2.8659          | 1.0    |
| 1.6403        | 6.67  | 1000 | 0.9440          | 0.7593 |
| 1.3483        | 10.0  | 1500 | 0.7580          | 0.6215 |
| 1.2255        | 13.33 | 2000 | 0.6851          | 0.5722 |
| 1.1139        | 16.67 | 2500 | 0.6409          | 0.5220 |
| 1.0688        | 20.0  | 3000 | 0.6245          | 0.5055 |
| 0.99          | 23.33 | 3500 | 0.6142          | 0.4874 |
| 0.9345        | 26.67 | 4000 | 0.5946          | 0.4829 |
| 0.9058        | 30.0  | 4500 | 0.6229          | 0.4704 |
| 0.8683        | 33.33 | 5000 | 0.6153          | 0.4666 |
| 0.8367        | 36.67 | 5500 | 0.5952          | 0.4542 |
| 0.8162        | 40.0  | 6000 | 0.6030          | 0.4541 |
| 0.8042        | 43.33 | 6500 | 0.5972          | 0.4485 |
| 0.7836        | 46.67 | 7000 | 0.6070          | 0.4497 |
| 0.7556        | 50.0  | 7500 | 0.6102          | 0.4455 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
