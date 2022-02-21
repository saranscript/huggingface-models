---
language: is
datasets:
- malromur
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
widget:
- example_title: Malromur sample 1608
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/resolve/main/sample1608.flac
- example_title: Malromur sample 3860
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/resolve/main/sample3860.flac
model-index:
- name: XLSR Wav2Vec2 Icelandic by Mehrdad Farahani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Malromur is
      type: malromur
      args: lt
    metrics:
       - name: Test WER
         type: wer
         value: 09.21
        
---

# Wav2Vec2-Large-XLSR-53-Icelandic

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in Icelandic using [Malromur](https://clarin.is/en/resources/malromur/). When using this model, make sure that your speech input is sampled at 16kHz.

## Usage
The model can be used directly (without a language model) as follows:

**Requirements**
```bash
# requirement packages
!pip install git+https://github.com/huggingface/datasets.git
!pip install git+https://github.com/huggingface/transformers.git
!pip install torchaudio
!pip install librosa
!pip install jiwer
!pip install num2words
```

**Normalizer**
```bash

# num2word packages
# Original source: https://github.com/savoirfairelinux/num2words
!mkdir -p ./num2words
!wget -O num2words/__init__.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/num2words/__init__.py
!wget -O num2words/base.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/num2words/base.py
!wget -O num2words/compat.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/num2words/compat.py
!wget -O num2words/currency.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/num2words/currency.py
!wget -O num2words/lang_EU.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/num2words/lang_EU.py
!wget -O num2words/lang_IS.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/num2words/lang_IS.py
!wget -O num2words/utils.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/num2words/utils.py

# Malromur_test selected based on gender and age
!wget -O malromur_test.csv https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/malromur_test.csv

# Normalizer
!wget -O normalizer.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-icelandic/raw/main/normalizer.py
```

**Prediction**
```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset

import numpy as np
import re
import string

import IPython.display as ipd

from normalizer import Normalizer

normalizer = Normalizer(lang="is")


def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    speech_array = speech_array.squeeze().numpy()
    speech_array = librosa.resample(np.asarray(speech_array), sampling_rate, 16_000)

    batch["speech"] = speech_array
    return batch


def predict(batch):
    features = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)

    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits 
        
    pred_ids = torch.argmax(logits, dim=-1)

    batch["predicted"] = processor.batch_decode(pred_ids)
    return batch


device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-icelandic")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-icelandic").to(device)

dataset = load_dataset("csv", data_files={"test": "./malromur_test.csv"})["test"]
dataset = dataset.map(
    normalizer, 
    fn_kwargs={"do_lastspace_removing": True, "text_key_name": "cleaned_sentence"},
    remove_columns=list(set(dataset.column_names) - set(['cleaned_sentence', 'path']))
)

dataset = dataset.map(speech_file_to_array_fn)
result = dataset.map(predict, batched=True, batch_size=8)

max_items = np.random.randint(0, len(result), 20).tolist()
for i in max_items:
    reference, predicted =  result["cleaned_sentence"][i], result["predicted"][i]
    print("reference:", reference)
    print("predicted:", predicted)
    print('---')
```

**Output:**
```text
reference: eða eitthvað annað dýr
predicted: eða eitthvað annað dýr
---
reference: oddgerður
predicted: oddgerður
---
reference: eiðný
predicted: eiðný
---
reference: löndum
predicted: löndum
---
reference: tileinkaði bróður sínum markið
predicted: tileinkaði bróður sínum markið
---
reference: þetta er svo mikill hégómi
predicted: þetta er svo mikill hégómi
---
reference: timarit is
predicted: timarit is
---
reference: stefna strax upp aftur
predicted: stefna strax upp aftur
---
reference: brekkuflöt
predicted: brekkuflöt
---
reference: áætlunarferð frestað vegna veðurs
predicted: áætluna ferð frestað vegna veðurs
---
reference: sagði af sér vegna kláms
predicted: sagði af sér vegni kláms
---
reference: grímúlfur
predicted: grímúlgur
---
reference: lýsti sig saklausan
predicted: lýsti sig saklausan
---
reference: belgingur is
predicted: belgingur is
---
reference: sambía
predicted: sambía
---
reference: geirastöðum
predicted: geirastöðum
---
reference: varð tvisvar fyrir eigin bíl
predicted: var tvisvar fyrir eigin bíl
---
reference: reykjavöllum
predicted: reykjavöllum
---
reference: miklir menn eru þeir þremenningar
predicted: miklir menn eru þeir þremenningar
---
reference: handverkoghonnun is
predicted: handverkoghonnun is
---
```


## Evaluation

The model can be evaluated as follows on the test data of Malromur.

```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset, load_metric

import numpy as np
import re
import string

from normalizer import Normalizer

normalizer = Normalizer(lang="is")


def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    speech_array = speech_array.squeeze().numpy()
    speech_array = librosa.resample(np.asarray(speech_array), sampling_rate, 16_000)

    batch["speech"] = speech_array
    return batch


def predict(batch):
    features = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)

    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits 
        
    pred_ids = torch.argmax(logits, dim=-1)

    batch["predicted"] = processor.batch_decode(pred_ids)
    return batch


device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-icelandic")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-icelandic").to(device)

dataset = load_dataset("csv", data_files={"test": "./malromur_test.csv"})["test"]
dataset = dataset.map(
    normalizer, 
    fn_kwargs={"do_lastspace_removing": True, "text_key_name": "cleaned_sentence"},
    remove_columns=list(set(dataset.column_names) - set(['cleaned_sentence', 'path']))
)

dataset = dataset.map(speech_file_to_array_fn)
result = dataset.map(predict, batched=True, batch_size=8)

wer = load_metric("wer")

print("WER: {:.2f}".format(100 * wer.compute(predictions=result["predicted"], references=result["cleaned_sentence"])))
```


**Test Result**: 
- WER: 09.21%


## Training & Report
The Common Voice `train`, `validation` datasets were used for training.

You can see the training states [here](https://wandb.ai/m3hrdadfi/wav2vec2_large_xlsr_is/reports/Fine-Tuning-for-Wav2Vec2-Large-XLSR-Icelandic--Vmlldzo2Mjk3ODc?accessToken=j7neoz71mce1fkzt0bch4j0l50witnmme07xe90nvs769kjjtbwneu2wfz3oip16)

The script used for training can be found [here](https://colab.research.google.com/github/m3hrdadfi/notebooks/blob/main/Fine_Tune_XLSR_Wav2Vec2_on_Icelandic_ASR_with_%F0%9F%A4%97_Transformers_ipynb.ipynb)


## Questions?
Post a Github issue on the [Wav2Vec](https://github.com/m3hrdadfi/wav2vec) repo.