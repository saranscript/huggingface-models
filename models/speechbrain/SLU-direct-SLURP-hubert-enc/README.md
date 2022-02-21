---
language: "en"
thumbnail:
tags:
- Spoken language understanding
- speechbrain
- wav2vec2
- hubert
- pytorch
license: "apache-2.0"
datasets:
- SLURP
metrics:
- Accuracy
---

<iframe src="https://ghbtns.com/github-btn.html?user=speechbrain&repo=speechbrain&type=star&count=true&size=large&v=2" frameborder="0" scrolling="0" width="170" height="30" title="GitHub"></iframe>
<br/><br/>

# End-to-end SLU model for SLURP

This repository provides all the necessary tools to perform Speech to intent and slot label with a fine-tuned hubert encoder + decoder using SpeechBrain (in E2E trend). 
It is trained on [SLUR](https://arxiv.org/abs/2011.13205) training data.


For a better experience, we encourage you to learn more about
[SpeechBrain](https://speechbrain.github.io). The model performance on SLURP test set is:

| Release | SLU-F1(%) | 
|:-------------:|:--------------:|
| 30-11-21 | 75.10 | 


## Install SpeechBrain

First of all, please install SpeechBrain with the following command:

```
pip install speechbrain
```

Please notice that we encourage you to read our tutorials and learn more about
[SpeechBrain](https://speechbrain.github.io).

### Perform SLU E2E decoding

An external `py_module_file=custom_interface.py` is used as an external Predictor class into this HF repos. We use `foreign_class` function from `speechbrain.pretrained.interfaces` that allow you to load you custom model. 

```python
>>> from speechbrain.pretrained.interfaces import foreign_class
>>> slu = foreign_class(source="speechbrain/SLU-direct-SLURP-hubert-enc",  pymodule_file="custom_interface.py", classname="CustomSLUDecoder")
>>> slu.decode_file("speechbrain/SLU-direct-SLURP-hubert-enc/audio-1490356700-headset.flac")
```

The system is trained with recordings sampled at 16kHz (single channel).
The code will automatically normalize your audio (i.e., resampling + mono channel selection) when calling *decode_file* if needed. Make sure your input tensor is compliant with the expected sampling rate if you use *decode_batch* and *decode_batch*.

### Inference on GPU
To perform inference on the GPU, add  `run_opts={"device":"cuda"}`  when calling the `from_hparams` method.

### Training
The model was trained with SpeechBrain (aa018540).
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
cd  recipes/SLURP/direct
python train_with_wav2vec2.py hparams/train_with_wav2vec2.yaml --data_folder=your_data_folder
```

You can find our training results (models, logs, etc) [here](https://drive.google.com/drive/folders/1LpcuFldRo_Va1OCGp1bLNdiaC7AQNJOb?usp=sharing)).

### Limitations
The SpeechBrain team does not provide any warranty on the performance achieved by this model when used on other datasets.

# **Citing SpeechBrain**
Please, cite SpeechBrain if you use it for your research or business.

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

# **About SpeechBrain**
- Website: https://speechbrain.github.io/
- Code: https://github.com/speechbrain/speechbrain/
- HuggingFace: https://huggingface.co/speechbrain/
