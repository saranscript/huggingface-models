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
- name: XLSR Wav2Vec2 Taiwanese Mandarin(zh-tw) by Voidful
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice zh-TW
      type: common_voice
      args: zh-TW 
    metrics:
       - name: Test CER
         type: cer
         value: 18.36
---

# Wav2Vec2-Large-XLSR-53-tw-gpt
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on zh-tw using the [Common Voice](https://huggingface.co/datasets/common_voice).   
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage
[Colab trial](https://colab.research.google.com/drive/1e_z5jQHYbO2YKEaUgzb1ww1WwiAyydAj?usp=sharing)

```
import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
    AutoTokenizer, 
    AutoModelWithLMHead 
)
import torch
import re
import sys

model_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
device = "cuda"
processor_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"

chars_to_ignore_regex = r"[¥•＂＃＄％＆＇（）＊＋，－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､　、〃〈〉《》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏﹑﹔·'℃°•·．﹑︰〈〉─《﹖﹣﹂﹁﹔！？｡。＂＃＄％＆＇（）＊＋，﹐－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､、〃》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏.．!\"#$%&()*+,\-.\:;<=>?@\[\]\\\/^_`{|}~]"


model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(processor_name)

tokenizer = AutoTokenizer.from_pretrained("ckiplab/gpt2-base-chinese")  
gpt_model = AutoModelWithLMHead.from_pretrained("ckiplab/gpt2-base-chinese").to(device)

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
    
    decoded_results = []
    for logit in logits:
        pred_ids = torch.argmax(logit, dim=-1)
        mask = pred_ids.ge(1).unsqueeze(-1).expand(logit.size())
        vocab_size = logit.size()[-1]
        voice_prob = torch.nn.functional.softmax((torch.masked_select(logit, mask).view(-1,vocab_size)),dim=-1)
        gpt_input = torch.cat((torch.tensor([tokenizer.cls_token_id]).to(device),pred_ids[pred_ids>0]), 0)
        gpt_prob = torch.nn.functional.softmax(gpt_model(gpt_input).logits, dim=-1)[:voice_prob.size()[0],:]
        comb_pred_ids = torch.argmax(gpt_prob*voice_prob, dim=-1)
        decoded_results.append(processor.decode(comb_pred_ids))

    return decoded_results
```

Predict
```python
predict(load_file_to_data('voice file path'))
```

## Evaluation
The model can be evaluated as follows on the zh-tw test data of Common Voice.   
CER calculation refer to https://huggingface.co/ctl/wav2vec2-large-xlsr-cantonese 

env setup:
```
!pip install editdistance
!pip install torchaudio
!pip install datasets transformers
```

## Evaluation without LM:
```python
import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
)
import torch
import re
import sys
from transformers import AutoTokenizer, AutoModelWithLMHead 
from datasets import  Audio
from math import log

model_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
device = "cuda"
processor_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
chars_to_ignore_regex = r"[¥•＂＃＄％＆＇（）＊＋，－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､　、〃〈〉《》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏﹑﹔·'℃°•·．﹑︰〈〉─《﹖﹣﹂﹁﹔！？｡。＂＃＄％＆＇（）＊＋，﹐－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､、〃》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏.．!\"#$%&()*+,\-.\:;<=>?@\[\]\\\/^_`{|}~]"

tokenizer = AutoTokenizer.from_pretrained("ckiplab/gpt2-base-chinese")  
lm_model = AutoModelWithLMHead.from_pretrained("ckiplab/gpt2-base-chinese").to(device)
model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(processor_name)

ds = load_dataset("common_voice", 'zh-TW', split="test")
ds = ds.cast_column("audio", Audio(sampling_rate=16_000))
def map_to_array(batch):
    audio = batch["audio"]
    batch["speech"] = processor(audio["array"], sampling_rate=audio["sampling_rate"]).input_values[0]
    batch["sampling_rate"] = audio["sampling_rate"]
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


result = ds.map(map_to_pred, batched=True, batch_size=3, remove_columns=list(ds.features.keys()))

def cer_cal(groundtruth, hypothesis):
    err = 0
    tot = 0
    for p, t in zip(hypothesis, groundtruth):
        err += float(ed.eval(p.lower(), t.lower()))
        tot += len(t)
    return err / tot
print("CER: {:2f}".format(100 * cer_cal(result["target"],result["predicted"])))
```

`CER: 28.70`.  
`TIME: 04:08 min`

## Evaluation with GPT:
```python
import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
)
import torch
import re
import sys
from transformers import AutoTokenizer, AutoModelWithLMHead 
from datasets import  Audio
from math import log

model_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
device = "cuda"
processor_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
chars_to_ignore_regex = r"[¥•＂＃＄％＆＇（）＊＋，－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､　、〃〈〉《》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏﹑﹔·'℃°•·．﹑︰〈〉─《﹖﹣﹂﹁﹔！？｡。＂＃＄％＆＇（）＊＋，﹐－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､、〃》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏.．!\"#$%&()*+,\-.\:;<=>?@\[\]\\\/^_`{|}~]"

tokenizer = AutoTokenizer.from_pretrained("ckiplab/gpt2-base-chinese")  
lm_model = AutoModelWithLMHead.from_pretrained("ckiplab/gpt2-base-chinese").to(device)
model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(processor_name)

ds = load_dataset("common_voice", 'zh-TW', split="test")
ds = ds.cast_column("audio", Audio(sampling_rate=16_000))
def map_to_array(batch):
    audio = batch["audio"]
    batch["speech"] = processor(audio["array"], sampling_rate=audio["sampling_rate"]).input_values[0]
    batch["sampling_rate"] = audio["sampling_rate"]
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace("’", "'")
    return batch
ds = ds.map(map_to_array)

def map_to_pred(batch):
    features = processor(batch["speech"], sampling_rate=batch["sampling_rate"][0], padding=True, return_tensors="pt")
    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)
    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits

    decoded_results = []
    for logit in logits:
        pred_ids = torch.argmax(logit, dim=-1)
        mask = pred_ids.ge(1).unsqueeze(-1).expand(logit.size())
        vocab_size = logit.size()[-1]
        voice_prob = torch.nn.functional.softmax((torch.masked_select(logit, mask).view(-1,vocab_size)),dim=-1)
        lm_input = torch.cat((torch.tensor([tokenizer.cls_token_id]).to(device),pred_ids[pred_ids>0]), 0)
        lm_prob = torch.nn.functional.softmax(lm_model(lm_input).logits, dim=-1)[:voice_prob.size()[0],:]
        comb_pred_ids = torch.argmax(lm_prob*voice_prob, dim=-1)
        decoded_results.append(processor.decode(comb_pred_ids))

    batch["predicted"] = decoded_results
    batch["target"] = batch["sentence"]
    return batch


result = ds.map(map_to_pred, batched=True, batch_size=3, remove_columns=list(ds.features.keys()))

def cer_cal(groundtruth, hypothesis):
    err = 0
    tot = 0
    for p, t in zip(hypothesis, groundtruth):
        err += float(ed.eval(p.lower(), t.lower()))
        tot += len(t)
    return err / tot
print("CER: {:2f}".format(100 * cer_cal(result["target"],result["predicted"])))
```

`CER 25.70`.  
`TIME: 06:04 min`


## Evaluation with GPT + beam search:
```python
import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
)
import torch
import re
import sys
from transformers import AutoTokenizer, AutoModelWithLMHead 
from datasets import  Audio
from math import log

model_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
device = "cuda"
processor_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
chars_to_ignore_regex = r"[¥•＂＃＄％＆＇（）＊＋，－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､　、〃〈〉《》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏﹑﹔·'℃°•·．﹑︰〈〉─《﹖﹣﹂﹁﹔！？｡。＂＃＄％＆＇（）＊＋，﹐－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､、〃》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏.．!\"#$%&()*+,\-.\:;<=>?@\[\]\\\/^_`{|}~]"

tokenizer = AutoTokenizer.from_pretrained("ckiplab/gpt2-base-chinese")  
lm_model = AutoModelWithLMHead.from_pretrained("ckiplab/gpt2-base-chinese").to(device)
model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(processor_name)

ds = load_dataset("common_voice", 'zh-TW', split="test")
ds = ds.cast_column("audio", Audio(sampling_rate=16_000))
def map_to_array(batch):
    audio = batch["audio"]
    batch["speech"] = processor(audio["array"], sampling_rate=audio["sampling_rate"]).input_values[0]
    batch["sampling_rate"] = audio["sampling_rate"]
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace("’", "'")
    return batch
ds = ds.map(map_to_array)

def map_to_pred(batch):
    features = processor(batch["speech"], sampling_rate=batch["sampling_rate"][0], padding=True, return_tensors="pt")
    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)
    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits
        
    decoded_results = []
    for logit in logits:
        sequences = [[[], 1.0]]
        pred_ids = torch.argmax(logit, dim=-1)
        mask = pred_ids.ge(1).unsqueeze(-1).expand(logit.size())
        vocab_size = logit.size()[-1]
        voice_prob = torch.nn.functional.softmax((torch.masked_select(logit, mask).view(-1,vocab_size)),dim=-1)
        while True:
            all_candidates = list()
            exceed = False
            for seq in sequences:
                tokens, score = seq
                gpt_input = torch.tensor([tokenizer.cls_token_id]+tokens).to(device)
                gpt_prob = torch.nn.functional.softmax(lm_model(gpt_input).logits, dim=-1)[:len(gpt_input),:]
                if len(gpt_input) >= len(voice_prob):
                    exceed = True
                comb_pred_ids = gpt_prob*voice_prob[:len(gpt_input)]
                v,i = torch.topk(comb_pred_ids,50,dim=-1)
                for tok_id,tok_prob in zip(i.tolist()[-1],v.tolist()[-1]):
                    candidate = [tokens + [tok_id], score + -log(tok_prob)]
                    all_candidates.append(candidate)
            ordered = sorted(all_candidates, key=lambda tup: tup[1])
            sequences = ordered[:10]
            if exceed:
                break
        decoded_results.append(processor.decode(sequences[0][0]))

    batch["predicted"] = decoded_results
    batch["target"] = batch["sentence"]
    return batch


result = ds.map(map_to_pred, batched=True, batch_size=3, remove_columns=list(ds.features.keys()))

def cer_cal(groundtruth, hypothesis):
    err = 0
    tot = 0
    for p, t in zip(hypothesis, groundtruth):
        err += float(ed.eval(p.lower(), t.lower()))
        tot += len(t)
    return err / tot
print("CER: {:2f}".format(100 * cer_cal(result["target"],result["predicted"])))
```

`CER 18.36`.  


## Evaluation with BERT:
```python
import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
)
import torch
import re
import sys
from transformers import AutoTokenizer, AutoModelForMaskedLM 

model_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
device = "cuda"
processor_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
chars_to_ignore_regex = r"[¥•＂＃＄％＆＇（）＊＋，－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､　、〃〈〉《》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏﹑﹔·'℃°•·．﹑︰〈〉─《﹖﹣﹂﹁﹔！？｡。＂＃＄％＆＇（）＊＋，﹐－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､、〃》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏.．!\"#$%&()*+,\-.\:;<=>?@\[\]\\\/^_`{|}~]"

tokenizer = AutoTokenizer.from_pretrained("bert-base-chinese")  
lm_model = AutoModelForMaskedLM.from_pretrained("bert-base-chinese").to(device)
model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(processor_name)

ds = load_dataset("common_voice", 'zh-TW', data_dir="./cv-corpus-6.1-2020-12-11", split="test")

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

    decoded_results = []
    for logit in logits:
        pred_ids = torch.argmax(logit, dim=-1)
        mask = ~pred_ids.eq(tokenizer.pad_token_id).unsqueeze(-1).expand(logit.size())
        vocab_size = logit.size()[-1]
        voice_prob = torch.nn.functional.softmax((torch.masked_select(logit, mask).view(-1,vocab_size)),dim=-1)
        lm_input = torch.masked_select(pred_ids, ~pred_ids.eq(tokenizer.pad_token_id)).unsqueeze(0)
        mask_lm_prob = voice_prob.clone()
        for i in range(lm_input.shape[-1]):
            masked_lm_input = lm_input.clone()
            masked_lm_input[0][i] = torch.tensor(tokenizer.mask_token_id).to('cuda')
            lm_prob = torch.nn.functional.softmax(lm_model(masked_lm_input).logits, dim=-1).squeeze(0)
            mask_lm_prob[i] = lm_prob[i]
        comb_pred_ids = torch.argmax(mask_lm_prob*voice_prob, dim=-1)
        decoded_results.append(processor.decode(comb_pred_ids))

    batch["predicted"] = decoded_results
    batch["target"] = batch["sentence"]
    return batch


result = ds.map(map_to_pred, batched=True, batch_size=1, remove_columns=list(ds.features.keys()))

def cer_cal(groundtruth, hypothesis):
    err = 0
    tot = 0
    for p, t in zip(hypothesis, groundtruth):
        err += float(ed.eval(p.lower(), t.lower()))
        tot += len(t)
    return err / tot
print("CER: {:2f}".format(100 * cer_cal(result["target"],result["predicted"])))
```
`CER 25.57`.  
`TIME: 09:49 min`

## Evaluation with T-TA:
setup
```
!git clone https://github.com/voidful/pytorch-tta.git
!mv ./pytorch-tta/tta ./tta
!wget https://github.com/voidful/pytorch-tta/releases/download/wiki_zh/wiki_zh.pt
```

```python
import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
)
import torch
import re
import sys
from tta.modeling_tta import TTALMModel
from transformers import AutoTokenizer
import torch



model_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
device = "cuda"
processor_name = "voidful/wav2vec2-large-xlsr-53-tw-gpt"
chars_to_ignore_regex = r"[¥•＂＃＄％＆＇（）＊＋，－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､　、〃〈〉《》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏﹑﹔·'℃°•·．﹑︰〈〉─《﹖﹣﹂﹁﹔！？｡。＂＃＄％＆＇（）＊＋，﹐－／：；＜＝＞＠［＼］＾＿｀｛｜｝～｟｠｢｣､、〃》「」『』【】〔〕〖〗〘〙〚〛〜〝〞〟〰〾〿–—‘’‛“”„‟…‧﹏.．!\"#$%&()*+,\-.\:;<=>?@\[\]\\\/^_`{|}~]"

tokenizer = AutoTokenizer.from_pretrained("bert-base-chinese")  
lm_model = TTALMModel("bert-base-chinese")
tokenizer = AutoTokenizer.from_pretrained("bert-base-chinese")
lm_model.load_state_dict(torch.load("./wiki_zh.pt",map_location=torch.device('cuda')))
lm_model.to('cuda')
lm_model.eval()
model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(processor_name)

ds = load_dataset("common_voice", 'zh-TW', data_dir="./cv-corpus-6.1-2020-12-11", split="test")

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

    decoded_results = []
    for logit in logits:
        pred_ids = torch.argmax(logit, dim=-1)
        mask = ~pred_ids.eq(tokenizer.pad_token_id).unsqueeze(-1).expand(logit.size())
        vocab_size = logit.size()[-1]
        voice_prob = torch.nn.functional.softmax((torch.masked_select(logit, mask).view(-1,vocab_size)),dim=-1)
        lm_input = torch.masked_select(pred_ids, ~pred_ids.eq(tokenizer.pad_token_id)).unsqueeze(0)
        lm_prob = torch.nn.functional.softmax(lm_model.forward(lm_input)[0], dim=-1).squeeze(0)
        comb_pred_ids = torch.argmax(lm_prob*voice_prob, dim=-1)
        decoded_results.append(processor.decode(comb_pred_ids))

    batch["predicted"] = decoded_results
    batch["target"] = batch["sentence"]
    return batch


result = ds.map(map_to_pred, batched=True, batch_size=16, remove_columns=list(ds.features.keys()))

def cer_cal(groundtruth, hypothesis):
    err = 0
    tot = 0
    for p, t in zip(hypothesis, groundtruth):
        err += float(ed.eval(p.lower(), t.lower()))
        tot += len(t)
    return err / tot
print("CER: {:2f}".format(100 * cer_cal(result["target"],result["predicted"])))
```

`CER: 25.77`.   
`TIME: 06:01 min`
