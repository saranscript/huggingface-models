---
language: pa-IN
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
- name: wav2vec2-xlsr-punjabi
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice pa 
      type: common_voice
      args: pa-IN
    metrics:
       - name: Test WER
         type: wer
         value: 58.06
---

# Wav2Vec2-Large-XLSR-53-Punjabi 

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Punjabi using the [Common Voice](https://huggingface.co/datasets/common_voice)

When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "pa-IN", split="test")

processor = Wav2Vec2Processor.from_pretrained("gagan3012/wav2vec2-xlsr-punjabi") 
model = Wav2Vec2ForCTC.from_pretrained("gagan3012/wav2vec2-xlsr-punjabi") 

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
\\\\tspeech_array, sampling_rate = torchaudio.load(batch["path"])
\\\\tbatch["speech"] = resampler(speech_array).squeeze().numpy()
\\\\treturn batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
\\\\tlogits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])

```

#### Results: 

Prediction: ['ਹਵਾ ਲਾਤ ਵਿੱਚ ਪੰਦ ਛੇ ਇਖਲਾਟਕੀ ਮੁਜਰਮ ਸਨ', 'ਮੈ ਇ ਹਾ ਪੈਸੇ ਲੇਹੜ ਨਹੀਂ ਸੀ ਚੌਨਾ']

Reference: ['ਹਵਾਲਾਤ ਵਿੱਚ ਪੰਜ ਛੇ ਇਖ਼ਲਾਕੀ ਮੁਜਰਮ ਸਨ', 'ਮੈਂ ਇਹ ਪੈਸੇ ਲੈਣੇ ਨਹੀਂ ਸੀ ਚਾਹੁੰਦਾ']

## Evaluation

The model can be evaluated as follows on the {language} test data of Common Voice.  # TODO: replace #TODO: replace language with your {language}, *e.g.* French


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "pa-IN", split="test") #TODO: replace {lang_id} in your language code here. Make sure the code is one of the *ISO codes* of [this](https://huggingface.co/languages) site.
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("gagan3012/wav2vec2-xlsr-punjabi") 
model = Wav2Vec2ForCTC.from_pretrained("gagan3012/wav2vec2-xlsr-punjabi") 
model.to("cuda")

chars_to_ignore_regex = '[\\\\\\\\\\\\\\\\,\\\\\\\\\\\\\\\\?\\\\\\\\\\\\\\\\.\\\\\\\\\\\\\\\\!\\\\\\\\\\\\\\\\-\\\\\\\\\\\\\\\\;\\\\\\\\\\\\\\\\:\\\\\\\\\\\\\\\\"\\\\\\\\\\\\\\\\“]'  # TODO: adapt this list to include all special characters you removed from the data
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
\\\\\\\\tbatch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
\\\\\\\\tspeech_array, sampling_rate = torchaudio.load(batch["path"])
\\\\\\\\tbatch["speech"] = resampler(speech_array).squeeze().numpy()
\\\\\\\\treturn batch

test_dataset = test_dataset.map(speech_file_to_array_fn)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def evaluate(batch):
\\\\\\\\tinputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

\\\\\\\\twith torch.no_grad():
\\\\\\\\t\\\\\\\\tlogits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

\\\\\\\\tpred_ids = torch.argmax(logits, dim=-1)
\\\\\\\\tbatch["pred_strings"] = processor.batch_decode(pred_ids)
\\\\\\\\treturn batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Result**: 58.05 %


## Training

The script used for training can be found [here](https://colab.research.google.com/drive/1A7Y20c1QkSHfdOmLXPMiOEpwlTjDZ7m5?usp=sharing) 