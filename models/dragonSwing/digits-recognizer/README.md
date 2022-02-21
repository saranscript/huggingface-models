---
language: vi
datasets:
- common_voice
- vivos
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
license: apache-2.0
---

# Wav2Vec2-Large-XLSR-Vietnamese-Spoken-Digit
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Vietnamese Spoken Digits Recognition task.
When using this model, make sure that your speech input is sampled at 16kHz.
## Usage
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
test_dataset = load_dataset("common_voice", "vi", split="test")
processor = Wav2Vec2Processor.from_pretrained("dragonSwing/digits-recognizer")
model = Wav2Vec2ForCTC.from_pretrained("dragonSwing/digits-recognizer")
resampler = torchaudio.transforms.Resample(48_000, 16_000)
# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
  speech_array, sampling_rate = torchaudio.load(batch["path"])
  batch["speech"] = resampler(speech_array).squeeze().numpy()
  return batch
test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)
with torch.no_grad():
  logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits
predicted_ids = torch.argmax(logits, dim=-1)
print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```
## Evaluation

## Training
## TODO
The Common Voice `train`, `validation`, the VIVOS and FOSD datasets were used for training
The script used for training can be found ... 