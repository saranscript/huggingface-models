---
tags:
- asteroid
- audio
- MultiDecoderDPRNN
datasets:
- Wsj0MixVar
- sep_clean
license: cc-by-sa-4.0
---
## Asteroid model

## Description:
- Code: The code corresponding to this pretrained model can be found in [this asteroid recipe](https://github.com/asteroid-team/asteroid/tree/master/egs/wsj0-mix-var/Multi-Decoder-DPRNN).

- [Paper](https://ieeexplore.ieee.org/document/9414205): "Multi-Decoder DPRNN: High Accuracy Source Counting and Separation", Junzhe Zhu, Raymond Yeh, Mark Hasegawa-Johnson. ICASSP(2021). 

- Summary: This model achieves SOTA on the problem of source separation with an unknown number of speakers. It uses multiple decoder heads(each tackling a distinct number of speakers), in addition to a classifier head that selects which decoder head to use.

- [Demo Page](https://junzhejosephzhu.github.io/Multi-Decoder-DPRNN/)

- [Original research repo](https://github.com/JunzheJosephZhu/MultiDecoder-DPRNN)

This model was trained by Joseph Zhu using the wsj0-mix-var/Multi-Decoder-DPRNN recipe in Asteroid. 
It was trained on the `sep_count` task of the Wsj0MixVar dataset.
 
## Training config:
```yaml
filterbank:
  n_filters: 64
  kernel_size: 8
  stride: 4
masknet:
  n_srcs: [2, 3, 4, 5]
  bn_chan: 128
  hid_size: 128
  chunk_size: 128
  hop_size: 64
  n_repeats: 8
  mask_act: 'sigmoid'
  bidirectional: true
  dropout: 0
  use_mulcat: false
training:
  epochs: 200
  batch_size: 2
  num_workers: 2
  half_lr: yes
  lr_decay: yes
  early_stop: yes
  gradient_clipping: 5
optim:
  optimizer: adam
  lr: 0.001
  weight_decay: 0.00000
data:
  train_dir: "data/{}speakers/wav8k/min/tr"
  valid_dir: "data/{}speakers/wav8k/min/cv"
  task: sep_count
  sample_rate: 8000
  seglen: 4.0
  minlen: 2.0
loss:
  lambda: 0.05
```
 
## Results:
```yaml
'Accuracy': 0.9723333333333334, 'P-Si-SNR': 10.36027378628496
```

### License notice:
This work "MultiDecoderDPRNN" is a derivative of [CSR-I (WSJ0) Complete](https://catalog.ldc.upenn.edu/LDC93S6A)
by [LDC](https://www.ldc.upenn.edu/), used under [LDC User Agreement for 
Non-Members](https://catalog.ldc.upenn.edu/license/ldc-non-members-agreement.pdf) (Research only). 
"MultiDecoderDPRNN" is licensed under [Attribution-ShareAlike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/)
by Joseph Zhu.
