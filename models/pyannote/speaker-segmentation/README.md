---
tags:
- pyannote
- pyannote-audio-pipeline
- audio
- voice
- speech
- speaker
- speaker-segmentation
- speaker-diarization
- speaker-change-detection
- voice-activity-detection
- overlapped-speech-detection
datasets:
- ami
- dihard
- voxconverse
license: mit
inference: false
---

# 🎹 Speaker segmentation

Relies on pyannote.audio 2.0 currently in development: see [installation instructions](https://github.com/pyannote/pyannote-audio/tree/develop#installation).

```python
from pyannote.audio import Pipeline
pipeline = Pipeline.from_pretrained("pyannote/speaker-segmentation")
output = pipeline("audio.wav")

for turn, _, speaker in output.itertracks(yield_label=True):
    # speaker speaks between turn.start and turn.end
    ...
```

⚠️ This pipeline does not address [speaker diarization](https://huggingface.co/pyannote/speaker-diarization). 


## Support

For commercial enquiries and scientific consulting, please contact [me](mailto:herve@niderb.fr).  
For [technical questions](https://github.com/pyannote/pyannote-audio/discussions) and [bug reports](https://github.com/pyannote/pyannote-audio/issues), please check [pyannote.audio](https://github.com/pyannote/pyannote-audio) Github repository.


## Citation

```bibtex
@inproceedings{Bredin2021,
  Title = {{End-to-end speaker segmentation for overlap-aware resegmentation}},
  Author = {{Bredin}, Herv{\'e} and {Laurent}, Antoine},
  Booktitle = {Proc. Interspeech 2021},
  Address = {Brno, Czech Republic},
  Month = {August},
  Year = {2021},
```

```bibtex
@inproceedings{Bredin2020,
  Title = {{pyannote.audio: neural building blocks for speaker diarization}},
  Author = {{Bredin}, Herv{\'e} and {Yin}, Ruiqing and {Coria}, Juan Manuel and {Gelly}, Gregory and {Korshunov}, Pavel and {Lavechin}, Marvin and {Fustes}, Diego and {Titeux}, Hadrien and {Bouaziz}, Wassim and {Gill}, Marie-Philippe},
  Booktitle = {ICASSP 2020, IEEE International Conference on Acoustics, Speech, and Signal Processing},
  Address = {Barcelona, Spain},
  Month = {May},
  Year = {2020},
}
```
