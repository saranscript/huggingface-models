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
- label: Common Voice sample 4024
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian-v2/resolve/main/sample4024.flac
- label: Common Voice sample 4084
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian-v2/resolve/main/sample4084.flac
model-index:
- name: XLSR Wav2Vec2 Persian (Farsi) V2 by Mehrdad Farahani
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
         value: 31.92

---

# Wav2Vec2-Large-XLSR-53-Persian V2

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
    "#", "!", "؟", "?", "«", "»", "،", "(", ")", "؛", "'ٔ", "٬",'ٔ', ",", "?", 
    ".", "!", "-", ";", ":",'"',"“", "%", "‘", "”", "�", "–", "…", "_", "”", '“', '„',
    'ā', 'š',
    # "ء", 
]

# In case of farsi
chars_to_ignore = chars_to_ignore + list(string.ascii_lowercase + string.digits)

chars_to_mapping = {
    'ك': 'ک', 'دِ': 'د', 'بِ': 'ب', 'زِ': 'ز', 'ذِ': 'ذ', 'شِ': 'ش', 'سِ': 'س', 'ى': 'ی',
    'ي': 'ی', 'أ': 'ا', 'ؤ': 'و', "ے": "ی", "ۀ": "ه", "ﭘ": "پ", "ﮐ": "ک", "ﯽ": "ی",
    "ﺎ": "ا", "ﺑ": "ب", "ﺘ": "ت", "ﺧ": "خ", "ﺩ": "د", "ﺱ": "س", "ﻀ": "ض", "ﻌ": "ع",
    "ﻟ": "ل", "ﻡ": "م", "ﻢ": "م", "ﻪ": "ه", "ﻮ": "و", 'ﺍ': "ا", 'ة': "ه",
    'ﯾ': "ی", 'ﯿ': "ی", 'ﺒ': "ب", 'ﺖ': "ت", 'ﺪ': "د", 'ﺮ': "ر", 'ﺴ': "س", 'ﺷ': "ش",
    'ﺸ': "ش", 'ﻋ': "ع", 'ﻤ': "م", 'ﻥ': "ن", 'ﻧ': "ن", 'ﻭ': "و", 'ﺭ': "ر", "ﮔ": "گ",
        
    # "ها": "  ها", "ئ": "ی",
        
    "a": " ای ", "b": " بی ", "c": " سی ", "d": " دی ", "e": " ایی ", "f": " اف ",
    "g": " جی ", "h": " اچ ", "i": " آی ", "j": " جی ", "k": " کی ", "l": " ال ",
    "m": " ام ", "n": " ان ", "o": " او ", "p": " پی ", "q": " کیو ", "r": " آر ",
    "s": " اس ", "t": " تی ", "u": " یو ", "v": " وی ", "w": " دبلیو ", "x": " اکس ",
    "y": " وای ", "z": " زد ",
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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian-v2")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian-v2").to(device)

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
reference: عجم زنده کردم بدین پارسی 
predicted: عجم زنده کردم بدین پارسی
---
reference: لباس هایم کی آماده خواهند شد 
predicted: لباس خایم کی آماده خواهند شد
---
reference: با مهان همنشین شدم 
predicted: با مهان همنشین شدم
---
reference: یکی از بهترین فیلم هایی بود که در این سال ها دیدم 
predicted: یکی از بهترین فیلمهایی بود که در این سالها دیدم
---
reference: اون خیلی بد ماساژ میده 
predicted: اون خیلی بد ماساژ میده
---
reference: هنوزم بزرگترین دستاورد دولت روحانی اینه که رییسی رییسجمهور نشد 
predicted: هنوزم بزرگترین دستآوردار دولت روانیاینه که ریسی ریسیومرو نشد
---
reference: واسه بدنسازی آماده ای 
predicted: واسه بعدنسافی آماده ای
---
reference: خدای من شماها سالمین 
predicted: خدای من شما ها سالمین
---
reference: بهشون ثابت میشه که دروغ نگفتم 
predicted: بهشون ثابت میشه که دروغ مگفتم
---
reference: آیا ممکن است یک پتو برای من بیاورید 
predicted: سف کمیتخ لظا
---
reference: نزدیک جلو 
predicted: رزیک جلو
---
reference: شایعه پراکن دربارهاش دروغ و شایعه می سازد 
predicted: شایه پراکن دربارهاش دروغ و شایعه می سازد
---
reference: وقتی نیاز است که یک چهره دوستانه بیابند 
predicted: وقتی نیاز است یک چهره دوستانه بیابند
---
reference: ممکنه رادیواکتیوی چیزی باشه 
predicted: ممکنه به آدیوتیوی چیزی باشه
---
reference: دهنتون رو ببندید 
predicted: دهن جن رو ببندید
---
reference: پاشیم بریم قند و شکر و روغنمون رو بگیریم تا تموم نشده 
predicted: پاشین بریم قند و شکر و روغنمون رو بگیریم تا تموم نشده
---
reference: اما قبل از تمام کردن بحث تاریخی باید ذکری هم از ناپیکس بکنیم 
predicted: اما قبل از تمام کردن بحث تاریخی باید ذکری هم از نایپکس بکنیم
---
reference: لطفا کپی امضا شده قرارداد را بازگردانید 
predicted: لطفا کپی امضال شده قرار داد را باز گردانید
---
reference: خیلی هم چیز مهمی نیست 
predicted: خیلی هم چیز مهمی نیست
---
reference: شایعه پراکن دربارهاش دروغ و شایعه می سازد 
predicted: شایه پراکن دربارهاش دروغ و شایعه می سازد
---
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
    "#", "!", "؟", "?", "«", "»", "،", "(", ")", "؛", "'ٔ", "٬",'ٔ', ",", "?", 
    ".", "!", "-", ";", ":",'"',"“", "%", "‘", "”", "�", "–", "…", "_", "”", '“', '„',
    'ā', 'š',
    # "ء", 
]

# In case of farsi
chars_to_ignore = chars_to_ignore + list(string.ascii_lowercase + string.digits)

chars_to_mapping = {
    'ك': 'ک', 'دِ': 'د', 'بِ': 'ب', 'زِ': 'ز', 'ذِ': 'ذ', 'شِ': 'ش', 'سِ': 'س', 'ى': 'ی',
    'ي': 'ی', 'أ': 'ا', 'ؤ': 'و', "ے": "ی", "ۀ": "ه", "ﭘ": "پ", "ﮐ": "ک", "ﯽ": "ی",
    "ﺎ": "ا", "ﺑ": "ب", "ﺘ": "ت", "ﺧ": "خ", "ﺩ": "د", "ﺱ": "س", "ﻀ": "ض", "ﻌ": "ع",
    "ﻟ": "ل", "ﻡ": "م", "ﻢ": "م", "ﻪ": "ه", "ﻮ": "و", 'ﺍ': "ا", 'ة': "ه",
    'ﯾ': "ی", 'ﯿ': "ی", 'ﺒ': "ب", 'ﺖ': "ت", 'ﺪ': "د", 'ﺮ': "ر", 'ﺴ': "س", 'ﺷ': "ش",
    'ﺸ': "ش", 'ﻋ': "ع", 'ﻤ': "م", 'ﻥ': "ن", 'ﻧ': "ن", 'ﻭ': "و", 'ﺭ': "ر", "ﮔ": "گ",
        
    # "ها": "  ها", "ئ": "ی",
        
    "a": " ای ", "b": " بی ", "c": " سی ", "d": " دی ", "e": " ایی ", "f": " اف ",
    "g": " جی ", "h": " اچ ", "i": " آی ", "j": " جی ", "k": " کی ", "l": " ال ",
    "m": " ام ", "n": " ان ", "o": " او ", "p": " پی ", "q": " کیو ", "r": " آر ",
    "s": " اس ", "t": " تی ", "u": " یو ", "v": " وی ", "w": " دبلیو ", "x": " اکس ",
    "y": " وای ", "z": " زد ",
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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian-v2")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian-v2").to(device)

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
- WER: 31.92%


## Training
The Common Voice `train`, `validation` datasets were used for training.

You can see the training states [here](https://wandb.ai/m3hrdadfi/finetuned_wav2vec_xlsr_persian/reports/Fine-Tuning-for-Wav2Vec2-Large-XLSR-53-Persian--Vmlldzo1NjY1NjU?accessToken=pspukt0liicopnwe93wo1ipetqk0gzkuv8669g00wc6hcesk1fh0rfkbd0h46unk)

The script used for training can be found [here](https://colab.research.google.com/github/m3hrdadfi/notebooks/blob/main/Fine_Tune_XLSR_Wav2Vec2_on_Persian_ASR_with_%F0%9F%A4%97_Transformers_ipynb.ipynb)