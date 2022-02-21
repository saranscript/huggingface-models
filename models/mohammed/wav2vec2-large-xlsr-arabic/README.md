---
language: ar
datasets:
- common_voice
- arabic_speech_corpus
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: Mohammed XLSR Wav2Vec2 Large 53
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice ar
      type: common_voice
      args: ar
    metrics:
       - name: Test WER
         type: wer
         value: 36.699
       - name: Validation WER
         type: wer
         value: 36.699
---
# Wav2Vec2-Large-XLSR-53-Arabic

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53)
on Arabic using the `train` splits of [Common Voice](https://huggingface.co/datasets/common_voice)
and [Arabic Speech Corpus](https://huggingface.co/datasets/arabic_speech_corpus).
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
%%capture
!pip install datasets
!pip install transformers==4.4.0
!pip install torchaudio
!pip install jiwer
!pip install tnkeeh

import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "ar", split="test[:2%]")


processor = Wav2Vec2Processor.from_pretrained("mohammed/wav2vec2-large-xlsr-arabic")
model = Wav2Vec2ForCTC.from_pretrained("mohammed/wav2vec2-large-xlsr-arabic")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("The predicted sentence is: ", processor.batch_decode(predicted_ids))
print("The original sentence is:", test_dataset["sentence"][:2])
```

The output is:

```
The predicted sentence is : ['ألديك قلم', 'ليست نارك مكسافة على هذه الأرض أبعد من يوم أمس']
The original sentence is: ['ألديك قلم ؟', 'ليست هناك مسافة على هذه الأرض أبعد من يوم أمس.']
```

## Evaluation

The model can be evaluated as follows on the Arabic test data of Common Voice:

```python

import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re
# creating a dictionary with all diacritics
dict = {
'ِ': '',
'ُ': '', 
'ٓ': '', 
'ٰ': '', 
'ْ': '', 
'ٌ': '', 
'ٍ': '', 
'ً': '', 
'ّ': '', 
'َ': '',
'~': '',
',': '',
'ـ': '',
'—': '',
'.': '',
'!': '',
'-': '',
';': '',
':': '',
'\'': '',
'"': '',
'☭': '',
'«': '',
'»': '',
'؛': '',
'ـ': '',
'_': '',
'،': '',
'“': '',
'%': '',
'‘': '',
'”': '',
'�': '',
'_': '',
',': '',
'?': '',
'#': '',
'‘': '',
'.': '',
'؛': '',
'get': '',
'؟': '',
'  ': ' ',
'\'ۖ ': '',
'\'': '',
 '\'ۚ' : '',
 ' \'': '',
 '31': '', 
 '24': '',
 '39': ''
} 

# replacing multiple diacritics using dictionary (stackoverflow is amazing)
def remove_special_characters(batch):
  # Create a regular expression  from the dictionary keys
  regex = re.compile("(%s)" % "|".join(map(re.escape, dict.keys())))
  # For each match, look-up corresponding value in dictionary
  batch["sentence"] = regex.sub(lambda mo: dict[mo.string[mo.start():mo.end()]], batch["sentence"])
  return batch 
  

test_dataset = load_dataset("common_voice", "ar", split="test") 
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("mohammed/wav2vec2-large-xlsr-arabic") 
model = Wav2Vec2ForCTC.from_pretrained("mohammed/wav2vec2-large-xlsr-arabic")
model.to("cuda")


resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
test_dataset = test_dataset.map(remove_special_characters)
# Preprocessing the datasets.
# We need to read the audio files as arrays
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

**Test Result**: 36.699%


## Future Work

One can use *data augmentation*, *transliteration*, or *attention_mask* to increase the accuracy.  
