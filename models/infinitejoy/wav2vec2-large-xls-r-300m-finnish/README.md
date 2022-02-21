---
language:
- fi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- fi
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Finnish
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: fi
    metrics:
       - name: Test WER
         type: wer
         value: 29.97
       - name: Test CER
         type: cer
         value: NA
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-finnish

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - FI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2307
- Wer: 0.2984

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
- num_epochs: 70.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9032        | 4.39  | 500  | 2.8768          | 1.0    |
| 1.5724        | 8.77  | 1000 | 0.5638          | 0.6438 |
| 1.1818        | 13.16 | 1500 | 0.3338          | 0.4759 |
| 1.0798        | 17.54 | 2000 | 0.2876          | 0.4086 |
| 1.0296        | 21.93 | 2500 | 0.2694          | 0.4248 |
| 1.0014        | 26.32 | 3000 | 0.2626          | 0.3733 |
| 0.9616        | 30.7  | 3500 | 0.2391          | 0.3294 |
| 0.9303        | 35.09 | 4000 | 0.2352          | 0.3218 |
| 0.9248        | 39.47 | 4500 | 0.2351          | 0.3207 |
| 0.8837        | 43.86 | 5000 | 0.2341          | 0.3103 |
| 0.8887        | 48.25 | 5500 | 0.2311          | 0.3115 |
| 0.8529        | 52.63 | 6000 | 0.2230          | 0.3001 |
| 0.8404        | 57.02 | 6500 | 0.2279          | 0.3054 |
| 0.8242        | 61.4  | 7000 | 0.2298          | 0.3006 |
| 0.8288        | 65.79 | 7500 | 0.2333          | 0.2997 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
