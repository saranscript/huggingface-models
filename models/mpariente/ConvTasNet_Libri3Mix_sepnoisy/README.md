---
tags:
- asteroid
- audio
- ConvTasNet
- audio-to-audio
datasets:
- LibriMix
- sep_noisy
license: cc-by-sa-4.0
---

## Asteroid model
Imported from this Zenodo [model page](https://zenodo.org/record/4020529).

## Description:
This model was trained by  Takhir Mirzaev using the Librimix/ConvTasNet recipe in Asteroid. 
It was trained on the `sep_noisy` task of the Libri3Mix dataset.
 

## Training config:
```yaml
data:
    n_src: 3
    sample_rate: 8000
    segment: 3
    task: sep_noisy
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
    skip_chan: 128
optim:
    lr: 0.001
    optimizer: adam
    weight_decay: 0.0
positional arguments:
training:
    batch_size: 4
    early_stop: True
    epochs: 200
    half_lr: True
    num_workers: 4
```
 

## Results:
```yaml
si_sdr: 6.824750632456865
si_sdr_imp: 11.234803761803752
sdr: 7.715799858488098
sdr_imp: 11.778681386239114
sir: 16.442141130818637
sir_imp: 19.527535070051055
sar: 8.757864265661263
sar_imp: -0.15657258049670303
stoi: 0.7854554136619554
stoi_imp: 0.22267957718163015 
```
 

## License notice:
This work "ConvTasNet_Libri3Mix_sepnoisy" 
is a derivative of [LibriSpeech ASR corpus](http://www.openslr.org/12) by 
[Vassil Panayotov](https://github.com/vdp),
used under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). 
"ConvTasNet_Libri3Mix_sepnoisy" 
is licensed under [Attribution-ShareAlike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/)
by Manuel Pariente.