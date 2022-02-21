---
language: "en"
thumbnail:
tags:
- Source Separation
- Speech Separation
- Audio Source Separation
- SepFormer
- DPRNN
- Convtasnet
- speechbrain
license: "apache-2.0"
datasets:
- REAL-M
- WHAMR!
- Libri2Mix

metrics:
- SI-SNRi


---


# SI-SNR Estimator introduced for the REAL-M dataset

This repository provides the Separator models to be able to train a blind SI-SNR estimator with the recipe provided in the SpeechBrain repository to complement the REAL-M real-life speech separation dataset. 

The SI-SNR estimator is trained with a recordings from the WHAMR! and LibriMix datasets. We used a mixture of 9 separators to create the training data on the fly. 

This model is released together with the REAL-M dataset for source separation on in-the-wild speech mixtures. 

The REAL-M dataset can downloaded from [this link](https://sourceseparationresearch.com/static/REAL-M-v0.1.0.tar.gz).
The paper for the REAL-M dataset can be found on [this arxiv link](https://arxiv.org/pdf/2110.10812.pdf). 

## Install SpeechBrain

First of all, currently you need to install SpeechBrain:

```bash
pip install speechbrain
```

Please notice that we encourage you to read our tutorials and learn more about [SpeechBrain](https://speechbrain.github.io).


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

# **About SpeechBrain**
- Website: https://speechbrain.github.io/
- Code: https://github.com/speechbrain/speechbrain/
- HuggingFace: https://huggingface.co/speechbrain/