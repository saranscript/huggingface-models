---
language: et
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
widget:
- label: Common Voice sample 1123
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-estonian/resolve/main/sample1123.flac
- label: Common Voice sample 910
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-estonian/resolve/main/sample910.flac
model-index:
- name: XLSR Wav2Vec2 Estonian by Mehrdad Farahani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice et
      type: common_voice
      args: et
    metrics:
       - name: Test WER
         type: wer
         value: 33.93
---


# Wav2Vec2-Large-XLSR-53-Estonian

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in Estonian using [Common Voice](https://huggingface.co/datasets/common_voice). When using this model, make sure that your speech input is sampled at 16kHz.

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

chars_to_ignore = [
    ",", "?", ".", "!", "-", ";", ":", '""', "%", "'", '"', "�",
    "#", "!", "?", "«", "»", "(", ")", "؛", ",", "?", ".", "!", "-", ";", ":", '"', 
    "“", "%", "‘", "�", "–", "…", "_", "”", '“', '„'
]
chars_to_mapping = {
"\u200c": " ", "\u200d": " ", "\u200e": " ", "\u200f": " ", "\ufeff": " ",
}

def multiple_replace(text, chars_to_mapping):
    pattern = "|".join(map(re.escape, chars_to_mapping.keys()))
    return re.sub(pattern, lambda m: chars_to_mapping[m.group()], str(text))

def remove_special_characters(text, chars_to_ignore_regex):
    text = re.sub(chars_to_ignore_regex, '', text).lower() + " "
    return text

def normalizer(batch, chars_to_ignore, chars_to_mapping):
    chars_to_ignore_regex = f"""[{"".join(chars_to_ignore)}]"""
    text = batch["sentence"].lower().strip()
    
    text = text.replace("\u0307", " ").strip()
    text = multiple_replace(text, chars_to_mapping)
    text = remove_special_characters(text, chars_to_ignore_regex)

    batch["sentence"] = text
    return batch


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

    batch["predicted"] = processor.batch_decode(pred_ids)[0]
    return batch


device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-estonian")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-estonian").to(device)

dataset = load_dataset("common_voice", "et", split="test[:1%]")
dataset = dataset.map(
    normalizer, 
    fn_kwargs={"chars_to_ignore": chars_to_ignore, "chars_to_mapping": chars_to_mapping},
    remove_columns=list(set(dataset.column_names) - set(['sentence', 'path']))
)

dataset = dataset.map(speech_file_to_array_fn)
result = dataset.map(predict)

max_items = np.random.randint(0, len(result), 10).tolist()
for i in max_items:
    reference, predicted =  result["sentence"][i], result["predicted"][i]
    print("reference:", reference)
    print("predicted:", predicted)
    print('---')
```

**Output:**
```text
reference: õhulossid lagunevad ning ees ootab maapind 
predicted: õhulassid lagunevad ning ees ootab maapind
---
reference: milliseks kiievisse pääsemise nimel võistlev muusik soome muusikamaastiku hetkeseisu hindab ning kas ta ka ennast sellel tulevikus tegutsemas näeb kuuled videost 
predicted: milliseks gievisse pääsemise nimel võitlev muusiks soome muusikama aastiku hetke seisu hindab ning kas ta ennast selle tulevikus tegutsemast näeb kuulad videost
---
reference: näiteks kui pool seina on tehtud tekib tunne et tahaks tegelikult natuke teistsugust ja hakkame otsast peale 
predicted: näiteks kui pool seine on tehtud tekib tunnetahaks tegelikult matuka teistsugust jahappanna otsast peane
---
reference: neuroesteetilised katsed näitavad et just nägude vaatlemine aktiveerib inimese aju esteetilist keskust 
predicted: neuroaisteetiliselt katsed näitaval et just nägude vaatlemine aptiveerid inimese aju est eedilist keskust
---
reference: paljud inimesed kindlasti kadestavad teid kuid ei julge samamoodi vabalt võtta 
predicted: paljud inimesed kindlasti kadestavadteid kuid ei julge sama moodi vabalt võtta
---
reference: parem on otsida pileteid inkognito veebi kaudu 
predicted: parem on otsida pileteid ning kognitu veebikaudu
---
reference: ja vot siin ma jäin vaikseks 
predicted: ja vat siisma ja invaikseks
---
reference: mida sa iseendale juubeli puhul soovid 
predicted: mida saise endale jubeli puhul soovid
---
reference: kuumuse ja kõrge temperatuuri tõttu kuivas tühjadel karjamaadel rohi mis muutus kergesti süttivaks 
predicted: kuumuse ja kõrge temperatuuri tõttu kuivast ühjadal karjamaadel rohi mis muutus kergesti süttivaks
---
reference: ilmselt on inimesi kelle jaoks on see hea lahendus 
predicted: ilmselt on inimesi kelle jaoks on see hea lahendus
---
```


## Evaluation

The model can be evaluated as follows on the Estonian test data of Common Voice.

```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset, load_metric

import numpy as np
import re
import string


chars_to_ignore = [
    ",", "?", ".", "!", "-", ";", ":", '""', "%", "'", '"', "�",
    "#", "!", "?", "«", "»", "(", ")", "؛", ",", "?", ".", "!", "-", ";", ":", '"', 
    "“", "%", "‘", "�", "–", "…", "_", "”", '“', '„'
]
chars_to_mapping = {
    "\u200c": " ", "\u200d": " ", "\u200e": " ", "\u200f": " ", "\ufeff": " ",
}

def multiple_replace(text, chars_to_mapping):
    pattern = "|".join(map(re.escape, chars_to_mapping.keys()))
    return re.sub(pattern, lambda m: chars_to_mapping[m.group()], str(text))

def remove_special_characters(text, chars_to_ignore_regex):
    text = re.sub(chars_to_ignore_regex, '', text).lower() + " "
    return text

def normalizer(batch, chars_to_ignore, chars_to_mapping):
    chars_to_ignore_regex = f"""[{"".join(chars_to_ignore)}]"""
    text = batch["sentence"].lower().strip()
    
    text = text.replace("\u0307", " ").strip()
    text = multiple_replace(text, chars_to_mapping)
    text = remove_special_characters(text, chars_to_ignore_regex)

    batch["sentence"] = text
    return batch


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

    batch["predicted"] = processor.batch_decode(pred_ids)[0]
    return batch


device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-estonian")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-estonian").to(device)

dataset = load_dataset("common_voice", "et", split="test")
dataset = dataset.map(
    normalizer, 
    fn_kwargs={"chars_to_ignore": chars_to_ignore, "chars_to_mapping": chars_to_mapping},
    remove_columns=list(set(dataset.column_names) - set(['sentence', 'path']))
)

dataset = dataset.map(speech_file_to_array_fn)
result = dataset.map(predict)

wer = load_metric("wer")

print("WER: {:.2f}".format(100 * wer.compute(predictions=result["predicted"], references=result["sentence"])))
```

**Test Result**: 
- WER: 33.93%


## Training & Report
The Common Voice `train`, `validation` datasets were used for training.

You can see the training states [here](https://wandb.ai/m3hrdadfi/finetuned_wav2vec_xlsr_estonian/reports/Fine-Tuning-for-Wav2Vec2-Large-XLSR-53-Estonian--Vmlldzo1NjA1MTI?accessToken=k2b2g3a2i12m1sdwf13q8b226pplmmyw12joxo6vk38eb4djellfzmn9fp2725fw)

The script used for training can be found [here](https://colab.research.google.com/github/m3hrdadfi/notebooks/blob/main/Fine_Tune_XLSR_Wav2Vec2_on_Estonian_ASR_with_%F0%9F%A4%97_Transformers_ipynb.ipynb)