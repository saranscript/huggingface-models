---
language:
- ar
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- ar
- robust-speech-event
datasets:
- common_voice
model-index:
- name: XLS-R-300M - Arabic
  results:
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: ar
    metrics:
       - name: Test WER
         type: wer
         value: 1.0
       - name: Test CER
         type: cer
         value: 1.0

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-ar

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - AR dataset.
It achieves the following results on the evaluation set:
- eval_loss: 3.0191
- eval_wer: 1.0
- eval_runtime: 252.2389
- eval_samples_per_second: 30.217
- eval_steps_per_second: 0.476
- epoch: 1.0
- step: 340

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 5
- mixed_precision_training: Native AMP

### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

#### Evaluation Commands

Please use the evaluation script `eval.py` included in the repo.

1. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id nouamanetazi/wav2vec2-xls-r-300m-ar --dataset speech-recognition-community-v2/dev_data --config ar --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```