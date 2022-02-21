---
language: 
- id

license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
metrics:
- wer
- cer
model-index:
- name: wav2vec2-large-xls-r-1b-Indonesian
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice id  # Required. Example: Common Voice zh-CN
      args: id         # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 45.51 # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
    
      - type: cer    # Required. Example: wer
        value: 16.43  # Required. Example: 20.90
        name: Test CER    # Optional. Example: Test WER
     

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-1b-Indonesian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9550
- Wer: 0.4551
- Cer: 0.1643



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
| 3.663         | 7.69  | 200  | 0.7898          | 0.6039 | 0.1848 |
| 0.7424        | 15.38 | 400  | 1.0215          | 0.5615 | 0.1924 |
| 0.4494        | 23.08 | 600  | 1.0901          | 0.5249 | 0.1932 |
| 0.5075        | 30.77 | 800  | 1.1013          | 0.5079 | 0.1935 |
| 0.4671        | 38.46 | 1000 | 1.1034          | 0.4916 | 0.1827 |
| 0.1928        | 46.15 | 1200 | 0.9550          | 0.4551 | 0.1643 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
