---
language:
- gn
license: apache-2.0
tags:
- automatic-speech-recognition
- generated_from_trainer
- gn
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-300m-gn-cv8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: pt
    metrics:
       - name: Test WER
         type: wer
         value: 69.05
       - name: Test CER
         type: cer
         value: 14.70
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-gn-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9392
- Wer: 0.7033

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- training_steps: 5000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 20.0601       | 5.54   | 100  | 5.1622          | 1.0    |
| 3.7052        | 11.11  | 200  | 3.2869          | 1.0    |
| 3.3275        | 16.65  | 300  | 3.2162          | 1.0    |
| 3.2984        | 22.22  | 400  | 3.1638          | 1.0    |
| 3.1111        | 27.76  | 500  | 2.5541          | 1.0    |
| 2.238         | 33.32  | 600  | 1.2198          | 0.9616 |
| 1.5284        | 38.86  | 700  | 0.9571          | 0.8593 |
| 1.2735        | 44.43  | 800  | 0.8719          | 0.8363 |
| 1.1269        | 49.97  | 900  | 0.8334          | 0.7954 |
| 1.0427        | 55.54  | 1000 | 0.7700          | 0.7749 |
| 1.0152        | 61.11  | 1100 | 0.7747          | 0.7877 |
| 0.943         | 66.65  | 1200 | 0.7151          | 0.7442 |
| 0.9132        | 72.22  | 1300 | 0.7224          | 0.7289 |
| 0.8397        | 77.76  | 1400 | 0.7354          | 0.7059 |
| 0.8577        | 83.32  | 1500 | 0.7285          | 0.7263 |
| 0.7931        | 88.86  | 1600 | 0.7863          | 0.7084 |
| 0.7995        | 94.43  | 1700 | 0.7562          | 0.6880 |
| 0.799         | 99.97  | 1800 | 0.7905          | 0.7059 |
| 0.7373        | 105.54 | 1900 | 0.7791          | 0.7161 |
| 0.749         | 111.11 | 2000 | 0.8125          | 0.7161 |
| 0.6925        | 116.65 | 2100 | 0.7722          | 0.6905 |
| 0.7034        | 122.22 | 2200 | 0.8989          | 0.7136 |
| 0.6745        | 127.76 | 2300 | 0.8270          | 0.6982 |
| 0.6837        | 133.32 | 2400 | 0.8569          | 0.7161 |
| 0.6689        | 138.86 | 2500 | 0.8339          | 0.6982 |
| 0.6471        | 144.43 | 2600 | 0.8441          | 0.7110 |
| 0.615         | 149.97 | 2700 | 0.9038          | 0.7212 |
| 0.6477        | 155.54 | 2800 | 0.9089          | 0.7059 |
| 0.6047        | 161.11 | 2900 | 0.9149          | 0.7059 |
| 0.5613        | 166.65 | 3000 | 0.8582          | 0.7263 |
| 0.6017        | 172.22 | 3100 | 0.8787          | 0.7084 |
| 0.5546        | 177.76 | 3200 | 0.8753          | 0.6957 |
| 0.5747        | 183.32 | 3300 | 0.9167          | 0.7212 |
| 0.5535        | 188.86 | 3400 | 0.8448          | 0.6905 |
| 0.5331        | 194.43 | 3500 | 0.8644          | 0.7161 |
| 0.5428        | 199.97 | 3600 | 0.8730          | 0.7033 |
| 0.5219        | 205.54 | 3700 | 0.9047          | 0.6982 |
| 0.5158        | 211.11 | 3800 | 0.8706          | 0.7033 |
| 0.5107        | 216.65 | 3900 | 0.9139          | 0.7084 |
| 0.4903        | 222.22 | 4000 | 0.9456          | 0.7315 |
| 0.4772        | 227.76 | 4100 | 0.9475          | 0.7161 |
| 0.4713        | 233.32 | 4200 | 0.9237          | 0.7059 |
| 0.4743        | 238.86 | 4300 | 0.9305          | 0.6957 |
| 0.4705        | 244.43 | 4400 | 0.9561          | 0.7110 |
| 0.4908        | 249.97 | 4500 | 0.9389          | 0.7084 |
| 0.4717        | 255.54 | 4600 | 0.9234          | 0.6982 |
| 0.4462        | 261.11 | 4700 | 0.9323          | 0.6957 |
| 0.4556        | 266.65 | 4800 | 0.9432          | 0.7033 |
| 0.4691        | 272.22 | 4900 | 0.9389          | 0.7059 |
| 0.4601        | 277.76 | 5000 | 0.9392          | 0.7033 |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.11.0
