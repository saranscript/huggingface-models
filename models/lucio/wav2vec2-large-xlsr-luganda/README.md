---
language: lg
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
- name: XLSR Wav2Vec2 Large Luganda by Lucio
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice lg
      type: common_voice
      args: lg
    metrics:
       - name: Test WER
         type: wer
         value: 29.52
---

# Wav2Vec2-Large-XLSR-53-lg

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Luganda using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset, using train, validation and other (excluding voices that are in the test set), and taking the test data for validation as well as test.
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "lg", split="test[:2%]") 

processor = Wav2Vec2Processor.from_pretrained("lucio/wav2vec2-large-xlsr-luganda") 
model = Wav2Vec2ForCTC.from_pretrained("lucio/wav2vec2-large-xlsr-luganda")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset[:2]["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```


## Evaluation

The model can be evaluated as follows on the Luganda test data of Common Voice. (Available in Colab [here](https://colab.research.google.com/drive/1XxZ3mJOEXwIn-QH3C23jD_Qpom9aA1vH?usp=sharing).)


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re
import unidecode

test_dataset = load_dataset("common_voice", "lg", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("lucio/wav2vec2-large-xlsr-luganda") 
model = Wav2Vec2ForCTC.from_pretrained("lucio/wav2vec2-large-xlsr-luganda")
model.to("cuda")

chars_to_ignore_regex = '[\[\],?.!;:%"“”(){}‟ˮʺ″«»/…‽�–]'
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

def remove_special_characters(batch):
    # word-internal apostrophes are marking contractions
    batch["norm_text"] = re.sub(r'[‘’´`]', r"'", batch["sentence"])
    # most other punctuation is ignored
    batch["norm_text"] = re.sub(chars_to_ignore_regex, "", batch["norm_text"]).lower().strip()
    batch["norm_text"] = re.sub(r"(-|' | '|  +)", " ", batch["norm_text"])
    # remove accents from a few characters (from loanwords, not tones)
    batch["norm_text"] = unidecode.unidecode(batch["norm_text"])
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
test_dataset = test_dataset.map(remove_special_characters)

def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["norm_text"])))
```

**Test Result**: 29.52 % 

## Training

The Common Voice `train`, `validation` and `other` datasets were used for training, excluding voices that are in both the `other` and `test` datasets. The data was augmented to twice the original size with added noise and manipulated pitch, phase and intensity.
Training proceeded for 60 epochs, on 1 V100 GPU provided by OVHcloud. The `test` data was used for validation.

The [script used for training](https://github.com/serapio/transformers/blob/feature/xlsr-finetune/examples/research_projects/wav2vec2/run_common_voice.py) is adapted from the [example script provided in the transformers repo](https://github.com/huggingface/transformers/blob/master/examples/research_projects/wav2vec2/run_common_voice.py).