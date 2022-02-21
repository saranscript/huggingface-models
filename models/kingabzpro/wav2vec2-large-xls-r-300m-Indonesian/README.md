---
language: 
- id

license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
metrics:
- wer
- cer
model-index:
- name: wav2vec2-large-xls-r-300m-Indonesian
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_7_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice id  # Required. Example: Common Voice zh-CN
      args: id         # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 25.06 # Required. Example: 20.90
        name: Test WER With LM   # Optional. Example: Test WER
    
      - type: cer    # Required. Example: wer
        value: 6.50  # Required. Example: 20.90
        name: Test CER With LM   # Optional. Example: Test WER
     

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-Indonesian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4087
- Wer: 0.2461
- Cer: 0.0666



### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 64
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 400
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 5.0788        | 4.26  | 200  | 2.9389          | 1.0    | 1.0    |
| 2.8288        | 8.51  | 400  | 2.2535          | 1.0    | 0.8004 |
| 0.907         | 12.77 | 600  | 0.4558          | 0.4243 | 0.1095 |
| 0.4071        | 17.02 | 800  | 0.4013          | 0.3468 | 0.0913 |
| 0.3           | 21.28 | 1000 | 0.4167          | 0.3075 | 0.0816 |
| 0.2544        | 25.53 | 1200 | 0.4132          | 0.2835 | 0.0762 |
| 0.2145        | 29.79 | 1400 | 0.3878          | 0.2693 | 0.0729 |
| 0.1923        | 34.04 | 1600 | 0.4023          | 0.2623 | 0.0702 |
| 0.1681        | 38.3  | 1800 | 0.3984          | 0.2581 | 0.0686 |
| 0.1598        | 42.55 | 2000 | 0.3982          | 0.2493 | 0.0663 |
| 0.1464        | 46.81 | 2200 | 0.4087          | 0.2461 | 0.0666 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
