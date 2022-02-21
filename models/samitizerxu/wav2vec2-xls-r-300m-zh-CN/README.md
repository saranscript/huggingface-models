---
language:
- zh-CN
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- robust-speech-event
- zh
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-zh-CN
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: zh-CN
    metrics:
       - name: Test WER
         type: wer
         value: 80
       - name: Test CER
         type: cer
         value: 40.11
  # - task: 
  #     name: Automatic Speech Recognition
  #     type: automatic-speech-recognition
  #   dataset:
  #     name: Robust Speech Event - Dev Data
  #     type: speech-recognition-community-v2/dev_data
  #     args: zh-CN
  #   metrics:
  #      - name: Test WER
  #        type: wer
  #        value: TBD
  #      - name: Test CER
  #        type: cer
  #        value: TBD
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-zh-CN

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - ZH-CN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8828
- Wer: 2.0604

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 60.2112       | 0.74  | 500   | 64.8189         | 1.0    |
| 8.1128        | 1.48  | 1000  | 6.8997          | 1.0    |
| 6.0492        | 2.22  | 1500  | 5.9677          | 1.9495 |
| 5.9326        | 2.95  | 2000  | 5.8845          | 1.4092 |
| 5.8763        | 3.69  | 2500  | 5.8460          | 1.6126 |
| 5.7888        | 4.43  | 3000  | 5.7545          | 2.2034 |
| 5.735         | 5.17  | 3500  | 5.6777          | 2.3350 |
| 5.6861        | 5.91  | 4000  | 5.5179          | 2.2232 |
| 5.381         | 6.65  | 4500  | 5.1420          | 2.1816 |
| 4.625         | 7.39  | 5000  | 3.9020          | 2.0722 |
| 4.214         | 8.12  | 5500  | 3.3394          | 2.1430 |
| 3.8992        | 8.86  | 6000  | 2.9085          | 2.1534 |
| 3.6481        | 9.6   | 6500  | 2.6208          | 2.3538 |
| 3.4658        | 10.34 | 7000  | 2.3172          | 2.2271 |
| 3.257         | 11.08 | 7500  | 2.0916          | 2.1351 |
| 3.1294        | 11.82 | 8000  | 1.8954          | 2.2133 |
| 3.0266        | 12.56 | 8500  | 1.7673          | 2.0896 |
| 2.9451        | 13.29 | 9000  | 1.6659          | 2.1381 |
| 2.8802        | 14.03 | 9500  | 1.5637          | 2.1969 |
| 2.78          | 14.77 | 10000 | 1.4921          | 2.2335 |
| 2.7049        | 15.51 | 10500 | 1.4132          | 2.2217 |
| 2.6768        | 16.25 | 11000 | 1.3667          | 2.2232 |
| 2.6358        | 16.99 | 11500 | 1.3111          | 2.1286 |
| 2.5802        | 17.72 | 12000 | 1.2679          | 2.1430 |
| 2.5012        | 18.46 | 12500 | 1.2365          | 2.1153 |
| 2.458         | 19.2  | 13000 | 1.2118          | 2.1573 |
| 2.4433        | 19.94 | 13500 | 1.1992          | 2.1336 |
| 2.438         | 20.68 | 14000 | 1.1803          | 2.1509 |
| 2.418         | 21.42 | 14500 | 1.1601          | 2.1232 |
| 2.3322        | 22.16 | 15000 | 1.1418          | 2.1930 |
| 2.3387        | 22.89 | 15500 | 1.1172          | 2.2464 |
| 2.3349        | 23.63 | 16000 | 1.1144          | 2.1856 |
| 2.291         | 24.37 | 16500 | 1.1018          | 2.1930 |
| 2.2766        | 25.11 | 17000 | 1.0883          | 2.1762 |
| 2.2534        | 25.85 | 17500 | 1.0744          | 2.1875 |
| 2.2393        | 26.59 | 18000 | 1.0561          | 2.1846 |
| 2.2085        | 27.33 | 18500 | 1.0466          | 2.1445 |
| 2.1966        | 28.06 | 19000 | 1.0382          | 2.1089 |
| 2.1794        | 28.8  | 19500 | 1.0264          | 1.9861 |
| 2.1423        | 29.54 | 20000 | 1.0246          | 1.9678 |
| 2.1649        | 30.28 | 20500 | 0.9982          | 2.0005 |
| 2.143         | 31.02 | 21000 | 0.9985          | 2.0450 |
| 2.1338        | 31.76 | 21500 | 0.9932          | 2.0025 |
| 2.1076        | 32.5  | 22000 | 0.9903          | 2.0505 |
| 2.0519        | 33.23 | 22500 | 0.9834          | 2.0737 |
| 2.0534        | 33.97 | 23000 | 0.9756          | 2.0247 |
| 2.0121        | 34.71 | 23500 | 0.9688          | 2.1440 |
| 2.0161        | 35.45 | 24000 | 0.9582          | 2.1232 |
| 2.0178        | 36.19 | 24500 | 0.9480          | 2.0896 |
| 2.0154        | 36.93 | 25000 | 0.9483          | 2.0787 |
| 1.9966        | 37.67 | 25500 | 0.9406          | 2.0297 |
| 1.9753        | 38.4  | 26000 | 0.9419          | 2.0346 |
| 1.9524        | 39.14 | 26500 | 0.9274          | 2.0698 |
| 1.9427        | 39.88 | 27000 | 0.9233          | 2.0787 |
| 1.9258        | 40.62 | 27500 | 0.9182          | 2.0529 |
| 1.9031        | 41.36 | 28000 | 0.9150          | 2.0787 |
| 1.9297        | 42.1  | 28500 | 0.9040          | 2.0505 |
| 1.9041        | 42.84 | 29000 | 0.9009          | 2.0579 |
| 1.8929        | 43.57 | 29500 | 0.8968          | 2.0327 |
| 1.9077        | 44.31 | 30000 | 0.8954          | 2.0619 |
| 1.8504        | 45.05 | 30500 | 0.8922          | 2.0737 |
| 1.8732        | 45.79 | 31000 | 0.8898          | 2.0683 |
| 1.877         | 46.53 | 31500 | 0.8849          | 2.0589 |
| 1.8587        | 47.27 | 32000 | 0.8843          | 2.0450 |
| 1.8236        | 48.01 | 32500 | 0.8810          | 2.0554 |
| 1.8392        | 48.74 | 33000 | 0.8820          | 2.0574 |
| 1.8428        | 49.48 | 33500 | 0.8816          | 2.0668 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id samitizerxu/wav2vec2-xls-r-300m-zh-CN --dataset mozilla-foundation/common_voice_7_0 --config zh-CN --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id samitizerxu/wav2vec2-xls-r-300m-zh-CN --dataset speech-recognition-community-v2/dev_data --config zh-CN --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```