---

language: "en"

thumbnail:

tags:

- audio-source-separation

- Source Separation

- Speech Separation

- WHAM!

- REAL-M

- SepFormer

- Transformer 

- pytorch

- speechbrain

license: "apache-2.0"

datasets:

- REAL-M
- WHAMR!

metrics:

- SI-SNRi

---

<iframe src="https://ghbtns.com/github-btn.html?user=speechbrain&repo=speechbrain&type=star&count=true&size=large&v=2" frameborder="0" scrolling="0" width="170" height="30" title="GitHub"></iframe>

<br/><br/>

# Neural SI-SNR Estimator 
The Neural SI-SNR Estimator predicts the scale-invariant signal-to-noise ratio (SI-SNR) from the separated signals and the original mixture.
The performance estimation is blind (i.e., no targets signals are needed). This model allows a performance estimation on real mixtures, where the targets are not available.

  
This repository provides the SI-SNR estimator model introduced for the REAL-M dataset. 

The REAL-M dataset can downloaded from [this link](https://sourceseparationresearch.com/static/REAL-M-v0.1.0.tar.gz).
The paper for the REAL-M dataset can be found on [this arxiv link](https://arxiv.org/pdf/2110.10812.pdf). 


| Release | Test-Set (WHAMR!) average l1 error |  
|:---:|:---:|
| 18-10-21 | 1.7 dB | 

## Install SpeechBrain

First of all, currently you need to install SpeechBrain from the source:

1. Clone SpeechBrain:

```bash
git clone https://github.com/speechbrain/speechbrain/
```

2. Install it:

```
cd speechbrain

pip install -r requirements.txt

pip install -e .

```

Please notice that we encourage you to read our tutorials and learn more about [SpeechBrain](https://speechbrain.github.io).

### Minimal example for SI-SNR estimation

```python
from speechbrain.pretrained import SepformerSeparation as separator
from speechbrain.pretrained.interfaces import fetch
from speechbrain.pretrained.interfaces import SNREstimator as snrest

import torchaudio

# 1- Download a test mixture
fetch("test_mixture.wav", source="speechbrain/sepformer-wsj02mix", savedir=".", save_filename="test_mixture.wav")

# 2- Separate the mixture with a pretrained model (sepformer-whamr in this case)
model = separator.from_hparams(source="speechbrain/sepformer-whamr", savedir='pretrained_models/sepformer-whamr')
est_sources = model.separate_file(path='test_mixture.wav')

# 3- Estimate the performance
snr_est_model = snrest.from_hparams(source="speechbrain/REAL-M-sisnr-estimator",savedir='pretrained_models/REAL-M-sisnr-estimator')
mix, fs = torchaudio.load('test_mixture.wav')
snrhat = snr_est_model.estimate_batch(mix, est_sources)
print(snrhat) # Estimates are in dB / 10 (in the range 0-1, e.g., 0 --> 0dB, 1 --> 10dB)

```

### Inference on GPU

To perform inference on the GPU, add  `run_opts={"device":"cuda"}`  when calling the `from_hparams` method.

### Training

The model was trained with SpeechBrain (fc2eabb7).

To train it from scratch follows these steps:

1. Clone SpeechBrain:

```bash

git clone https://github.com/speechbrain/speechbrain/

```

2. Install it:

```

cd speechbrain

pip install -r requirements.txt

pip install -e .

```

3. Run Training:

```
cd recipes/REAL-M/sisnr-estimation

python train.py hparams/pool_sisnrestimator.yaml --data_folder /yourLibri2Mixpath --base_folder_dm /yourLibriSpeechpath --rir_path /yourpathforwhamrRIRs --dynamic_mixing True --use_whamr_train True --whamr_data_folder /yourpath/whamr --base_folder_dm_whamr /yourpath/wsj0-processed/si_tr_s
```

You can find our training results (models, logs, etc) [here](https://drive.google.com/drive/folders/1NGncbjvLeGfbUqmVi6ej-NH9YQn5vBmI).

### Limitations

The SpeechBrain team does not provide any warranty on the performance achieved by this model when used on other datasets.

#### Referencing SpeechBrain

```bibtex

@misc{speechbrain,
  title={{SpeechBrain}: A General-Purpose Speech Toolkit},

  author={Mirco Ravanelli and Titouan Parcollet and Peter Plantinga and Aku Rouhe and Samuele Cornell and Loren Lugosch and Cem Subakan and Nauman Dawalatabad and Abdelwahab Heba and Jianyuan Zhong and Ju-Chieh Chou and Sung-Lin Yeh and Szu-Wei Fu and Chien-Feng Liao and Elena Rastorgueva and François Grondin and William Aris and Hwidong Na and Yan Gao and Renato De Mori and Yoshua Bengio},
  year={2021},
  eprint={2106.04624},
  archivePrefix={arXiv},
  primaryClass={eess.AS},
  note={arXiv:2106.04624}
}

```

#### Referencing REAL-M

```bibtex
@misc{subakan2021realm,
      title={REAL-M: Towards Speech Separation on Real Mixtures}, 
      author={Cem Subakan and Mirco Ravanelli and Samuele Cornell and François Grondin},
      year={2021},
      eprint={2110.10812},
      archivePrefix={arXiv},
      primaryClass={eess.AS}
}
``` 


```

# **About SpeechBrain**

- Website: https://speechbrain.github.io/

- Code: https://github.com/speechbrain/speechbrain/

- HuggingFace: https://huggingface.co/speechbrain/