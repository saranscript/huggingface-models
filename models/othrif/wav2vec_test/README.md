---
language: ar
datasets:
- https://arabicspeech.org/
tags:
- audio
- automatic-speech-recognition
- speech
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Egyptian by Zaid Alyafeai and Othmane Rifki
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: arabicspeech.org MGB-3
      type: arabicspeech.org MGB-3
      args: ar  
    metrics:
       - name: Test WER
         type: wer
         value: 55.2
---
# Test Wav2Vec2 with egyptian arabic
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in Egyptian using the [arabicspeech.org MGB-3](https://arabicspeech.org/mgb3-asr/)
When using this model, make sure that your speech input is sampled at 16kHz.
## Usage
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
dataset = load_dataset("arabic_speech_corpus", split="test")
processor = Wav2Vec2Processor.from_pretrained("othrif/wav2vec_test")
model = Wav2Vec2ForCTC.from_pretrained("othrif/wav2vec_test")
resampler = torchaudio.transforms.Resample(48_000, 16_000)
# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
\\tspeech_array, sampling_rate = torchaudio.load(batch["path"])
\\tbatch["speech"] = resampler(speech_array).squeeze().numpy()
\\treturn batch
test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)
with torch.no_grad():
\\tlogits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits
predicted_ids = torch.argmax(logits, dim=-1)
print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```