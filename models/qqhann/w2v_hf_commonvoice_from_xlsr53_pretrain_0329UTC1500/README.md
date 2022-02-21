---
language: ja 
datasets:
- common_voice #TODO: remove if you did not use the common voice dataset
- TODO: add more datasets if you have used additional datasets. Make sure to use the exact same 
dataset name as the one found [here](https://huggingface.co/datasets). If the dataset can not be found in the official datasets, just give it a new name
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
         value: 70.1869
---

# Wav2Vec2-Large-XLSR-53-Japanese

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Japanese using the [Common Voice](https://huggingface.co/datasets/common_voice), ... and ... dataset{s}.
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "ja", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("qqhann/w2v_hf_commonvoice_from_xlsr53_pretrain_0329UTC1500")
model = Wav2Vec2ForCTC.from_pretrained("qqhann/w2v_hf_commonvoice_from_xlsr53_pretrain_0329UTC1500")

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
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "ja", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("qqhann/w2v_hf_commonvoice_from_xlsr53_pretrain_0329UTC1500")
model = Wav2Vec2ForCTC.from_pretrained("qqhann/w2v_hf_commonvoice_from_xlsr53_pretrain_0329UTC1500")
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“]'  # TODO: adapt this list to include all special characters you removed from the data
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
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

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Result**: 70.18 %

## Training

The Common Voice `train`, `validation`, and ... datasets were used for training as well as ... and ...

<!-- # TODO: adapt to state all the datasets that were used for training. -->

The script used for training can be found [here](...)

<!-- # TODO: fill in a link to your training script here. If you trained your model in a colab, simply fill in the link here. If you trained the model locally, it would be great if you could upload the training script on github and paste the link here. -->
