---
language: hi
datasets:
- common_voice 
- indic tts
- iiith 
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: Hindi XLSR Wav2Vec2 Large 53
results:
- task: 
    name: Speech Recognition
    type: automatic-speech-recognition
    dataset:
      - name: Common Voice hi
        type: common_voice
        args: hi 
      - name: Indic IIT (IITM)
        type: indic
        args: hi
      - name: IIITH Indic Dataset
        type: iiith
        args: hi
    metrics:
       - name: Custom Dataset Hindi WER
         type: wer
         value: 17.23
       - name: CommonVoice Hindi (Test) WER 
         type: wer
         value: 56.46
---

# Wav2Vec2-Large-XLSR-53-Hindi

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Hindi using the following datasets:
- [Common Voice](https://huggingface.co/datasets/common_voice), 
- [Indic TTS- IITM](https://www.iitm.ac.in/donlab/tts/index.php) and
- [IIITH - Indic Speech Datasets](http://speech.iiit.ac.in/index.php/research-svl/69.html)

The Indic datasets are well balanced across gender and accents. However the CommonVoice dataset is skewed towards male voices


Fine-tuned on facebook/wav2vec2-large-xlsr-53 using Hindi dataset :: 60 epochs >> 17.05% WER
                          
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
test_dataset = load_dataset("common_voice", "hi", split="test")

processor = Wav2Vec2Processor.from_pretrained("skylord/wav2vec2-large-xlsr-hindi") 
model = Wav2Vec2ForCTC.from_pretrained("skylord/wav2vec2-large-xlsr-hindi") 

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
## Predictions 

*Some good ones ..... *

| Predictions | Reference |
|-------|-------|
|फिर वो सूरज तारे पहाड बारिश पदछड़ दिन रात शाम नदी बर्फ़ समुद्र धुंध हवा कुछ भी हो सकती है | फिर वो सूरज तारे पहाड़ बारिश पतझड़ दिन रात शाम नदी बर्फ़ समुद्र धुंध हवा कुछ भी हो सकती है |
| इस कारण जंगल में बडी दूर स्थित राघव के आश्रम में लोघ कम आने लगे और अधिकांश भक्त सुंदर के आश्रम में जाने लगे |  इस कारण जंगल में बड़ी दूर स्थित राघव के आश्रम में लोग कम आने लगे और अधिकांश भक्त सुन्दर के आश्रम में जाने लगे |
| अपने बचन के अनुसार शुभमूर्त पर अनंत दक्षिणी पर्वत गया और मंत्रों का जप करके सरोवर में उतरा | अपने बचन के अनुसार शुभमुहूर्त पर अनंत दक्षिणी पर्वत गया और मंत्रों का जप करके सरोवर में उतरा |



*Some crappy stuff .... *


| Predictions | Reference |
|-------|-------|
| वस गनिल साफ़ है। | उसका दिल साफ़ है। |
| चाय वा एक कुछ लैंगे हब | चायवाय कुछ लेंगे आप |
| टॉम आधे है स्कूल हें है | टॉम अभी भी स्कूल में है |



## Evaluation

The model can be evaluated as follows on the following two datasets: 
1. Custom dataset created from 20% of Indic, IIITH and CV (test): WER 17.xx% 
2. CommonVoice Hindi test dataset: WER 56.xx%

Links to the datasets are provided above (check the links at the start of the README)

train-test csv files are shared on the following gdrive links:
a. IIITH [train](https://storage.googleapis.com/indic-dataset/train_test_splits/iiit_hi_train.csv) [test](https://storage.googleapis.com/indic-dataset/train_test_splits/iiit_hi_test.csv)
b. Indic TTS [train](https://storage.googleapis.com/indic-dataset/train_test_splits/indic_train_full.csv) [test](https://storage.googleapis.com/indic-dataset/train_test_splits/indic_test_full.csv)


Update the audio_path as per your local file structure.

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

## Load the datasets
test_dataset = load_dataset("common_voice", "hi", split="test") 

indic = load_dataset("csv", data_files= {'train':"/workspace/data/hi2/indic_train_full.csv",
                                        "test": "/workspace/data/hi2/indic_test_full.csv"}, download_mode="force_redownload")
iiith = load_dataset("csv", data_files= {"train": "/workspace/data/hi2/iiit_hi_train.csv", 
                                        "test": "/workspace/data/hi2/iiit_hi_test.csv"}, download_mode="force_redownload")

## Pre-process datasets and concatenate to create test dataset
# Drop columns of common_voice
split = ['train', 'test', 'validation', 'other', 'invalidated']

for sp in split:
    common_voice[sp] = common_voice[sp].remove_columns(['client_id', 'up_votes', 'down_votes', 'age', 'gender', 'accent', 'locale', 'segment']) 
    
common_voice = common_voice.rename_column('path', 'audio_path')
common_voice = common_voice.rename_column('sentence', 'target_text')

train_dataset = datasets.concatenate_datasets([indic['train'], iiith['train'], common_voice['train']])
test_dataset = datasets.concatenate_datasets([indic['test'], iiith['test'], common_voice['test'], common_voice['validation']])

## Load model from HF hub

wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("skylord/wav2vec2-large-xlsr-hindi") 
model = Wav2Vec2ForCTC.from_pretrained("skylord/wav2vec2-large-xlsr-hindi")
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\'\;\:\"\“\%\‘\”\�Utrnle\_]'
unicode_ignore_regex = r'[dceMaWpmFui\xa0\u200d]' # Some unwanted unicode chars
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays

def speech_file_to_array_fn(batch):
  batch["target_text"] = re.sub(chars_to_ignore_regex, '', batch["target_text"])
  batch["target_text"] = re.sub(unicode_ignore_regex, '', batch["target_text"])
    
  speech_array, sampling_rate = torchaudio.load(batch["audio_path"])
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

**Test Result on custom dataset**: 17.23 % 




```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "hi", split="test") 
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("skylord/wav2vec2-large-xlsr-hindi") 
model = Wav2Vec2ForCTC.from_pretrained("skylord/wav2vec2-large-xlsr-hindi")
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\'\;\:\"\“\%\‘\”\�Utrnle\_]'
unicode_ignore_regex = r'[dceMaWpmFui\xa0\u200d]' # Some unwanted unicode chars
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays

def speech_file_to_array_fn(batch):
  batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).sub(unicode_ignore_regex, '', batch["sentence"])
  speech_array, sampling_rate = torchaudio.load(batch["path"])
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

**Test Result on CommonVoice**: 56.46 % 



## Training

The Common Voice `train`, `validation`, datasets were used for training as well as   

The script used for training & wandb dashboard can be found [here](https://wandb.ai/thinkevolve/huggingface/reports/Project-Hindi-XLSR-Large--Vmlldzo2MTI2MTQ)
