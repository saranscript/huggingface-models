---
language: de
datasets:
- common_voice
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Large 53
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice de
      type: common_voice
      args: de
    metrics:
       - name: Test WER
         type: wer
         value: 29.35 
---

# Wav2Vec2-Large-XLSR-53-German

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on German using 3% of the [Common Voice](https://huggingface.co/datasets/common_voice) dataset. 
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "de", split="test[:2%]") 

processor = Wav2Vec2Processor.from_pretrained("marcel/wav2vec2-large-xlsr-german-demo")
model = Wav2Vec2ForCTC.from_pretrained("marcel/wav2vec2-large-xlsr-german-demo") 

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

The model can be evaluated as follows on the {language} test data of Common Voice.


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "de", split="test[:10%]")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("marcel/wav2vec2-large-xlsr-german-demo")
model = Wav2Vec2ForCTC.from_pretrained("marcel/wav2vec2-large-xlsr-german-demo") 
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“\%\”\�\カ\æ\無\ན\カ\臣\ѹ\…\«\»\ð\ı\„\幺\א\ב\比\ш\ע\)\ứ\в\œ\ч\+\—\ш\‚\נ\м\ń\乡\$\=\ש\ф\支\(\°\и\к\̇]'
substitutions = {
    'e' : '[\ə\é\ě\ę\ê\ế\ế\ë\ė\е]',
    'o' : '[\ō\ô\ô\ó\ò\ø\ọ\ŏ\õ\ő\о]',
    'a' : '[\á\ā\ā\ă\ã\å\â\à\ą\а]',
    'c' : '[\č\ć\ç\с]',
    'l' : '[\ł]',
    'u' : '[\ú\ū\ứ\ů]',
    'und' : '[\&]',
    'r' : '[\ř]',
    'y' : '[\ý]',
    's' : '[\ś\š\ș\ş]',
    'i' : '[\ī\ǐ\í\ï\î\ï]',
    'z' : '[\ź\ž\ź\ż]',
    'n' : '[\ñ\ń\ņ]',
    'g' : '[\ğ]',
    'ss' : '[\ß]',
    't' : '[\ț\ť]',
    'd' : '[\ď\đ]',
    "'": '[\ʿ\་\’\`\´\ʻ\`\‘]',
    'p': '\р'
}
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
    for x in substitutions:
        batch["sentence"] = re.sub(substitutions[x], x, batch["sentence"])
        speech_array, sampling_rate = torchaudio.load(batch["path"])
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

**Test Result**: 29.35 % 


## Training

The first 3% of the Common Voice `train`, `validation` datasets were used for training.

The script used for training can be found TODO
