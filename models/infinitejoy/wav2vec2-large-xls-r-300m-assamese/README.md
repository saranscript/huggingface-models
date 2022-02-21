---
license: apache-2.0
language: as
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning
- as
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Assamese
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: as
    metrics:
       - name: Test WER
         type: wer
         value: 72.64
       - name: Test CER
         type: cer
         value: 27.35
---

# wav2vec2-large-xls-r-300m-assamese

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice_7_0 dataset.
It achieves the following results on the evaluation set:

- WER: 0.7954545454545454
- CER: 0.32341269841269843

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

To compute the evaluation parameters

```bash
cd wav2vec2-large-xls-r-300m-assamese; python eval.py --model_id ./ --dataset mozilla-foundation/common_voice_7_0 --config as --split test --log_outputs
```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:

- learning_rate: 3e-4
- train_batch_size: 16
- eval_batch_size: 8
- seed: not given
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 400
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer      |
|:-------------:|:------:|:----:|:---------------:|:------:  |
| 1.584065      | NA     | 400  | 1.584065        | 0.915512 |
| 1.658865      | Na     | 800  | 1.658865        | 0.805096 |
| 1.882352      | NA     | 1200 | 1.882352        | 0.820742 |
| 1.881240      | NA     | 1600 | 1.881240        | 0.810907 |
| 2.159748      | NA     | 2000 | 2.159748        | 0.804202 |
| 1.992871      | NA     | 2400 | 1.992871        | 0.803308 |
| 2.201436      | NA     | 2800 | 2.201436        | 0.802861 |
| 2.165218      | NA     | 3200 | 2.165218        | 0.793920 |
| 2.253643      | NA     | 3600 | 2.253643        | 0.796603 |
| 2.265880      | NA     | 4000 | 2.265880        | 0.790344 |
| 2.293935      | NA     | 4400 | 2.293935        | 0.797050 |
| 2.288851      | NA     | 4800 | 2.288851        | 0.784086 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu113
- Datasets 1.13.3
- Tokenizers 0.10.3
