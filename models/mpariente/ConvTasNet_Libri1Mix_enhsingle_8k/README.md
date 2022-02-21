---
tags:
- asteroid
- audio
- ConvTasNet
datasets:
- LibriMix
- enh_single
license: cc-by-sa-4.0
---

## Asteroid model
Imported from this Zenodo [model page](https://zenodo.org/record/3970768).

## Description:
This model was trained by  Brij Mohan using the Librimix/ConvTasNet recipe in Asteroid. 
It was trained on the `enh_single` task of the Libri3Mix dataset.
 

## Training config:
```yaml
data:
    n_src: 1
    sample_rate: 8000
    segment: 3
    task: enh_single
    train_dir: data/wav8k/min/train-360
    valid_dir: data/wav8k/min/dev
filterbank:
    kernel_size: 16
    n_filters: 512
    stride: 8
masknet:
    bn_chan: 128
    hid_chan: 512
    mask_act: relu
    n_blocks: 8
    n_repeats: 3
    n_src: 1
    skip_chan: 128
optim:
    lr: 0.001
    optimizer: adam
    weight_decay: 0.0
training:
    batch_size: 24
    early_stop: True
    epochs: 200
    half_lr: True
```
 

## Results:
```yaml
si_sdr: 14.783675142685572
si_sdr_imp: 11.464625198953202
sdr: 15.497505907983102
sdr_imp: 12.07230150154914
sar: 15.497505907983102
sar_imp: 12.07230150154914
stoi: 0.9270030254700518
stoi_imp: 0.1320547197597893 
```
 

## License notice:
This work "ConvTasNet_Libri1Mix_enhsingle_8k" 
is a derivative of [LibriSpeech ASR corpus](http://www.openslr.org/12) by 
[Vassil Panayotov](https://github.com/vdp),
used under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). 
"ConvTasNet_Libri1Mix_enhsingle_8k" 
is licensed under [Attribution-ShareAlike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/)
by Manuel Pariente.