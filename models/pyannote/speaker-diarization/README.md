---
tags:
- pyannote
- pyannote-audio-pipeline
- audio
- voice
- speech
- speaker
- speaker-diarization
- speaker-change-detection
- voice-activity-detection
- overlapped-speech-detection
datasets:
- ami
- dihard
- voxconverse
- voxceleb
license: mit
inference: false
---

# 🎹 Speaker diarization

Relies on pyannote.audio 2.0 currently in development: see [installation instructions](https://github.com/pyannote/pyannote-audio/tree/develop#installation).

```python
from pyannote.audio import Pipeline
pipeline = Pipeline.from_pretrained("pyannote/speaker-diarization")
output = pipeline("audio.wav")

for turn, _, speaker in output.itertracks(yield_label=True):
    # speaker speaks between turn.start and turn.end
    ...
```

## Benchmark 

| Dataset                                                                                             | [Diarization error rate](http://pyannote.github.io/pyannote-metrics/reference.html#diarization) |
| --------------------------------------------------------------------------------------------------- | ------ |
| [AMI `only_words` evaluation set](https://github.com/BUTSpeechFIT/AMI-diarization-setup)            | 21.3% |
| [DIHARD 3 evaluation set](https://arxiv.org/abs/2012.01477)                                         | 22.2% |
| [VoxConverse 0.0.2 evaluation set](https://github.com/joonson/voxconverse)                          | 13.0% |

## Support

For commercial enquiries and scientific consulting, please contact [me](mailto:herve@niderb.fr).  
For [technical questions](https://github.com/pyannote/pyannote-audio/discussions) and [bug reports](https://github.com/pyannote/pyannote-audio/issues), please check [pyannote.audio](https://github.com/pyannote/pyannote-audio) Github repository.


## Citation

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
