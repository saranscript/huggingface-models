---
language:
- ia
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: 'wav2vec2-large-xls-r-300m-ia'
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ia
    metrics:
       - name: Test WER using LM
         type: wer
         value: 8.6074
       - name: Test CER using LM
         type: cer
         value: 2.4147
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-ia

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1452
- Wer: 0.1253

## Training Procedure

Training is conducted in Google Colab, the training notebook provided in the repo

## Training and evaluation data

Language Model Created from texts from processed sentence in train + validation split of dataset (common voice 8.0 for Interlingua)
Evaluation is conducted in Notebook, you can see within the repo "notebook_evaluation_wav2vec2_ia.ipynb"

Test WER without LM
wer = 20.1776 %
cer = 4.7205 %

Test WER using 
wer = 8.6074 %
cer = 2.4147 %

evaluation using eval.py
```
huggingface-cli login #login to huggingface for getting auth token to access the common voice v8
#running with LM
python eval.py --model_id ayameRushia/wav2vec2-large-xls-r-300m-ia --dataset mozilla-foundation/common_voice_8_0 --config ia --split test --lm

# running without LM
python eval.py --model_id ayameRushia/wav2vec2-large-xls-r-300m-ia --dataset mozilla-foundation/common_voice_8_0 --config ia --split test
```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 16
- eval_batch_size: 4
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 400
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 7.432         | 1.87  | 400  | 2.9636          | 1.0    |
| 2.6922        | 3.74  | 800  | 2.2111          | 0.9977 |
| 1.2581        | 5.61  | 1200 | 0.4864          | 0.4028 |
| 0.6232        | 7.48  | 1600 | 0.2807          | 0.2413 |
| 0.4479        | 9.35  | 2000 | 0.2219          | 0.1885 |
| 0.3654        | 11.21 | 2400 | 0.1886          | 0.1606 |
| 0.323         | 13.08 | 2800 | 0.1716          | 0.1444 |
| 0.2935        | 14.95 | 3200 | 0.1687          | 0.1443 |
| 0.2707        | 16.82 | 3600 | 0.1632          | 0.1382 |
| 0.2559        | 18.69 | 4000 | 0.1507          | 0.1337 |
| 0.2433        | 20.56 | 4400 | 0.1572          | 0.1358 |
| 0.2338        | 22.43 | 4800 | 0.1489          | 0.1305 |
| 0.2258        | 24.3  | 5200 | 0.1485          | 0.1278 |
| 0.2218        | 26.17 | 5600 | 0.1470          | 0.1272 |
| 0.2169        | 28.04 | 6000 | 0.1470          | 0.1270 |
| 0.2117        | 29.91 | 6400 | 0.1452          | 0.1253 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
