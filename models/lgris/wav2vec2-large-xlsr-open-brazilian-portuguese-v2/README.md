---
language: pt
datasets:
- common_voice 
- mls
- cetuc
- lapsbm
- voxforge
metrics:
- wer
tags:
- audio
- speech
- wav2vec2
- pt
- portuguese-speech-corpus
- automatic-speech-recognition
- speech
- PyTorch
license: apache-2.0
---

# Wav2vec 2.0 With Open Brazilian Portuguese Datasets v2

This a the demonstration of a fine-tuned Wav2vec model for Brazilian Portuguese using the following datasets:

- [CETUC](http://www02.smt.ufrj.br/~igor.quintanilha/alcaim.tar.gz): contains approximately 145 hours of Brazilian Portuguese speech distributed among 50 male and 50 female speakers, each pronouncing approximately 1,000 phonetically balanced sentences selected from the [CETEN-Folha](https://www.linguateca.pt/cetenfolha/) corpus.
- [Multilingual Librispeech (MLS)](https://arxiv.org/abs/2012.03411): a massive dataset available in many languages. The MLS is based on audiobook recordings in public domain like [LibriVox](https://librivox.org/). The dataset contains a total of 6k hours of transcribed data in many languages. The set in Portuguese [used in this work](http://www.openslr.org/94/) (mostly Brazilian variant) has approximately 284 hours of speech, obtained from 55 audiobooks read by 62 speakers.
- [VoxForge](http://www.voxforge.org/): is a project with the goal to build open datasets for acoustic models. The corpus contains approximately 100 speakers and 4,130 utterances of Brazilian Portuguese, with sample rates varying from 16kHz to 44.1kHz.
- [Common Voice 6.1](https://commonvoice.mozilla.org/pt): is a project proposed by Mozilla Foundation with the goal to create a wide open dataset in different languages to train ASR models. In this project, volunteers donate and validate speech using the [oficial site](https://commonvoice.mozilla.org/pt). The set in Portuguese (mostly Brazilian variant) used in this work is the 6.1 version (pt_63h_2020-12-11) that contains about 50 validated hours and 1,120 unique speakers.
- [Lapsbm](https://github.com/falabrasil/gitlab-resources): "Falabrasil - UFPA" is a dataset used by the Fala Brasil group to benchmark ASR systems in Brazilian Portuguese. Contains 35 speakers (10 females), each one pronouncing 20 unique sentences, totalling  700 utterances in Brazilian Portuguese. The audios were recorded in 22.05 kHz without environment control.

These datasets were combined to build a larger Brazilian Portuguese dataset. All data was used for training except Common Voice dev/test sets, that were used for validation/test respectively.

The original model was fine-tuned using [fairseq](https://github.com/pytorch/fairseq). This notebook uses a converted version of the original one.

__NOTE: The common voice test reports 10% of WER, however, this model was trained using all the validated instances of Common Voice, except the instances of the test set. This means that some speakers of the train set can be present on the test set.__

## Imports and dependencies


```python
%%capture
!pip install datasets
!pip install jiwer
!pip install torchaudio
!pip install transformers
!pip install soundfile
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
```

## Preparation


```python
chars_to_ignore_regex = '[\,\?\.\!\;\:\"]'  # noqa: W605
wer = load_metric("wer")
device = "cuda"
```


```python
model_name = 'lgris/wav2vec2-large-xlsr-open-brazilian-portuguese-v2'
model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(model_name)
```


```python
def map_to_pred(batch):
    features = processor(batch["speech"], sampling_rate=batch["sampling_rate"][0], padding=True, return_tensors="pt")
    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)
    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits
    pred_ids = torch.argmax(logits, dim=-1)
    batch["predicted"] = processor.batch_decode(pred_ids)
    batch["predicted"] = [pred.lower() for pred in batch["predicted"]]
    batch["target"] = batch["sentence"]
    return batch
```

## Tests

### Test against Common Voice (In-domain)


```python
dataset = load_dataset("common_voice", "pt", split="test", data_dir="./cv-corpus-6.1-2020-12-11")

resampler = torchaudio.transforms.Resample(orig_freq=48_000, new_freq=16_000)

def map_to_array(batch):
    speech, _ = torchaudio.load(batch["path"])
    batch["speech"] = resampler.forward(speech.squeeze(0)).numpy()
    batch["sampling_rate"] = resampler.new_freq
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace("’", "'")
    return batch
```


```python
ds = dataset.map(map_to_array)
result = ds.map(map_to_pred, batched=True, batch_size=1, remove_columns=list(ds.features.keys()))
print(wer.compute(predictions=result["predicted"], references=result["target"]))
for pred, target in zip(result["predicted"][:10], result["target"][:10]):
    print(pred, "|", target) 
```

**Result**: 10.69%

### Test against [TEDx](http://www.openslr.org/100/) (Out-of-domain)


```python
!gdown --id 1HJEnvthaGYwcV_whHEywgH2daIN4bQna
!tar -xf tedx.tar.gz
```


```python
dataset = load_dataset('csv', data_files={'test': 'test.csv'})['test']

def map_to_array(batch):
    speech, _ = torchaudio.load(batch["path"])
    batch["speech"] = speech.squeeze(0).numpy()
    batch["sampling_rate"] = resampler.new_freq
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace("’", "'")
    return batch
```


```python
ds = dataset.map(map_to_array)
result = ds.map(map_to_pred, batched=True, batch_size=1, remove_columns=list(ds.features.keys()))
print(wer.compute(predictions=result["predicted"], references=result["target"]))
for pred, target in zip(result["predicted"][:10], result["target"][:10]):
    print(pred, "|", target) 
```

**Result**: 34.53%