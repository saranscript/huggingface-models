---
language: de
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 German by Florian Zimmermeister
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice de
      type: common_voice
      args: de  
    metrics:
       - name: Test WER
         type: wer
         value: 15.36
---
# Wav2Vec2-Large-XLSR-53-German
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in German using the [Common Voice](https://huggingface.co/datasets/common_voice)
When using this model, make sure that your speech input is sampled at 16kHz.
## Usage
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
test_dataset = load_dataset("common_voice", "de", split="test[:2%]").
processor = Wav2Vec2Processor.from_pretrained("flozi00/wav2vec-xlsr-german")
model = Wav2Vec2ForCTC.from_pretrained("flozi00/wav2vec-xlsr-german")
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
The model can be evaluated as follows on the {language} test data of Common Voice.
```python
import datasets
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import soundfile as sf
import torch
from jiwer import wer
import librosa
import re
import json
import time

chars_to_ignore_regex = '[\\\\,\\\\?\\\\.\\\\!\\\\-\\\\;\\\\:\\\\"\\\\“\\\\%\\\\‘\\\\”\\\\�]'
pattern = re.compile("[A-Za-z0-9 ]+")

#try:
#    os.remove("dataset.json")
#except:
#    pass

modelName = "flozi00/wav2vec-xlsr-german"
model = Wav2Vec2ForCTC.from_pretrained(modelName).to("cuda")
tokenizer = Wav2Vec2Processor.from_pretrained(modelName)


print("loading and cleaning")
val_dataset = datasets.load_dataset("common_voice","de", split="validation")
val_dataset = val_dataset.remove_columns(["client_id","up_votes","down_votes","age","gender","accent","locale","segment"])
val_dataset = val_dataset.rename_column("path","file")
val_dataset = val_dataset.rename_column("sentence","text")
#val_dataset = val_dataset.filter(lambda example, indice: indice % 30 == 0, with_indices=True)


print(val_dataset)


def map_to_array(batch):
    batch["text"] = re.sub(chars_to_ignore_regex, '', batch["text"]).upper() + " "
    try:
        speech_array, sampling_rate = sf.read(batch["file"]+ ".wav")
    except:
        speech_array, sampling_rate = librosa.load(batch["file"], sr=16000, res_type='kaiser_fast')
        sf.write(batch["file"] + ".wav", speech_array, sampling_rate, subtype='PCM_24')
    batch["speech"] = speech_array
    return batch


print("reading audio")
start = time.time()
val_dataset = val_dataset.map(map_to_array)
print(time.time()-start)
val_dataset = val_dataset.filter(lambda example: True if pattern.fullmatch(example["text"]) is not None else False)


def map_to_pred(batch):
    inputs = tokenizer(batch["speech"], return_tensors="pt", padding="longest")
    input_values = inputs.input_values.to("cuda")
    attention_mask = inputs.attention_mask.to("cuda")

    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits

    predicted_ids = torch.argmax(logits, dim=-1)
    transcription = tokenizer.batch_decode(predicted_ids)
    batch["transcription"] = transcription
    return batch


print("predicting")
result = val_dataset.map(map_to_pred, batched=True, batch_size=32, remove_columns=["speech"])

print("WER:", wer(result["text"], result["transcription"]))

```
**Test Result**: 15.36 %
