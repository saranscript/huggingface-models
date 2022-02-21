---
language: fa
datasets:
- shemo
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
widget:
- label: ShEMO sample 250
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian-shemo/resolve/main/sample250.flac
- label: ShEMO sample 52
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian-shemo/resolve/main/sample52.flac
model-index:
- name: XLSR Wav2Vec2 Persian (Farsi) ShEMO by Mehrdad Farahani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: ShEMO fa
      type: shemo
      args: fa  
    metrics:
       - name: Test WER
         type: wer
         value: 30.00
         
---

# Wav2Vec2-Large-XLSR-53-Persian ShEMO

Fine-tuned [Wav2Vec2-Large-XLSR-53-Persian V2](https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian-v2) in Persian (Farsi) using [ShEMO](https://www.kaggle.com/mansourehk/shemo-persian-speech-emotion-detection-database). When using this model, make sure that your speech input is sampled at 16kHz.

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
!pip install num2fawords
```


**Prediction**
```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset

from num2fawords import words, ordinal_words
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
    _text = []
    for word in text.split():
        try:
            word = int(word)
            _text.append(words(word))
        except:
            _text.append(word)
            
    text = " ".join(_text) + " "
    
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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian-shemo")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian-shemo").to(device)

dataset = load_dataset("csv", data_files={"test": "/content/fa/dataset/test.csv"}, delimiter="\t")["test"]
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
reference: همون شبی که قسم خوردی منو از جونت بیشتر دوست داری و تا آخر عمر کنار من می مونی همون شبی که به من وعده دادی بزرگترین جشن های ازدواج رو برام بگیری 
predicted: همون شبی که قسم خوردی منو از جونت بیشتر دوستاری و تا آخر عمر کنار من می مونیمو یبی که به من وعض دادین بزرگترین جشن های ازدواج و برام بگیری
---
reference: خودتون دم به ساعت فحشش می دین کتکش می زنین بس نیست 
predicted: خودتون دم به ساعت فشش می دیم کتاکش می زنیم بس نیست
---
reference: خونه 
predicted: خونه
---
reference: شلوغش نکن 
predicted: شلوغش نکن
---
reference: برای بقیه سوییت هایی در نظر گرفتم 
predicted: برای بقی سویید هایی در نظر گرفتم
---
reference: برو گمشو برو گمشو برو بیرون 
predicted: برو گمشو برو گمشو برو بیرون
---
reference: فقط یک سال بعد از خاتمه جنگ بود که حقیقت رو فهمیدی 
predicted: فقط یک سال بعد از خاتمه جنگ بود که حقیقت و فهمیدید
---
reference: غیر از اون دو نفری که اینجا خوابیدند کسان دیگه ای از دوستانشو به تو معرفی نکرده 
predicted: غیر از اون دو نفری که اینجا خوابیدند کسانه دیگه ای از دوستانشو به تو معرفی نکرده
---
reference: من می دونم اینجایی درو واز کن کویی کوئک 
predicted: من می دونم این جایی د رو واز کن کوری فکر
---
reference: نویسنده باید چهار تا چشم داشته باشه چهار تا گوش 
predicted: نویسند باید چهار تا چشم داشته باشه و چهار تا گوش
---
reference: غیر از اون دو نفری که اینجا خوابیدند کسان دیگه ای از دوستانشو به تو معرفی نکرده 
predicted: غیر از اون دو نفری که اینجا خوابیدند کسانه دیگه ای از دوستانشو به تو معرفی نکرده
---
reference: پس همراهان من چه می کنن چه می کنن که این سرکرده کولی ها تونسته خودشو اینجا برسونه 
predicted: پس همرا حال من چه می کنن چه می کنن که این سرکرده کلی ها تونسته خودش رو اینجا برسونه
---
reference: گوش بدید مادمازل حقیقت اینه که من دلم می خواد به شما کمک کنم زیبایی و جوانی شما دل منو به رحم میاره به من اعتماد کنید دلم می خواد بتونم شما رو از مرگ نجات بدم 
predicted: هوش بدید مادماز حقیقت اینه که من دلم می خواد به شما کمک کنم زیبای و جوانی شما دل منو به رحم می آره به من اعتماد کنید دلم می خواد بتونم شما رو از مرگ نجات بدم
---
reference: قربان به نظر می رسه شما نه تنها به مرگ رونالد دریو بلکه به مرگ خانم مونرو هم مشکوکید 
predicted: قربان به نظر می رسه شما نه تن ها به مرگ رونال گریو بلکه به مرگ خانم مونرا مشکوکین
---
reference: برای اینکه شما رو دوست دارم 
predicted: برای اینکه شما رو دوست دارم
---
reference: مرتبه اول دنبال جسدی می گشتن که انداخته بودن کنار خیابون 
predicted: حر تبه اول دنبال جسدی می گشتند که انداخته بودن کنار خیابون
---
reference: خونه 
predicted: خونه
---
reference: کدبانوی جدید این طبقه هستم 
predicted: کدبانوی جدید این طبقه هستم
---
reference: و این برات خیلی گرون تموم شد 
predicted: و این برات خیلی گرون تموم شد
---
reference: خب چرا نمی دین به خودشون 
predicted: خبچرا نمی تون به خودشون
```

## Evaluation

The model can be evaluated as follows on the Persian (Farsi) test data of Common Voice.

```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset, load_metric

from num2fawords import words, ordinal_words
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
    _text = []
    for word in text.split():
        try:
            word = int(word)
            _text.append(words(word))
        except:
            _text.append(word)
            
    text = " ".join(_text) + " "
    
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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian-shemo")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-persian-shemo").to(device)

dataset = load_dataset("csv", data_files={"test": "/content/fa/dataset/test.csv"}, delimiter="\t")["test"]
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
- WER: 31.00%


## Training
The Common Voice `train`, `validation` datasets were used for training.

The script used for training can be found [here](https://colab.research.google.com/github/m3hrdadfi/notebooks/blob/main/Fine_Tune_XLSR_Wav2Vec2_on_Persian_ShEMO_ASR_with_%F0%9F%A4%97_Transformers_ipynb.ipynb)