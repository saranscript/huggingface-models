---
language: bem 
datasets:
- BembaSpeech 
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Bemba by Claytone Sikasote     
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: BembaSpeech bem 
      type: bembaspeech
      args: bem 
    metrics:
       - name: Test WER
         type: wer
         value: 42.17 
---

# Wav2Vec2-Large-XLSR-53-Bemba

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Bemba language of Zambia using the [BembaSpeech](https://csikasote.github.io/BembaSpeech). When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("csv", data_files={"test": "/content/test.csv"}, delimiter="\t")["test"] # Adapt the path to test.csv

processor = Wav2Vec2Processor.from_pretrained("csikasote/wav2vec2-large-xlsr-bemba") 
model = Wav2Vec2ForCTC.from_pretrained("csikasote/wav2vec2-large-xlsr-bemba") 

#BembaSpeech is sample at 16kHz so we you do not need to resample
#resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = speech_array.squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
     logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```

## Evaluation

The model can be evaluated as follows on the Bemba test data of BembaSpeech.  


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("csv", data_files={"test": "/content/test.csv"}, delimiter="\\t")["test"] 
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("csikasote/wav2vec2-large-xlsr-bemba") 
model = Wav2Vec2ForCTC.from_pretrained("csikasote/wav2vec2-large-xlsr-bemba") 
model.to("cuda")

chars_to_ignore_regex = '[\,\_\?\.\!\;\:\"\“]'  
#resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = speech_array.squeeze().numpy() 
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

**Test Result**: 42.17 %  

## Training

The BembaSpeech `train`, `dev` and `test` datasets were used for training, development and evaluation respectively. The script used for evaluating the model on the test dataset can be found [here](https://colab.research.google.com/drive/1aplFHfaXE68HGDwBYV2KqUWPasrk7bXv?usp=sharing).
