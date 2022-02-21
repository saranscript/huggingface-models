---
language: fa
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
widget:
- example_title: Common Voice sample 687
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian/resolve/main/sample687.flac
- example_title: Common Voice sample 1671
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian/resolve/main/sample1671.flac
model-index:
- name: XLSR Wav2Vec2 Persian (Farsi) by Mehrdad Farahani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice fa
      type: common_voice
      args: fa
    metrics:
       - name: Test WER
         type: wer
         value: 32.20
        
---

# Wav2Vec2-Large-XLSR-53-Persian

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in Persian (Farsi) using [Common Voice](https://huggingface.co/datasets/common_voice). When using this model, make sure that your speech input is sampled at 16kHz.

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
!pip install hazm
```


**Prediction**
```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset

import numpy as np
import hazm
import re
import string

import IPython.display as ipd

_normalizer = hazm.Normalizer()
chars_to_ignore = [
    ",", "?", ".", "!", "-", ";", ":", '""', "%", "'", '"', "�",
    "#", "!", "؟", "?", "«", "»", "ء", "،", "(", ")", "؛", "'ٔ", "٬",'ٔ', ",", "?", 
    ".", "!", "-", ";", ":",'"',"“", "%", "‘", "”", "�", "–", "…", "_", "”", '“', '„'
]

# In case of farsi
chars_to_ignore = chars_to_ignore + list(string.ascii_lowercase + string.digits)

chars_to_mapping = {
    'ك': 'ک', 'دِ': 'د', 'بِ': 'ب', 'زِ': 'ز', 'ذِ': 'ذ', 'شِ': 'ش', 'سِ': 'س', 'ى': 'ی',
    'ي': 'ی', 'أ': 'ا', 'ؤ': 'و', "ے": "ی", "ۀ": "ه", "ﭘ": "پ", "ﮐ": "ک", "ﯽ": "ی",
    "ﺎ": "ا", "ﺑ": "ب", "ﺘ": "ت", "ﺧ": "خ", "ﺩ": "د", "ﺱ": "س", "ﻀ": "ض", "ﻌ": "ع",
    "ﻟ": "ل", "ﻡ": "م", "ﻢ": "م", "ﻪ": "ه", "ﻮ": "و", "ئ": "ی", 'ﺍ': "ا", 'ة': "ه",
    'ﯾ': "ی", 'ﯿ': "ی", 'ﺒ': "ب", 'ﺖ': "ت", 'ﺪ': "د", 'ﺮ': "ر", 'ﺴ': "س", 'ﺷ': "ش",
    'ﺸ': "ش", 'ﻋ': "ع", 'ﻤ': "م", 'ﻥ': "ن", 'ﻧ': "ن", 'ﻭ': "و", 'ﺭ': "ر", "ﮔ": "گ",
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
    
    text = _normalizer.normalize(text)
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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian").to(device)

dataset = load_dataset("common_voice", "fa", split="test[:1%]")
dataset = dataset.map(
    normalizer, 
    fn_kwargs={"chars_to_ignore": chars_to_ignore, "chars_to_mapping": chars_to_mapping},
    remove_columns=list(set(dataset.column_names) - set(['sentence', 'path']))
)

dataset = dataset.map(speech_file_to_array_fn)
result = dataset.map(predict)

max_items = np.random.randint(0, len(result), 20).tolist()
for i in max_items:
    reference, predicted =  result["sentence"][i], result["predicted"][i]
    print("reference:", reference)
    print("predicted:", predicted)
    print('---')
```

**Output:**
```text
reference: اطلاعات مسری است
predicted: اطلاعات مسری است
---
reference: نه منظورم اینه که وقتی که ساکته چه کاریه خودمونه بندازیم زحمت
predicted: نه منظورم اینه که وقتی که ساکت چی کاریه خودمونو بندازیم زحمت
---
reference: من آب پرتقال می خورم لطفا
predicted: من آپ ارتغال می خورم لطفا
---
reference: وقت آن رسیده آنها را که قدم پیش میگذارند بزرگ بداریم
predicted: وقت آ رسیده آنها را که قدم پیش میگذارند بزرگ بداریم
---
reference: سیم باتری دارید
predicted: سیم باتری دارید
---
reference: این بهتره تا اینکه به بهونه درس و مشق هر روز بره خونه شون
predicted: این بهتره تا اینکه به بهمونه درسومش خرروز بره خونه اشون
---
reference: ژاکت تنگ است
predicted: ژاکت تنگ است
---
reference: آت و اشغال های خیابان
predicted: آت و اشغال های خیابان
---
reference: من به این روند اعتراض دارم
predicted: من به این لوند تراج دارم
---
reference: کرایه این مکان چند است
predicted: کرایه این مکان چند است
---
reference: ولی این فرصت این سهم جوانی اعطا نشده است
predicted: ولی این فرصت این سحم جوانی اتان نشده است
---
reference: متوجه فاجعهای محیطی میشوم
predicted: متوجه فاجایهای محیطی میشوم
---
reference: ترافیک شدیدیم بود و دیدن نور ماشینا و چراغا و لامپهای مراکز تجاری حس خوبی بهم میدادن
predicted: ترافیک شدید ی هم بودا دیدن نور ماشینا و چراغ لامپهای مراکز تجاری حس خولی بهم میدادن
---
reference: این مورد عمل ها مربوط به تخصص شما می شود
predicted: این مورد عملها مربوط به تخصص شما میشود
---
reference: انرژی خیلی کمی دارم
predicted: انرژی خیلی کمی دارم
---
reference: زیادی خوبی کردنم تهش داستانه
predicted: زیادی خوبی کردنم ترش داستانه
---
reference: بردهای که پادشاه شود
predicted: برده ای که پاده شاه شود
---
reference: یونسکو
predicted: یونسکو
---
reference: شما اخراج هستید
predicted: شما اخراج هستید
---
reference: من سفر کردن را دوست دارم
predicted: من سفر کردم را دوست دارم
```

## Evaluation

The model can be evaluated as follows on the Persian (Farsi) test data of Common Voice.

```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset, load_metric

import numpy as np
import hazm
import re
import string

_normalizer = hazm.Normalizer()
chars_to_ignore = [
    ",", "?", ".", "!", "-", ";", ":", '""', "%", "'", '"', "�",
    "#", "!", "؟", "?", "«", "»", "ء", "،", "(", ")", "؛", "'ٔ", "٬",'ٔ', ",", "?", 
    ".", "!", "-", ";", ":",'"',"“", "%", "‘", "”", "�", "–", "…", "_", "”", '“', '„'
]

# In case of farsi
chars_to_ignore = chars_to_ignore + list(string.ascii_lowercase + string.digits)

chars_to_mapping = {
    'ك': 'ک', 'دِ': 'د', 'بِ': 'ب', 'زِ': 'ز', 'ذِ': 'ذ', 'شِ': 'ش', 'سِ': 'س', 'ى': 'ی',
    'ي': 'ی', 'أ': 'ا', 'ؤ': 'و', "ے": "ی", "ۀ": "ه", "ﭘ": "پ", "ﮐ": "ک", "ﯽ": "ی",
    "ﺎ": "ا", "ﺑ": "ب", "ﺘ": "ت", "ﺧ": "خ", "ﺩ": "د", "ﺱ": "س", "ﻀ": "ض", "ﻌ": "ع",
    "ﻟ": "ل", "ﻡ": "م", "ﻢ": "م", "ﻪ": "ه", "ﻮ": "و", "ئ": "ی", 'ﺍ': "ا", 'ة': "ه",
    'ﯾ': "ی", 'ﯿ': "ی", 'ﺒ': "ب", 'ﺖ': "ت", 'ﺪ': "د", 'ﺮ': "ر", 'ﺴ': "س", 'ﺷ': "ش",
    'ﺸ': "ش", 'ﻋ': "ع", 'ﻤ': "م", 'ﻥ': "ن", 'ﻧ': "ن", 'ﻭ': "و", 'ﺭ': "ر", "ﮔ": "گ",
    "\\u200c": " ", "\\u200d": " ", "\\u200e": " ", "\\u200f": " ", "\\ufeff": " ",
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
    
    text = _normalizer.normalize(text)
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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian").to(device)

dataset = load_dataset("common_voice", "fa", split="test")
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

**Test Result:** 
- WER: 32.20%


## Training
The Common Voice `train`, `validation` datasets were used for training.
The script used for training can be found [here](https://colab.research.google.com/github/m3hrdadfi/notebooks/blob/main/Fine_Tune_XLSR_Wav2Vec2_on_Persian_ASR_with_%F0%9F%A4%97_Transformers_ipynb.ipynb)