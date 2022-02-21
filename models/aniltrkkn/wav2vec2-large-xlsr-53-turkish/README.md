---
language: tr
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
- name: Wav2Vec2-Large-XLSR-53-Turkish
results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice tr
      type: common_voice
      args: tr
    metrics:
       - name: Test WER
         type: wer
         value: 17.46
---

# Wav2Vec2-Large-XLSR-53-Turkish

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Turkish using the [Common Voice](https://huggingface.co/datasets/common_voice).
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from unicode_tr import unicode_tr

test_dataset = load_dataset("common_voice", "tr", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("aniltrkkn/wav2vec2-large-xlsr-53-turkish")
model = Wav2Vec2ForCTC.from_pretrained("aniltrkkn/wav2vec2-large-xlsr-53-turkish")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
\tspeech_array, sampling_rate = torchaudio.load(batch["path"])
\tbatch["speech"] = resampler(speech_array).squeeze().numpy()
\treturn batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
\tlogits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```


## Evaluation

The model can be evaluated as follows on the Turkish test data of Common Voice.  


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "tr", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("aniltrkkn/wav2vec2-large-xlsr-53-turkish")
model = Wav2Vec2ForCTC.from_pretrained("aniltrkkn/wav2vec2-large-xlsr-53-turkish")
model.to("cuda")

chars_to_ignore_regex = '[\\,\\?\\.\\!\\-\\;\\:\\"\\“]'
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
\tbatch["sentence"] = str(unicode_tr(re.sub(chars_to_ignore_regex, "", batch["sentence"])).lower())
\tspeech_array, sampling_rate = torchaudio.load(batch["path"])
\tbatch["speech"] = resampler(speech_array).squeeze().numpy()
\treturn batch

test_dataset = test_dataset.map(speech_file_to_array_fn)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def evaluate(batch):
\tinputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

\twith torch.no_grad():
\t\tlogits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

\tpred_ids = torch.argmax(logits, dim=-1)
\tbatch["pred_strings"] = processor.batch_decode(pred_ids)
\treturn batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Result**: 17.46 %

## Training
unicode_tr package is used for converting sentences to lower case since regular lower() does not work well with Turkish.

Since training data is very limited for Turkish, all data is employed with a K-Fold (k=5) training approach. Best model out of the 5 trainings is uploaded. Training arguments:
    --num_train_epochs="30" \\
    --per_device_train_batch_size="32" \\
    --evaluation_strategy="steps" \\
    --activation_dropout="0.055" \\
    --attention_dropout="0.094" \\
    --feat_proj_dropout="0.04" \\
    --hidden_dropout="0.047" \\
    --layerdrop="0.041" \\
    --learning_rate="2.34e-4" \\
    --mask_time_prob="0.082" \\
    --warmup_steps="250" \\

All trainings took ~20 hours with a GeForce RTX 3090 Graphics Card.