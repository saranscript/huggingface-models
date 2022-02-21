---
language: zh
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
- robust-speech-event
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Cantonese (Hong Kong) by Voidful
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice zh-HK
      type: common_voice
      args: zh-HK 
    metrics:
       - name: Test CER
         type: cer
         value: 16.41
---

# Wav2Vec2-Large-XLSR-53-hk
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Cantonese using the [Common Voice](https://huggingface.co/datasets/common_voice).  
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage
[Colab trial](https://colab.research.google.com/drive/1nBRLf4Pwiply_y5rXWoaIB8LxX41tfEI?usp=sharing)

```
import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
)
import torch
import re
import sys

model_name = "voidful/wav2vec2-large-xlsr-53-hk"
device = "cuda"
processor_name = "voidful/wav2vec2-large-xlsr-53-hk"

chars_to_ignore_regex = r"[¥•＂＃＄％＆＇（）＊＋，－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､　、〃〈〉《》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏﹑﹔·'℃°•·．﹑︰〈〉─《﹖﹣﹂﹁﹔！？｡。＂＃＄％＆＇（）＊＋，﹐－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､、〃》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏.．!\\"#$%&()*+,\\-.\\:;<=>?@\\[\\]\\\\\\/^_`{|}~]"

model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(processor_name)

resampler = torchaudio.transforms.Resample(orig_freq=48_000, new_freq=16_000)

def load_file_to_data(file):
    batch = {}
    speech, _ = torchaudio.load(file)
    batch["speech"] = resampler.forward(speech.squeeze(0)).numpy()
    batch["sampling_rate"] = resampler.new_freq
    return batch


def predict(data):
    features = processor(data["speech"], sampling_rate=data["sampling_rate"], padding=True, return_tensors="pt")
    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)
    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits
    pred_ids = torch.argmax(logits, dim=-1)
    return processor.batch_decode(pred_ids)
    
```

Predict
```python
predict(load_file_to_data('voice file path'))
```

## Evaluation
The model can be evaluated as follows on the Cantonese (Hong Kong) test data of Common Voice.   
CER calculation refer to https://huggingface.co/ctl/wav2vec2-large-xlsr-cantonese 

```python
!mkdir cer
!wget -O cer/cer.py https://huggingface.co/ctl/wav2vec2-large-xlsr-cantonese/raw/main/cer.py
!pip install jiwer

import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
)
import torch
import re
import sys

cer = load_metric("./cer")
model_name = "voidful/wav2vec2-large-xlsr-53-hk"
device = "cuda"
processor_name = "voidful/wav2vec2-large-xlsr-53-hk"

chars_to_ignore_regex = r"[¥•＂＃＄％＆＇（）＊＋，－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､　、〃〈〉《》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏﹑﹔·'℃°•·．﹑︰〈〉─《﹖﹣﹂﹁﹔！？｡。＂＃＄％＆＇（）＊＋，﹐－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､、〃》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏.．!\\"#$%&()*+,\\-.\\:;<=>?@\\[\\]\\\\\\/^_`{|}~]"

model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(processor_name)

ds = load_dataset("common_voice", 'zh-HK', data_dir="./cv-corpus-6.1-2020-12-11", split="test")

resampler = torchaudio.transforms.Resample(orig_freq=48_000, new_freq=16_000)

def map_to_array(batch):
    speech, _ = torchaudio.load(batch["path"])
    batch["speech"] = resampler.forward(speech.squeeze(0)).numpy()
    batch["sampling_rate"] = resampler.new_freq
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace("’", "'")
    return batch

ds = ds.map(map_to_array)

def map_to_pred(batch):
    features = processor(batch["speech"], sampling_rate=batch["sampling_rate"][0], padding=True, return_tensors="pt")
    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)
    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits
    pred_ids = torch.argmax(logits, dim=-1)
    batch["predicted"] = processor.batch_decode(pred_ids)
    batch["target"] = batch["sentence"]
    return batch

result = ds.map(map_to_pred, batched=True, batch_size=16, remove_columns=list(ds.features.keys()))

print("CER: {:2f}".format(100 * cer.compute(predictions=result["predicted"], references=result["target"])))
```

`CER 16.41`
