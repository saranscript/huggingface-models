---
language: br
datasets:
- common_voice 
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Breton by Cahya
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice br
      type: common_voice
      args: br
    metrics:
       - name: Test WER
         type: wer
         value: 41.71
---

# Wav2Vec2-Large-XLSR-Breton

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53)
on the [Breton Common Voice dataset](https://huggingface.co/datasets/common_voice).
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "br", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("cahya/wav2vec2-large-xlsr-breton")
model = Wav2Vec2ForCTC.from_pretrained("cahya/wav2vec2-large-xlsr-breton")

chars_to_ignore_regex = '[\\,\,\?\.\!\;\:\"\“\%\”\�\(\)\/\«\»\½\…]'

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower() + " "
    batch["sentence"] = batch["sentence"].replace("ʼ", "'")
    batch["sentence"] = batch["sentence"].replace("’", "'")
    batch["sentence"] = batch["sentence"].replace('‘', "'")
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    resampler = torchaudio.transforms.Resample(sampling_rate, 16_000)
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset[:2]["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset[:2]["sentence"])
```

The above code leads to the following prediction for the first two samples:
```
Prediction: ["ne' ler ket don a-benn us netra pa vez zer nic'hed evel-si", 'an eil hag egile']
Reference: ['"n\'haller ket dont a-benn eus netra pa vezer nec\'het evel-se." ', 'an eil hag egile. ']
```


## Evaluation

The model can be evaluated as follows on the Breton test data of Common Voice.

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "br", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("cahya/wav2vec2-large-xlsr-breton")
model = Wav2Vec2ForCTC.from_pretrained("cahya/wav2vec2-large-xlsr-breton") 
model.to("cuda")

chars_to_ignore_regex = '[\\,\,\?\.\!\;\:\"\“\%\”\�\(\)\/\«\»\½\…]'

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower() + " "
    batch["sentence"] = batch["sentence"].replace("ʼ", "'")
    batch["sentence"] = batch["sentence"].replace("’", "'")
    batch["sentence"] = batch["sentence"].replace('‘', "'")
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    resampler = torchaudio.transforms.Resample(sampling_rate, 16_000)
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Result**: 41.71 %

## Training

The Common Voice `train`, `validation`, and ... datasets were used for training as well as ... and ...  # TODO

The script used for training can be found [here](https://github.com/cahya-wirawan/indonesian-speech-recognition) 
(will be available soon)
