---
language: en
tags:
- audio
- automatic-speech-recognition
metrics:
- wer
license: mit
---
We took `facebook/wav2vec2-large-960h` and fine tuned it using 1400 audio clips (around 10-15 seconds each) from various cryptocurrency related podcasts. To label the data, we downloaded cryptocurrency podcasts from youtube with their subtitle data and split the clips up by sentence. We then compared the youtube transcription with `facebook/wav2vec2-large-960h` to correct many mistakes in the youtube transcriptions. We can probably achieve better results with more data clean up.

On our data we achieved a WER of 13.1%. `facebook/wav2vec2-large-960h` only reached a WER of 27% on our data.

## Usage
```python
from transformers import Wav2Vec2Processor, Wav2Vec2ForCTC
from datasets import load_dataset
import soundfile as sf
import torch


# load model and tokenizer
processor = Wav2Vec2Processor.from_pretrained("distractedm1nd/wav2vec-en-finetuned-on-cryptocurrency")
model = Wav2Vec2ForCTC.from_pretrained("distractedm1nd/wav2vec-en-finetuned-on-cryptocurrency"

filename = "INSERT_FILENAME"
audio, sampling_rate = sf.read(filename)

input_values = processor(audio, return_tensors="pt", padding="longest", sampling_rate=sampling_rate).input_values  # Batch size 1


# retrieve logits
logits = model(input_values).logits

# take argmax and decode
predicted_ids = torch.argmax(logits, dim=-1)
tokenizer.batch_decode(predicted_ids
```
