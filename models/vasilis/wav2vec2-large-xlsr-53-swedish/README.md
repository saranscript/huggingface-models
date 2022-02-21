---
language: sv-SE
datasets:
- common_voice
- NST Swedish ASR Database
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
- name: V XLSR Wav2Vec2 Large 53 - Swedish
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice sv-SE
      type: common_voice
      args: sv-SE
    metrics:
       - name: Test WER
         type: wer
         value: 14.695793
       - name: Test CER
         type: cer
         value: 5.264666
---

# Wav2Vec2-Large-XLSR-53-Swedish

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Swedish using the [Common Voice](https://huggingface.co/datasets/common_voice)  and parts for the [NST Swedish ASR Database](https://www.nb.no/sprakbanken/en/resource-catalogue/oai-nb-no-sbr-16/).
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "sv-SE", split="test[:2%]") #TODO: replace {lang_id} in your language code here. Make sure the code is one of the *ISO codes* of [this](https://huggingface.co/languages) site.

processor = Wav2Vec2Processor.from_pretrained("vasilis/wav2vec2-large-xlsr-53-swedish") #TODO: replace {model_id} with your model id. The model id consists of {your_username}/{your_modelname}, *e.g.* `elgeish/wav2vec2-large-xlsr-53-arabic`
model = Wav2Vec2ForCTC.from_pretrained("vasilis/wav2vec2-large-xlsr-53-swedish") #TODO: replace {model_id} with your model id. The model id consists of {your_username}/{your_modelname}, *e.g.* `elgeish/wav2vec2-large-xlsr-53-arabic`

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

The model can be evaluated as follows on the Swedish test data of Common Voice.


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "sv-SE", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("vasilis/wav2vec2-large-xlsr-53-swedish")
model = Wav2Vec2ForCTC.from_pretrained("vasilis/wav2vec2-large-xlsr-53-swedish")
model.to("cuda")

chars_to_ignore_regex = "[\,\?\.\!\-\;\:\"\“\%\‘\”\�\']"  # TODO: adapt this list to include all special characters you removed from the data

resampler = {
    48_000: torchaudio.transforms.Resample(48_000, 16_000),
    44100: torchaudio.transforms.Resample(44100, 16_000),
    32000: torchaudio.transforms.Resample(32000, 16_000)
}

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler[sampling_rate](speech_array).squeeze().numpy()
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
print("CER: {:2f}".format(100 * wer.compute(predictions=[" ".join(list(entry)) for entry in result["pred_strings"]], references=[" ".join(list(entry)) for entry in result["sentence"]])))

```

**Test Result**:  14.695793 %

## Training

As first step used Common Voice train dataset and parts from NST
as can be found [here](https://github.com/se-asr/nst/tree/master).
Part of NST where removed using this mask

```python
mask = [(5 < len(x.split()) < 20) and np.average([len(entry) for entry in x.split()]) > 5 for x in dataset['transcript'].tolist()]
```

After training like this for 20000 steps the model was finetuned on all of nst data using the mask

```python
mask = [(1 < len(x.split()) < 25) and np.average([len(entry) for entry in x.split()]) > 3 for x in dataset['transcript'].tolist()]
```

and all of common voice for 100000 more steps approximately 16 epochs.
