---
language:
- km
license: apache-2.0
tags:
- automatic-speech-recognition
- openslr
- robust-speech-event
- km
- generated_from_trainer
datasets:
- openslr
model-index:
- name: wav2vec2-xls-r-1b-km
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: OpenSLR km
      type: openslr
      args: km
    metrics:
       - name: Test WER
         type: wer
         value: 32.13
       - name: Test CER
         type: cer
         value: 9.35
  - task:
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: km
    metrics:
       - name: Test WER
         type: wer
         value: 32.13
       - name: Test CER
         type: cer
         value: 9.35
---
# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the openslr dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4239
- Wer: 0.4221

# Evaluation results on OpenSLR "test" (self-split 10%) (Running ./eval.py):
- WER: 0.4490281634272114
- CER: 0.12198285179047481

# Evaluation results on OpenSLR "test" with LM ngram (self-split 10%) (Running ./eval.py):
- WER: 0.32130107100357
- CER: 0.09345053678218891

# Note
- Since this dataset is small (4 hours of voice recording), we decided not to train that for too long to avoid overfitting and under-generalization.
- This model performs worse than its 300M-variant. Probably, we don't explore the hyper-parameter enough?

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 75
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.5671        | 5.47  | 400  | 12.0218         | 1.0    |
| 3.5159        | 10.95 | 800  | 10.6337         | 1.0    |
| 2.4543        | 16.43 | 1200 | 1.8256          | 0.9839 |
| 1.9437        | 21.91 | 1600 | 1.1237          | 0.9173 |
| 1.696         | 27.39 | 2000 | 0.8246          | 0.7700 |
| 1.5342        | 32.87 | 2400 | 0.6433          | 0.6594 |
| 1.4509        | 38.35 | 2800 | 0.5500          | 0.5787 |
| 1.3478        | 43.83 | 3200 | 0.5070          | 0.4907 |
| 1.3096        | 49.31 | 3600 | 0.4692          | 0.4726 |
| 1.2532        | 54.79 | 4000 | 0.4448          | 0.4479 |
| 1.2291        | 60.27 | 4400 | 0.4374          | 0.4366 |
| 1.196         | 65.75 | 4800 | 0.4314          | 0.4310 |
| 1.1862        | 71.23 | 5200 | 0.4239          | 0.4221 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
