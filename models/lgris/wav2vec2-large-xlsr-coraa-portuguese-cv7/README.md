---
license: apache-2.0
tags:
- generated_from_trainer
- pt
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: wav2vec2-large-xlsr-coraa-portuguese-cv7
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-coraa-portuguese-cv7

This model is a fine-tuned version of [Edresson/wav2vec2-large-xlsr-coraa-portuguese](https://huggingface.co/Edresson/wav2vec2-large-xlsr-coraa-portuguese) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1777
- Wer: 0.1339

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
| 0.4779        | 0.13  | 100  | 0.2620          | 0.2020 |
| 0.4505        | 0.26  | 200  | 0.2339          | 0.1998 |
| 0.4285        | 0.39  | 300  | 0.2507          | 0.2109 |
| 0.4148        | 0.52  | 400  | 0.2311          | 0.2101 |
| 0.4072        | 0.65  | 500  | 0.2278          | 0.1899 |
| 0.388         | 0.78  | 600  | 0.2193          | 0.1898 |
| 0.3952        | 0.91  | 700  | 0.2108          | 0.1901 |
| 0.3851        | 1.04  | 800  | 0.2121          | 0.1788 |
| 0.3496        | 1.17  | 900  | 0.2154          | 0.1776 |
| 0.3063        | 1.3   | 1000 | 0.2095          | 0.1730 |
| 0.3376        | 1.43  | 1100 | 0.2129          | 0.1801 |
| 0.3273        | 1.56  | 1200 | 0.2132          | 0.1776 |
| 0.3347        | 1.69  | 1300 | 0.2054          | 0.1698 |
| 0.323         | 1.82  | 1400 | 0.1986          | 0.1724 |
| 0.3079        | 1.95  | 1500 | 0.2005          | 0.1701 |
| 0.3029        | 2.08  | 1600 | 0.2159          | 0.1644 |
| 0.2694        | 2.21  | 1700 | 0.1992          | 0.1678 |
| 0.2733        | 2.34  | 1800 | 0.2032          | 0.1657 |
| 0.269         | 2.47  | 1900 | 0.2056          | 0.1592 |
| 0.2869        | 2.6   | 2000 | 0.2058          | 0.1616 |
| 0.2813        | 2.73  | 2100 | 0.1868          | 0.1584 |
| 0.2616        | 2.86  | 2200 | 0.1841          | 0.1550 |
| 0.2809        | 2.99  | 2300 | 0.1902          | 0.1577 |
| 0.2598        | 3.12  | 2400 | 0.1910          | 0.1514 |
| 0.24          | 3.25  | 2500 | 0.1971          | 0.1555 |
| 0.2481        | 3.38  | 2600 | 0.1853          | 0.1537 |
| 0.2437        | 3.51  | 2700 | 0.1897          | 0.1496 |
| 0.2384        | 3.64  | 2800 | 0.1842          | 0.1495 |
| 0.2405        | 3.77  | 2900 | 0.1884          | 0.1500 |
| 0.2372        | 3.9   | 3000 | 0.1950          | 0.1548 |
| 0.229         | 4.03  | 3100 | 0.1928          | 0.1477 |
| 0.2047        | 4.16  | 3200 | 0.1891          | 0.1472 |
| 0.2102        | 4.29  | 3300 | 0.1930          | 0.1473 |
| 0.199         | 4.42  | 3400 | 0.1914          | 0.1456 |
| 0.2121        | 4.55  | 3500 | 0.1840          | 0.1437 |
| 0.211         | 4.67  | 3600 | 0.1843          | 0.1403 |
| 0.2072        | 4.8   | 3700 | 0.1836          | 0.1428 |
| 0.2224        | 4.93  | 3800 | 0.1747          | 0.1412 |
| 0.1974        | 5.06  | 3900 | 0.1813          | 0.1416 |
| 0.1895        | 5.19  | 4000 | 0.1869          | 0.1406 |
| 0.1763        | 5.32  | 4100 | 0.1830          | 0.1394 |
| 0.2001        | 5.45  | 4200 | 0.1775          | 0.1394 |
| 0.1909        | 5.58  | 4300 | 0.1806          | 0.1373 |
| 0.1812        | 5.71  | 4400 | 0.1784          | 0.1359 |
| 0.1737        | 5.84  | 4500 | 0.1778          | 0.1353 |
| 0.1915        | 5.97  | 4600 | 0.1777          | 0.1349 |
| 0.1921        | 6.1   | 4700 | 0.1784          | 0.1359 |
| 0.1805        | 6.23  | 4800 | 0.1757          | 0.1348 |
| 0.1742        | 6.36  | 4900 | 0.1771          | 0.1341 |
| 0.1709        | 6.49  | 5000 | 0.1777          | 0.1339 |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
