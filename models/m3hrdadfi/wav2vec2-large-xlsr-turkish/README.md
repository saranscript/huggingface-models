---
language: tr
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
widget:
- label: Common Voice sample 1378
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-turkish/resolve/main/sample1378.flac
- label: Common Voice sample 1589
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-turkish/resolve/main/sample1589.flac
model-index:
- name: XLSR Wav2Vec2 Turkish by Mehrdad Farahani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice tr
      type: common_voice
      args: tr
    metrics:
       - name: Test WER
         type: wer
         value: 27.51
        
---

# Wav2Vec2-Large-XLSR-53-Turkish

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in Turkish using [Common Voice](https://huggingface.co/datasets/common_voice). When using this model, make sure that your speech input is sampled at 16kHz.

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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-turkish")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-turkish").to(device)

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
reference: ülke şu anda iki federasyona üye 
predicted: ülke şu anda iki federasyona üye
---
reference: foruma dört yüzde fazla kişi katıldı 
predicted: soruma dört yüzden fazla kişi katıldı
---
reference: mobi altmış üç çalışanları da mutsuz 
predicted: mobia haltmış üç çalışanları da mutsur
---
reference: kentin mali esnekliğinin düşük olduğu bildirildi 
predicted: kentin mali esnekleğinin düşük olduğu bildirildi
---
reference: fouere iki ülkeyi sorunu abartmamaya çağırdı 
predicted: foor iki ülkeyi soruna abartmamaya çanayordı
---
reference: o ülkeden herhangi bir tepki geldi mi 
predicted: o ülkeden herhayın bir tepki geldi mi
---
reference: bunlara asla sırtımızı dönmeyeceğiz 
predicted: bunlara asla sırtımızı dönmeyeceğiz
---
reference: sizi ayakta tutan nedir 
predicted: sizi ayakta tutan nedir
---
reference: artık insanlar daha bireysel yaşıyor 
predicted: artık insanlar daha bir eyselli yaşıyor
---
reference: her ikisi de diyaloga hazır olduğunu söylüyor 
predicted: her ikisi de diyaloğa hazır olduğunu söylüyor
---
reference: merkez bankasının başlıca amacı düşük enflasyon 
predicted: merkez bankasının başlrıca anatı güşükyen flasyon
---
reference: firefox 
predicted: fair foks
---
reference: ülke halkı çok misafirsever ve dışa dönük 
predicted: ülke halktı çok isatirtever ve dışa dönük
---
reference: ancak kamuoyu bu durumu pek de affetmiyor 
predicted: ancak kamuonyulgukirmu pek deafıf etmiyor
---
reference: i ki madende iki bin beş yüzden fazla kişi çalışıyor 
predicted: i ki madende iki bin beş yüzden fazla kişi çalışıyor
---
reference: sunnyside park dışarıdan oldukça iyi görünüyor 
predicted: sani sahip park dışarıdan oldukça iyi görünüyor
---
reference: büyük ödül on beş bin avro 
predicted: büyük ödül on beş bin avro
---
reference: köyümdeki camiler depoya dönüştürüldü 
predicted: küyümdeki camiler depoya dönüştürüldü
---
reference: maç oldukça diplomatik bir sonuçla birbir bitti 
predicted: maç oldukça diplomatik bir sonuçla bir birbitti
---
reference: kuşların ikisi de karantinada öldüler 
predicted: kuşların ikiste karantinada özdüler
---
```


## Evaluation

The model can be evaluated as follows on the Turkish test data of Common Voice.

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
    "\u0307": " "
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
    text = re.sub(" +", " ", text)
    text = text.strip() + " "

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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-turkish")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-turkish").to(device)

dataset = load_dataset("common_voice", "tr", split="test")
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
]

**Test Result**: 
- WER: 27.51%


## Training & Report
The Common Voice `train`, `validation` datasets were used for training.

You can see the training states [here](https://wandb.ai/m3hrdadfi/finetuned_wav2vec_xlsr_turkish/reports/Fine-Tuning-for-Wav2Vec2-Large-XLSR-53-Turkish--Vmlldzo1Njc1MDc?accessToken=02vm5cwbi7d342vyt7h9w9859zex0enltdmjoreyjt3bd5qwv0vs0g3u93iv92q0)

The script used for training can be found [here](https://colab.research.google.com/github/m3hrdadfi/notebooks/blob/main/Fine_Tune_XLSR_Wav2Vec2_on_Turkish_ASR_with_%F0%9F%A4%97_Transformers_ipynb.ipynb)