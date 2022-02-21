---
tags:
- superb
- speaker-diarization
- benchmark:superb
library_name: superb
pipeline_tag: speech-segmentation
---

# Test for superb using hubert downstream SD

## Usage

```python
import io
import soundfile as sf
from urllib.request import urlopen
from model import PreTrainedModel

model = PreTrainedModel()
url = "https://huggingface.co/datasets/lewtun/s3prl-sd-dummy/raw/main/audio.wav"
data, samplerate = sf.read(io.BytesIO(urlopen(url).read()))
print(model(data))
```