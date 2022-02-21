---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-large-xlsr-coraa-portuguese-cv8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-coraa-portuguese-cv8

This model is a fine-tuned version of [Edresson/wav2vec2-large-xlsr-coraa-portuguese](https://huggingface.co/Edresson/wav2vec2-large-xlsr-coraa-portuguese) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1626
- Wer: 0.1365

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

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.5614        | 0.1   | 100  | 0.2542          | 0.1986 |
| 0.5181        | 0.19  | 200  | 0.2740          | 0.2146 |
| 0.5056        | 0.29  | 300  | 0.2472          | 0.2068 |
| 0.4747        | 0.39  | 400  | 0.2464          | 0.2166 |
| 0.4627        | 0.48  | 500  | 0.2277          | 0.2041 |
| 0.4403        | 0.58  | 600  | 0.2245          | 0.1977 |
| 0.4413        | 0.68  | 700  | 0.2156          | 0.1968 |
| 0.437         | 0.77  | 800  | 0.2102          | 0.1919 |
| 0.4305        | 0.87  | 900  | 0.2130          | 0.1864 |
| 0.4324        | 0.97  | 1000 | 0.2144          | 0.1902 |
| 0.4217        | 1.06  | 1100 | 0.2230          | 0.1891 |
| 0.3823        | 1.16  | 1200 | 0.2033          | 0.1774 |
| 0.3641        | 1.25  | 1300 | 0.2143          | 0.1830 |
| 0.3707        | 1.35  | 1400 | 0.2034          | 0.1793 |
| 0.3767        | 1.45  | 1500 | 0.2029          | 0.1823 |
| 0.3483        | 1.54  | 1600 | 0.1999          | 0.1740 |
| 0.3577        | 1.64  | 1700 | 0.1928          | 0.1728 |
| 0.3667        | 1.74  | 1800 | 0.1898          | 0.1726 |
| 0.3283        | 1.83  | 1900 | 0.1920          | 0.1688 |
| 0.3571        | 1.93  | 2000 | 0.1904          | 0.1649 |
| 0.3467        | 2.03  | 2100 | 0.1994          | 0.1648 |
| 0.3145        | 2.12  | 2200 | 0.1940          | 0.1682 |
| 0.3186        | 2.22  | 2300 | 0.1879          | 0.1571 |
| 0.3058        | 2.32  | 2400 | 0.1975          | 0.1678 |
| 0.3096        | 2.41  | 2500 | 0.1877          | 0.1589 |
| 0.2964        | 2.51  | 2600 | 0.1862          | 0.1568 |
| 0.3068        | 2.61  | 2700 | 0.1809          | 0.1588 |
| 0.3036        | 2.7   | 2800 | 0.1769          | 0.1573 |
| 0.3084        | 2.8   | 2900 | 0.1836          | 0.1524 |
| 0.3109        | 2.9   | 3000 | 0.1807          | 0.1519 |
| 0.2969        | 2.99  | 3100 | 0.1851          | 0.1516 |
| 0.2698        | 3.09  | 3200 | 0.1737          | 0.1490 |
| 0.2703        | 3.19  | 3300 | 0.1759          | 0.1457 |
| 0.2759        | 3.28  | 3400 | 0.1778          | 0.1471 |
| 0.2728        | 3.38  | 3500 | 0.1717          | 0.1462 |
| 0.2398        | 3.47  | 3600 | 0.1767          | 0.1451 |
| 0.256         | 3.57  | 3700 | 0.1742          | 0.1410 |
| 0.2712        | 3.67  | 3800 | 0.1674          | 0.1414 |
| 0.2648        | 3.76  | 3900 | 0.1717          | 0.1423 |
| 0.2576        | 3.86  | 4000 | 0.1672          | 0.1403 |
| 0.2504        | 3.96  | 4100 | 0.1683          | 0.1381 |
| 0.2406        | 4.05  | 4200 | 0.1685          | 0.1399 |
| 0.2403        | 4.15  | 4300 | 0.1656          | 0.1381 |
| 0.2233        | 4.25  | 4400 | 0.1687          | 0.1371 |
| 0.2546        | 4.34  | 4500 | 0.1642          | 0.1377 |
| 0.2431        | 4.44  | 4600 | 0.1655          | 0.1372 |
| 0.2337        | 4.54  | 4700 | 0.1625          | 0.1370 |
| 0.2607        | 4.63  | 4800 | 0.1618          | 0.1363 |
| 0.2292        | 4.73  | 4900 | 0.1622          | 0.1366 |
| 0.2232        | 4.83  | 5000 | 0.1626          | 0.1365 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
