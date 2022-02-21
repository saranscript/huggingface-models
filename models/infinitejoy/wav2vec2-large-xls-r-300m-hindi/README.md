---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- hi
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Hindi
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: hi
    metrics:
       - name: Test WER
         type: wer
         value: 100
       - name: Test CER
         type: cer
         value: 92.98
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-hindi

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5414
- Wer: 1.0194

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 4.6095        | 3.38  | 500   | 4.5881          | 0.9999 |
| 3.3396        | 6.76  | 1000  | 3.3301          | 1.0001 |
| 2.0061        | 10.14 | 1500  | 1.2096          | 1.0063 |
| 1.523         | 13.51 | 2000  | 0.7836          | 1.0051 |
| 1.3868        | 16.89 | 2500  | 0.6837          | 1.0080 |
| 1.2807        | 20.27 | 3000  | 0.6568          | 1.0112 |
| 1.231         | 23.65 | 3500  | 0.6120          | 1.0105 |
| 1.1673        | 27.03 | 4000  | 0.5972          | 1.0089 |
| 1.1416        | 30.41 | 4500  | 0.5780          | 1.0132 |
| 1.0738        | 33.78 | 5000  | 0.5806          | 1.0123 |
| 1.0771        | 37.16 | 5500  | 0.5586          | 1.0067 |
| 1.0287        | 40.54 | 6000  | 0.5464          | 1.0058 |
| 1.0106        | 43.92 | 6500  | 0.5407          | 1.0062 |
| 0.9538        | 47.3  | 7000  | 0.5334          | 1.0089 |
| 0.9607        | 50.68 | 7500  | 0.5395          | 1.0110 |
| 0.9108        | 54.05 | 8000  | 0.5502          | 1.0137 |
| 0.9252        | 57.43 | 8500  | 0.5498          | 1.0062 |
| 0.8943        | 60.81 | 9000  | 0.5448          | 1.0158 |
| 0.8728        | 64.19 | 9500  | 0.5257          | 1.0113 |
| 0.8577        | 67.57 | 10000 | 0.5550          | 1.0178 |
| 0.8332        | 70.95 | 10500 | 0.5607          | 1.0166 |
| 0.8174        | 74.32 | 11000 | 0.5429          | 1.0145 |
| 0.8168        | 77.7  | 11500 | 0.5561          | 1.0116 |
| 0.7872        | 81.08 | 12000 | 0.5478          | 1.0164 |
| 0.7707        | 84.46 | 12500 | 0.5412          | 1.0216 |
| 0.7742        | 87.84 | 13000 | 0.5391          | 1.0207 |
| 0.7594        | 91.22 | 13500 | 0.5379          | 1.0208 |
| 0.7678        | 94.59 | 14000 | 0.5415          | 1.0198 |
| 0.7502        | 97.97 | 14500 | 0.5409          | 1.0191 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
