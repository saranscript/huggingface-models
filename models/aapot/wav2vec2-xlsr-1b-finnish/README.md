---
license: apache-2.0
language: fi
metrics:
- wer
- cer
tags:
- generated_from_trainer
- automatic-speech-recognition
- fi
- finnish
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: wav2vec2-xlsr-1b-finnish
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
         value: 13.11
       - name: Test CER
         type: cer
         value: 2.23

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xlsr-1b-finnish

**Note**: there is a better V2 version of this model which has been fine-tuned longer with 16 hours of more data: [aapot/wav2vec2-xlsr-1b-finnish-v2](https://huggingface.co/aapot/wav2vec2-xlsr-1b-finnish-v2)

**Note**: there is a language model version of this acoustic only model which achieves better test results thanks to the added language model: [aapot/wav2vec2-xlsr-1b-finnish-lm](https://huggingface.co/aapot/wav2vec2-xlsr-1b-finnish-lm)

This acoustic model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) for Finnish ASR. The model has been fine-tuned with 259.57 hours of Finnish transcribed speech data.
It achieves the following results on the Common Voice 7 test set together without language model:
- Wer: 13.11
- Cer: 2.23

## Model description

TODO

## Intended uses & limitations

TODO

## Training and evaluation data

This model was fine-tuned with 259.57 hours of Finnish transcribed speech data from following datasets:

| Dataset                                                                                                                       | Hours    | % of total hours |
|:------------------------------------------------------------------------------------------------------------------------------|:--------:|:----------------:|
| [Common Voice 7.0 Finnish train+evaluation+other splits](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) | 9.70 h   | 3.74 %           |
| [Finnish parliament session 2](https://b2share.eudat.eu/records/4df422d631544ce682d6af1d4714b2d4)                             | 0.24 h   | 0.09 %           |
| [VoxPopuli Finnish](https://github.com/facebookresearch/voxpopuli)                                                            | 5.94 h   | 2.29 %           |
| [CSS10 Finnish](https://github.com/kyubyong/css10)                                                                            | 10.32 h  | 3.98 %           |
| [Aalto Finnish Parliament ASR Corpus](http://urn.fi/urn:nbn:fi:lb-2021051903)                                                 | 228.00 h | 87.84 %          |
| [Finnish Broadcast Corpus](http://urn.fi/urn:nbn:fi:lb-2016042502)                                                            | 5.37 h   | 2.07 %           |

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: [8-bit Adam](https://github.com/facebookresearch/bitsandbytes) with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.968         | 0.18  | 500   | 0.4870          | 0.4720 |
| 0.6557        | 0.36  | 1000  | 0.2450          | 0.2931 |
| 0.647         | 0.54  | 1500  | 0.1818          | 0.2255 |
| 0.5297        | 0.72  | 2000  | 0.1698          | 0.2354 |
| 0.5802        | 0.9   | 2500  | 0.1581          | 0.2355 |
| 0.6351        | 1.07  | 3000  | 0.1689          | 0.2336 |
| 0.4626        | 1.25  | 3500  | 0.1719          | 0.3099 |
| 0.4526        | 1.43  | 4000  | 0.1434          | 0.2069 |
| 0.4692        | 1.61  | 4500  | 0.1645          | 0.2192 |
| 0.4584        | 1.79  | 5000  | 0.1483          | 0.1987 |
| 0.4234        | 1.97  | 5500  | 0.1499          | 0.2178 |
| 0.4243        | 2.15  | 6000  | 0.1345          | 0.2070 |
| 0.4108        | 2.33  | 6500  | 0.1383          | 0.1850 |
| 0.4048        | 2.51  | 7000  | 0.1338          | 0.1811 |
| 0.4085        | 2.69  | 7500  | 0.1290          | 0.1780 |
| 0.4026        | 2.87  | 8000  | 0.1239          | 0.1650 |
| 0.4033        | 3.04  | 8500  | 0.1346          | 0.1657 |
| 0.3986        | 3.22  | 9000  | 0.1310          | 0.1850 |
| 0.3867        | 3.4   | 9500  | 0.1273          | 0.1741 |
| 0.3658        | 3.58  | 10000 | 0.1219          | 0.1672 |
| 0.382         | 3.76  | 10500 | 0.1306          | 0.1698 |
| 0.3847        | 3.94  | 11000 | 0.1230          | 0.1577 |
| 0.3691        | 4.12  | 11500 | 0.1310          | 0.1615 |
| 0.3593        | 4.3   | 12000 | 0.1296          | 0.1622 |
| 0.3619        | 4.48  | 12500 | 0.1285          | 0.1601 |
| 0.3361        | 4.66  | 13000 | 0.1261          | 0.1569 |
| 0.3603        | 4.84  | 13500 | 0.1235          | 0.1533 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
