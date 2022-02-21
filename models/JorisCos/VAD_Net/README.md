---
tags:
- asteroid
- audio
- VADNet
- VAD
- Voice Activity Detection
datasets:
- LibriVAD
license: cc-by-sa-4.0
---

## Asteroid model `JorisCos/VAD_Net`

Description:

This model was trained by Joris Cosentino using the librimix recipe in [Asteroid](https://github.com/asteroid-team/asteroid).
It was trained on the `enh_single` task of the Libri1Mix  dataset.

Training config:

```yml
data:
  segment: 3
  train_dir: /home/jcosentino/VAD_dataset/metadata/sets/train.json
  valid_dir: /home/jcosentino/VAD_dataset/metadata/sets/dev.json
filterbank:
  kernel_size: 16
  n_filters: 512
  stride: 8
main_args:
  exp_dir: exp/full_not_causal_f1/
  help: null
masknet:
  bn_chan: 128
  causal: false
  hid_chan: 512
  mask_act: relu
  n_blocks: 3
  n_repeats: 5
  skip_chan: 128
optim:
  lr: 0.001
  optimizer: adam
  weight_decay: 0.0
positional arguments: {}
training:
  batch_size: 8
  early_stop: true
  epochs: 200
  half_lr: true
  num_workers: 4
```
  

Results:

On LibriVAD min test set :
```yml
accuracy: 0.8196149023502931,
precision: 0.8305009048356607,
recall: 0.8869202491310206,
f1_score: 0.8426184545700124
```


License notice:

This work "VAD_Net" is a derivative of [LibriSpeech ASR corpus](http://www.openslr.org/12) by Vassil Panayotov,
used under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); of The [DNS challenge](https://github.com/microsoft/DNS-Challenge) noises, [Attribution-ShareAlike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/).
"VAD_Net" is licensed under [Attribution-ShareAlike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/) by Joris Cosentino