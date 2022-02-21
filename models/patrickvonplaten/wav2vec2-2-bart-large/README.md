---
tags:
- automatic-speech-recognition
- librispeech_asr
- generated_from_trainer
- asr_seq2esq
widget:
- example_title: Librispeech sample 1
  src: https://cdn-media.huggingface.co/speech_samples/sample1.flac
- example_title: Librispeech sample 2
  src: https://cdn-media.huggingface.co/speech_samples/sample2.flac
- example_title: Common Voice sample
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_en_18301577.mp3
model-index:
- name: wav2vec2-2-bart-large
  results: []
---

To rerun this experiment, please clone this directory and run:

```bash
python create_model.py
```
followed by

```bash
./run_librispeech.sh
```

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-2-bart-large

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) and [bart-large](https://huggingface.co/facebook/bart-large) on the librispeech_asr - clean dataset.
  
It achieves the following results on the evaluation set:
- Loss: 0.3204
- Wer: 0.0486

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 4
- eval_batch_size: 4
- gradient_accumulation_steps: 2
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 64
- total_eval_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

See Training Metrics Tab.


### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3