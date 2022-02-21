---
language: fa
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
widget:
- example_title: Common Voice sample 1
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian-v3/resolve/main/sample1.flac
- example_title: Common Voice sample 2978
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian-v3/resolve/main/sample2978.flac
- example_title: Common Voice sample 5168
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-persian-v3/resolve/main/sample5168.flac
model-index:
- name: XLSR Wav2Vec2 Persian (Farsi) V3 by Mehrdad Farahani
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
         value: 10.36
---

# Wav2Vec2-Large-XLSR-53-Persian V3


## Usage
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in Persian (Farsi) using [Common Voice](https://huggingface.co/datasets/common_voice). When using this model, make sure that your speech input is sampled at 16kHz.


**Requirements**
```bash
# requirement packages
!pip install git+https://github.com/huggingface/datasets.git
!pip install git+https://github.com/huggingface/transformers.git
!pip install torchaudio
!pip install librosa
!pip install jiwer
!pip install parsivar
!pip install num2fawords
```

**Normalizer**
```bash
# Normalizer
!wget -O normalizer.py https://huggingface.co/m3hrdadfi/"wav2vec2-large-xlsr-persian-v3/raw/main/dictionary.py
!wget -O normalizer.py https://huggingface.co/m3hrdadfi/"wav2vec2-large-xlsr-persian-v3/raw/main/normalizer.py
```

**Downloading data**
```bash
wget https://voice-prod-bundler-ee1969a6ce8178826482b88e843c335139bd3fb4.s3.amazonaws.com/cv-corpus-6.1-2020-12-11/fa.tar.gz

tar -xzf fa.tar.gz
rm -rf fa.tar.gz
```

**Cleaning**
```python
from normalizer import normalizer

def cleaning(text):
    if not isinstance(text, str):
        return None

    return normalizer({"sentence": text}, return_dict=False)

data_dir = "/content/cv-corpus-6.1-2020-12-11/fa"

test = pd.read_csv(f"{data_dir}/test.tsv", sep="	")
test["path"] = data_dir + "/clips/" + test["path"]
print(f"Step 0: {len(test)}")

test["status"] = test["path"].apply(lambda path: True if os.path.exists(path) else None)
test = test.dropna(subset=["path"])
test = test.drop("status", 1)
print(f"Step 1: {len(test)}")

test["sentence"] = test["sentence"].apply(lambda t: cleaning(t))
test = test.dropna(subset=["sentence"])
print(f"Step 2: {len(test)}")

test = test.reset_index(drop=True)
print(test.head())

test = test[["path", "sentence"]]
test.to_csv("/content/test.csv", sep="	", encoding="utf-8", index=False)
```

**Prediction**
```python
import numpy as np
import pandas as pd

import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset, load_metric

import IPython.display as ipd

model_name_or_path = "m3hrdadfi/wav2vec2-large-xlsr-persian-v3"
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
print(model_name_or_path, device)

processor = Wav2Vec2Processor.from_pretrained(model_name_or_path)
model = Wav2Vec2ForCTC.from_pretrained(model_name_or_path).to(device)


def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    speech_array = speech_array.squeeze().numpy()
    speech_array = librosa.resample(np.asarray(speech_array), sampling_rate, processor.feature_extractor.sampling_rate)

    batch["speech"] = speech_array
    return batch


def predict(batch):
    features = processor(
        batch["speech"], 
        sampling_rate=processor.feature_extractor.sampling_rate, 
        return_tensors="pt", 
        padding=True
    )

    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)

    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits 

    pred_ids = torch.argmax(logits, dim=-1)

    batch["predicted"] = processor.batch_decode(pred_ids)
    return batch


dataset = load_dataset("csv", data_files={"test": "/content/test.csv"}, delimiter="	")["test"]
dataset = dataset.map(speech_file_to_array_fn)
result = dataset.map(predict, batched=True, batch_size=4)
```

**WER Score**
```python
wer = load_metric("wer")
print("WER: {:.2f}".format(100 * wer.compute(predictions=result["predicted"], references=result["sentence"])))
```

**Output**
```python
max_items = np.random.randint(0, len(result), 20).tolist()
for i in max_items:
    reference, predicted =  result["sentence"][i], result["predicted"][i]
    print("reference:", reference)
    print("predicted:", predicted)
    print('---')
```

```text
reference: ماجرا رو براش تعریف کردم اون گفت مریم اگه میدونی پسر خوبیه خب چه اشکالی داره با‌هاش بیش‌تر اشنا بشو 
predicted: ماجرا رو براش تعریف کردم اون گفت مریم اگه میدونی پسر خوبیه خب چه اشکالی داره با‌هاش بیش‌تر اشنا بشو
---
reference: بیا پایین تو اجازه نداری بری اون بالا 
predicted: بیا پایین تو اجازه نداری بری اون بالا
---
reference: هر روز یک دو مداد کش می رفتتم تااین که تا پایان ترم از تمامی دوستانم مداد برداشته بودم 
predicted: هر روز یک دو مداد کش می رفتم تااین که تا پایین ترم از تمامی دوستان و مداد برداشته بودم
---
reference: فکر میکنی آروم میشینه 
predicted: فکر میکنی آروم میشینه
---
reference: هرکسی با گوشی هوشمند خود میتواند با کایلا متصل گردد در یک محدوده مکانی 
predicted: هرکسی با گوشی هوشمند خود میتواند با کایلا متصل گردد در یک محدوده مکانی
---
reference: برو از مهرداد بپرس 
predicted: برو از مهرداد بپرس
---
reference: می خواهم شما را با این قدم‌ها آشنا کنم 
predicted: می خواهم شما را با این قدم‌ها آشنا کنم
---
reference: میدونم یه روز دوباره می تونم تو رو ببینم 
predicted: میدونم یه روز دوباره می تونم تو رو ببینم
---
reference: بسیار خوب خواهد بود دعوت او را بپذیری 
predicted: بسیار خوب خواهد بود دعوت او را بپذیری
---
reference: بهت بگن آشغالی خوبه 
predicted: بهت بگن آشغالی خوبه
---
reference: چرا معاشرت با هم ایمانان ما را محفوظ نگه میدارد 
predicted: چرا معاشرت با هم ایمانان آ را م حفوظ نگه میدارد
---
reference: بولیوی پس از گویان فقیر‌ترین کشور آمریکای جنوبی است 
predicted: بولیوی پس از گویان فقیر‌ترین کشور آمریکای جنوبی است
---
reference: بعد از مدتی اینکار برایم عادی شد 
predicted: بعد از مدتی اینکار برایم عادو شد
---
reference: به نظر اون هم همینطوره 
predicted: به نظر اون هم همینطوره
---
reference: هیچ مایونز ی دارید 
predicted: هیچ مایونز ی دارید
---
reference: هیچ یک از انان کاری به سنگ نداشتند 
predicted: هیچ شک از انان کاری به سنگ نداشتند
---
reference: می خواهم کمی کتاب شعر ببینم 
predicted: می خواهم کتاب شعر ببینم
---
reference: همین شوهر فهیمه مگه نمی گفتی فرمانده بوده کو 
predicted: همین شوهر فهیمه بینامی گفتی فهمانده بود کو
---
reference: اون جا‌ها کسی رو نمیبینی که تو دستش کتاب نباشه 
predicted: اون جا‌ها کسی رو نمیبینی که تو دستش کتاب نباشه
---
reference: زندان رفتن من در این سال‌های اخیر برام شانس بزرگی بود که معما و مشکل چندین سال‌هام را حل کرد 
predicted: زندان رفتن من در این سال‌ها اخی براب شانس بزرگی بود که معما و مشکل چندین سال‌هام را حل کرد
---
```

## Evaluation

**Test Result:** 
- WER: 10.36%