---
language:
- ro
license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
- gigant/romanian_speech_synthesis_0_8_1
model-index:
- name: wav2vec2-ro-300m_01
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event
      type: speech-recognition-community-v2/dev_data
      args: ro
    metrics:
       - name: Dev WER (without LM)
         type: wer
         value: 46.99
       - name: Dev CER (without LM)
         type: cer
         value: 16.04
       - name: Dev WER (with LM)
         type: wer
         value: 38.63
       - name: Dev CER (with LM)
         type: cer
         value: 14.52
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice
      type: mozilla-foundation/common_voice_8_0
      args: ro
    metrics:
       - name: Test WER (without LM)
         type: wer
         value: 11.73
       - name: Test CER (without LM)
         type: cer
         value: 2.93
       - name: Test WER (with LM)
         type: wer
         value: 7.31
       - name: Test CER (with LM)
         type: cer
         value: 2.17
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Romanian Wav2Vec2

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the [Common Voice 8.0 - Romanian subset](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0) dataset, with extra training data from [Romanian Speech Synthesis](https://huggingface.co/datasets/gigant/romanian_speech_synthesis_0_8_1) dataset.

Without the 5-gram Language Model optimization, it achieves the following results on the evaluation set (Common Voice 8.0, Romanian subset, test split):
- Loss: 0.1553
- Wer: 0.1174
- Cer: 0.0294

## Model description

The architecture is based on [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) with a speech recognition CTC head and an added 5-gram language model (using [pyctcdecode](https://github.com/kensho-technologies/pyctcdecode) and [kenlm](https://github.com/kpu/kenlm)) trained on the [Romanian Corpora Parliament](gigant/ro_corpora_parliament_processed) dataset. Those libraries are needed in order for the language model-boosted decoder to work.

## Intended uses & limitations

More information needed

## Training and evaluation data

Training data :
- [Common Voice 8.0 - Romanian subset](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0) : train + validation + other splits
- [Romanian Speech Synthesis](https://huggingface.co/datasets/gigant/romanian_speech_synthesis_0_8_1) : train + test splits

Evaluation data :
- [Common Voice 8.0 - Romanian subset](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0) : test split

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 3
- total_train_batch_size: 48
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 2.9272        | 0.78  | 500   | 0.7603          | 0.7734 | 0.2355 |
| 0.6157        | 1.55  | 1000  | 0.4003          | 0.4866 | 0.1247 |
| 0.4452        | 2.33  | 1500  | 0.2960          | 0.3689 | 0.0910 |
| 0.3631        | 3.11  | 2000  | 0.2580          | 0.3205 | 0.0796 |
| 0.3153        | 3.88  | 2500  | 0.2465          | 0.2977 | 0.0747 |
| 0.2795        | 4.66  | 3000  | 0.2274          | 0.2789 | 0.0694 |
| 0.2615        | 5.43  | 3500  | 0.2277          | 0.2685 | 0.0675 |
| 0.2389        | 6.21  | 4000  | 0.2135          | 0.2518 | 0.0627 |
| 0.2229        | 6.99  | 4500  | 0.2054          | 0.2449 | 0.0614 |
| 0.2067        | 7.76  | 5000  | 0.2096          | 0.2378 | 0.0597 |
| 0.1977        | 8.54  | 5500  | 0.2042          | 0.2387 | 0.0600 |
| 0.1896        | 9.32  | 6000  | 0.2110          | 0.2383 | 0.0595 |
| 0.1801        | 10.09 | 6500  | 0.1909          | 0.2165 | 0.0548 |
| 0.174         | 10.87 | 7000  | 0.1883          | 0.2206 | 0.0559 |
| 0.1685        | 11.65 | 7500  | 0.1848          | 0.2097 | 0.0528 |
| 0.1591        | 12.42 | 8000  | 0.1851          | 0.2039 | 0.0514 |
| 0.1537        | 13.2  | 8500  | 0.1881          | 0.2065 | 0.0518 |
| 0.1504        | 13.97 | 9000  | 0.1840          | 0.1972 | 0.0499 |
| 0.145         | 14.75 | 9500  | 0.1845          | 0.2029 | 0.0517 |
| 0.1417        | 15.53 | 10000 | 0.1884          | 0.2003 | 0.0507 |
| 0.1364        | 16.3  | 10500 | 0.2010          | 0.2037 | 0.0517 |
| 0.1331        | 17.08 | 11000 | 0.1838          | 0.1923 | 0.0483 |
| 0.129         | 17.86 | 11500 | 0.1818          | 0.1922 | 0.0489 |
| 0.1198        | 18.63 | 12000 | 0.1760          | 0.1861 | 0.0465 |
| 0.1203        | 19.41 | 12500 | 0.1686          | 0.1839 | 0.0465 |
| 0.1225        | 20.19 | 13000 | 0.1828          | 0.1920 | 0.0479 |
| 0.1145        | 20.96 | 13500 | 0.1673          | 0.1784 | 0.0446 |
| 0.1053        | 21.74 | 14000 | 0.1802          | 0.1810 | 0.0456 |
| 0.1071        | 22.51 | 14500 | 0.1769          | 0.1775 | 0.0444 |
| 0.1053        | 23.29 | 15000 | 0.1920          | 0.1783 | 0.0457 |
| 0.1024        | 24.07 | 15500 | 0.1904          | 0.1775 | 0.0446 |
| 0.0987        | 24.84 | 16000 | 0.1793          | 0.1762 | 0.0446 |
| 0.0949        | 25.62 | 16500 | 0.1801          | 0.1766 | 0.0443 |
| 0.0942        | 26.4  | 17000 | 0.1731          | 0.1659 | 0.0423 |
| 0.0906        | 27.17 | 17500 | 0.1776          | 0.1698 | 0.0424 |
| 0.0861        | 27.95 | 18000 | 0.1716          | 0.1600 | 0.0406 |
| 0.0851        | 28.73 | 18500 | 0.1662          | 0.1630 | 0.0410 |
| 0.0844        | 29.5  | 19000 | 0.1671          | 0.1572 | 0.0393 |
| 0.0792        | 30.28 | 19500 | 0.1768          | 0.1599 | 0.0407 |
| 0.0798        | 31.06 | 20000 | 0.1732          | 0.1558 | 0.0394 |
| 0.0779        | 31.83 | 20500 | 0.1694          | 0.1544 | 0.0388 |
| 0.0718        | 32.61 | 21000 | 0.1709          | 0.1578 | 0.0399 |
| 0.0732        | 33.38 | 21500 | 0.1697          | 0.1523 | 0.0391 |
| 0.0708        | 34.16 | 22000 | 0.1616          | 0.1474 | 0.0375 |
| 0.0678        | 34.94 | 22500 | 0.1698          | 0.1474 | 0.0375 |
| 0.0642        | 35.71 | 23000 | 0.1681          | 0.1459 | 0.0369 |
| 0.0661        | 36.49 | 23500 | 0.1612          | 0.1411 | 0.0357 |
| 0.0629        | 37.27 | 24000 | 0.1662          | 0.1414 | 0.0355 |
| 0.0587        | 38.04 | 24500 | 0.1659          | 0.1408 | 0.0351 |
| 0.0581        | 38.82 | 25000 | 0.1612          | 0.1382 | 0.0352 |
| 0.0556        | 39.6  | 25500 | 0.1647          | 0.1376 | 0.0345 |
| 0.0543        | 40.37 | 26000 | 0.1658          | 0.1335 | 0.0337 |
| 0.052         | 41.15 | 26500 | 0.1716          | 0.1369 | 0.0343 |
| 0.0513        | 41.92 | 27000 | 0.1600          | 0.1317 | 0.0330 |
| 0.0491        | 42.7  | 27500 | 0.1671          | 0.1311 | 0.0328 |
| 0.0463        | 43.48 | 28000 | 0.1613          | 0.1289 | 0.0324 |
| 0.0468        | 44.25 | 28500 | 0.1599          | 0.1260 | 0.0315 |
| 0.0435        | 45.03 | 29000 | 0.1556          | 0.1232 | 0.0308 |
| 0.043         | 45.81 | 29500 | 0.1588          | 0.1240 | 0.0309 |
| 0.0421        | 46.58 | 30000 | 0.1567          | 0.1217 | 0.0308 |
| 0.04          | 47.36 | 30500 | 0.1533          | 0.1198 | 0.0302 |
| 0.0389        | 48.14 | 31000 | 0.1582          | 0.1185 | 0.0297 |
| 0.0387        | 48.91 | 31500 | 0.1576          | 0.1187 | 0.0297 |
| 0.0376        | 49.69 | 32000 | 0.1560          | 0.1182 | 0.0295 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
