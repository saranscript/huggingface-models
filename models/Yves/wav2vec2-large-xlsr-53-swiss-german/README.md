---
language: sg
datasets:
- Yves/fhnw_swiss_parliament
metrics:
- wer
tags:
- audio
- speech
- wav2vec2
- sg
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
- PyTorch
license: apache-2.0
model-index:
- name: Yves XLSR Wav2Vec2 Large 53 Swiss German
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Yves/fhnw_swiss_parliament
      type: Yves/fhnw_swiss_parliament
    metrics:
       - name: Test WER
         type: wer
         value: NA%
---
# wav2vec2-large-xlsr-53-swiss-german
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Swiss German trying to achieve satisfactory Swiss-German to German transcriptions

## Dataset
Detailed information about the dataset that the model has been trained and validated with is available on [Yves/fhnw_swiss_parliament](https://huggingface.co/datasets/Yves/fhnw_swiss_parliament)

## Usage
The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("Yves/fhnw_swiss_parliament", data_dir="swiss_parliament", split="validation")

processor = Wav2Vec2Processor.from_pretrained("Yves/wav2vec2-large-xlsr-53-swiss-german")
model = Wav2Vec2ForCTC.from_pretrained("Yves/wav2vec2-large-xlsr-53-swiss-german").cuda()

resampler = torchaudio.transforms.Resample(48_000, 16_000)

def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values.cuda(), attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"])
```

## Evaluation
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
import csv

model_name = "Yves/wav2vec2-large-xlsr-53-swiss-german"
device = "cuda"

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“\%\‘\”\_\²\…\˟\&\+\[\]\(\−\–\)\›\»\‹\@\«\*\ʼ\/\°\'\'\’\'̈]'

completed_iterations = 0
eval_batch_size = 16

model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(model_name)

ds = load_dataset("Yves/fhnw_swiss_parliament", data_dir="container_0/swiss_parliament_dryrun", split="validation")

wer = load_metric("wer")
cer = load_metric("cer")
bleu = load_metric("sacrebleu")

resampler = torchaudio.transforms.Resample(orig_freq=48_000, new_freq=16_000)

def map_to_array(batch):
    speech, _ = torchaudio.load(batch["path"])
    batch["speech"] = resampler.forward(speech.squeeze(0)).numpy()
    batch["sampling_rate"] = resampler.new_freq
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace("’", "'")
    return batch

ds = ds.map(map_to_array)

out_file = open('output.tsv', 'w', encoding='utf-8')
tsv_writer = csv.writer(out_file, delimiter='\t')
tsv_writer.writerow(["client_id", "reference", "prediction", "wer", "cer", "bleu"])

def map_to_pred(batch,idx):
    features = processor(batch["speech"], sampling_rate=batch["sampling_rate"][0], padding=True, return_tensors="pt")
    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)
    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits
    pred_ids = torch.argmax(logits, dim=-1)
    batch["predicted"] = processor.batch_decode(pred_ids)
    batch["target"] = batch["sentence"]
    if not (len(idx) <= 2 and idx[0] == 0):
        for x in range(0, len(idx)):
            temp_reference = []
            temp_reference.append([batch["target"][x]])
            tsv_writer.writerow([batch["client_id"][x], batch["target"][x], batch["predicted"][x],                   
            wer.compute(predictions=[batch["predicted"][x]], references=[batch["sentence"][x]]), 
            cer.compute(predictions=[batch["predicted"][x]], references=[batch["sentence"][x]]),
            bleu.compute(predictions=[batch["predicted"][x]], references=temp_reference)["score"]])
    return batch

result = ds.map(map_to_pred, batched=True, batch_size=eval_batch_size, with_indices=True, remove_columns=list(ds.features.keys()))

out_file.close()

target_bleu = []
for x in result["target"]:
    target_bleu.append([x])
   
print(wer.compute(predictions=result["predicted"], references=result["target"]))
print(cer.compute(predictions=result["predicted"], references=result["target"]))
print(bleu.compute(predictions=result["predicted"], references=target_bleu))
```
 
## Scripts
The script used for training can be found on Google Colab [TBD](https://huggingface.co/Yves/wav2vec2-large-xlsr-53-swiss-german)