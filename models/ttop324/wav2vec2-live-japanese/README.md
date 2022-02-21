---
language: ja
datasets:
- common_voice
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: wav2vec2-live-japanese
  results:
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice Japanese
      type: common_voice
      args: ja
    metrics:
       - name: Test WER
         type: wer
         value: 21.48%
       - name: Test CER
         type: cer
         value: 9.82%
---
# wav2vec2-live-japanese
https://github.com/ttop32/wav2vec2-live-japanese-translator    
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Japanese hiragana using the 
- [common_voice](https://huggingface.co/datasets/common_voice)     
- [JSUT](https://sites.google.com/site/shinnosuketakamichi/publication/jsut)     
- [CSS10](https://github.com/Kyubyong/css10)     
- [TEDxJP-10K](https://github.com/laboroai/TEDxJP-10K)     
- [JVS](https://sites.google.com/site/shinnosuketakamichi/research-topics/jvs_corpus)
- [JSSS](https://sites.google.com/site/shinnosuketakamichi/research-topics/jsss_corpus)
## Inference
```python
#usage
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
model = Wav2Vec2ForCTC.from_pretrained("ttop324/wav2vec2-live-japanese")
processor = Wav2Vec2Processor.from_pretrained("ttop324/wav2vec2-live-japanese")
test_dataset = load_dataset("common_voice", "ja", split="test")
# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = torchaudio.functional.resample(speech_array, sampling_rate, 16000)[0].numpy()    
    return batch
test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset[:2]["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)
with torch.no_grad():
	logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits
predicted_ids = torch.argmax(logits, dim=-1)
print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset[:2]["sentence"])
```
## Evaluation
```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re
import pykakasi 
import MeCab
wer = load_metric("wer")
cer = load_metric("cer")
model = Wav2Vec2ForCTC.from_pretrained("ttop324/wav2vec2-live-japanese").to("cuda")
processor = Wav2Vec2Processor.from_pretrained("ttop324/wav2vec2-live-japanese")
test_dataset = load_dataset("common_voice", "ja", split="test")
chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“\‘\”\�‘、。．！，・―─~｢｣『』\\\\※\[\]\{\}「」〇？…]'
wakati = MeCab.Tagger("-Owakati")
kakasi = pykakasi.kakasi()
kakasi.setMode("J","H")      # kanji to hiragana
kakasi.setMode("K","H")      # katakana to hiragana
conv = kakasi.getConverter()
FULLWIDTH_TO_HALFWIDTH = str.maketrans(
    '　０１２３４５６７８９ａｂｃｄｅｆｇｈｉｊｋｌｍｎｏｐｑｒｓｔｕｖｗｘｙｚＡＢＣＤＥＦＧＨＩＪＫＬＭＮＯＰＱＲＳＴＵＶＷＸＹＺ！゛＃＄％＆（）＊＋、ー。／：；〈＝〉？＠［］＾＿‘｛｜｝～',
    ' 0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ!"#$%&()*+,-./:;<=>?@[]^_`{|}~',
)
def fullwidth_to_halfwidth(s):
    return s.translate(FULLWIDTH_TO_HALFWIDTH)
def preprocessData(batch):
    batch["sentence"] = fullwidth_to_halfwidth(batch["sentence"])
    batch["sentence"] = re.sub(chars_to_ignore_regex,' ', batch["sentence"]).lower()  #remove special char
    batch["sentence"] = wakati.parse(batch["sentence"])                              #add space
    batch["sentence"] = conv.do(batch["sentence"])                                   #covert to hiragana
    batch["sentence"] = " ".join(batch["sentence"].split())+" "                         #remove multiple space 
    
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = torchaudio.functional.resample(speech_array, sampling_rate, 16000)[0].numpy()    
    return batch
test_dataset = test_dataset.map(preprocessData)
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
print("CER: {:2f}".format(100 * cer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```