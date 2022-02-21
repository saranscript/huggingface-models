---
language: ja
datasets:
  - common_voice
  - jsut
metrics:
  - wer
  - cer
tags:
  - audio
  - automatic-speech-recognition
  - speech
  - xlsr-fine-tuning-week
license: apache-2.0
model-index:
  - name: Japanese XLSR Wav2Vec2 Large 53
    results:
      - task:
          name: Speech Recognition
          type: automatic-speech-recognition
        dataset:
          name: Common Voice ja
          type: common_voice
          args: ja
        metrics:
          - name: Test WER
            type: wer
            value: 51.72
          - name: Test CER
            type: cer
            value: 24.89
---

# Wav2Vec2-Large-XLSR-53-Japanese

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Japanese using the [Common Voice](https://huggingface.co/datasets/common_voice), and JSUT dataset{s}.
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "ja", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("qqhann/w2v_hf_jsut_xlsr53")
model = Wav2Vec2ForCTC.from_pretrained("qqhann/w2v_hf_jsut_xlsr53")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```

## Evaluation

The model can be evaluated as follows on the Japanese test data of Common Voice.

```python
!pip install torchaudio
!pip install datasets transformers
!pip install jiwer
!pip install mecab-python3
!pip install unidic-lite
!python -m unidic download
!pip install jaconv

import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re
import MeCab
from jaconv import kata2hira
from typing import List

# Japanese preprocessing
tagger = MeCab.Tagger("-Owakati")
chars_to_ignore_regex = '[\。\、\「\」\,\?\.\!\-\;\:\"\“\%\‘\”\�]'

def text2kata(text):
    node = tagger.parseToNode(text)
    word_class = []
    while node:
        word = node.surface
        wclass = node.feature.split(',')
        if wclass[0] != u'BOS/EOS':
            if len(wclass) <= 6:
                word_class.append((word))
            elif wclass[6] == None:
                word_class.append((word))
            else:
                word_class.append((wclass[6]))
        node = node.next
    return ' '.join(word_class)

def hiragana(text):
    return kata2hira(text2kata(text))

test_dataset = load_dataset("common_voice", "ja", split="test")
wer = load_metric("wer")
resampler = torchaudio.transforms.Resample(48_000, 16_000) # JSUT is already 16kHz
# resampler = torchaudio.transforms.Resample(16_000, 16_000) # JSUT is already 16kHz

processor = Wav2Vec2Processor.from_pretrained("qqhann/w2v_hf_jsut_xlsr53")
model = Wav2Vec2ForCTC.from_pretrained("qqhann/w2v_hf_jsut_xlsr53")
model.to("cuda")


# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = hiragana(batch["sentence"]).strip()
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch


test_dataset = test_dataset.map(speech_file_to_array_fn)

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

def cer_compute(predictions: List[str], references: List[str]):
    p = [" ".join(list(" " + pred.replace(" ", ""))).strip() for pred in predictions]
    r = [" ".join(list(" " + ref.replace(" ", ""))).strip() for ref in references]
    return wer.compute(predictions=p, references=r)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
print("CER: {:2f}".format(100 * cer_compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Result**: 51.72 %

## Training

<!-- The Common Voice `train`, `validation`, and ... datasets were used for training as well as ... and ... # TODO: adapt to state all the datasets that were used for training. -->

The privately collected JSUT Japanese dataset was used for training.

<!-- The script used for training can be found [here](...) # TODO: fill in a link to your training script here. If you trained your model in a colab, simply fill in the link here. If you trained the model locally, it would be great if you could upload the training script on github and paste the link here. -->
