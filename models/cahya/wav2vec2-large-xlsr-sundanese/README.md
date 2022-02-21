---
language: su
datasets:
- openslr
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Sundanese by cahya
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: OpenSLR High quality TTS data for Sundanese
      type: OpenSLR
      args: su
    metrics:
       - name: Test WER
         type: wer
         value: 6.19
---

# Wav2Vec2-Large-XLSR-Sundanese

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53)
on the [OpenSLR High quality TTS data for Sundanese](https://openslr.org/44/).
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
from datasets import load_dataset, load_metric, Dataset
from datasets.utils.download_manager import DownloadManager
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from pathlib import Path
import pandas as pd


def load_dataset_sundanese():
    urls = [
        "https://www.openslr.org/resources/44/su_id_female.zip",
        "https://www.openslr.org/resources/44/su_id_male.zip"
    ]
    dm = DownloadManager()
    download_dirs = dm.download_and_extract(urls)
    data_dirs = [ 
        Path(download_dirs[0])/"su_id_female/wavs",
        Path(download_dirs[1])/"su_id_male/wavs",
    ]
    filenames = [ 
        Path(download_dirs[0])/"su_id_female/line_index.tsv",
        Path(download_dirs[1])/"su_id_male/line_index.tsv",
    ]

    dfs = []
    
    dfs.append(pd.read_csv(filenames[0], sep='\t4?\t', names=["path", "sentence"]))
    dfs.append(pd.read_csv(filenames[1], sep='\t\t', names=["path", "sentence"]))
    
    for i, dir in enumerate(data_dirs):
        dfs[i]["path"] = dfs[i].apply(lambda row: str(data_dirs[i]) + "/" + row + ".wav", axis=1)
    df = pd.concat(dfs)
    # df = df.sample(frac=1, random_state=1).reset_index(drop=True)
    dataset = Dataset.from_pandas(df)
    dataset = dataset.remove_columns('__index_level_0__')
    
    return dataset.train_test_split(test_size=0.1, seed=1)
    
dataset = load_dataset_sundanese()
test_dataset = dataset['test']

processor = Wav2Vec2Processor.from_pretrained("cahya/wav2vec2-large-xlsr-sundanese")
model = Wav2Vec2ForCTC.from_pretrained("cahya/wav2vec2-large-xlsr-sundanese")

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
print("Reference:", test_dataset[:2]["sentence"])
```


## Evaluation

The model can be evaluated as follows or using the [notebook](https://github.com/cahya-wirawan/indonesian-speech-recognition/blob/main/XLSR_Wav2Vec2_for_Indonesian_Evaluation-Sundanese.ipynb).

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric, Dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets.utils.download_manager import DownloadManager
import re
from pathlib import Path
import pandas as pd


def load_dataset_sundanese():
    urls = [
        "https://www.openslr.org/resources/44/su_id_female.zip",
        "https://www.openslr.org/resources/44/su_id_male.zip"
    ]
    dm = DownloadManager()
    download_dirs = dm.download_and_extract(urls)
    data_dirs = [ 
        Path(download_dirs[0])/"su_id_female/wavs",
        Path(download_dirs[1])/"su_id_male/wavs",
    ]
    filenames = [ 
        Path(download_dirs[0])/"su_id_female/line_index.tsv",
        Path(download_dirs[1])/"su_id_male/line_index.tsv",
    ]

    dfs = []
    
    dfs.append(pd.read_csv(filenames[0], sep='\t4?\t', names=["path", "sentence"]))
    dfs.append(pd.read_csv(filenames[1], sep='\t\t', names=["path", "sentence"]))
    
    for i, dir in enumerate(data_dirs):
        dfs[i]["path"] = dfs[i].apply(lambda row: str(data_dirs[i]) + "/" + row + ".wav", axis=1)
    df = pd.concat(dfs)
    # df = df.sample(frac=1, random_state=1).reset_index(drop=True)
    dataset = Dataset.from_pandas(df)
    dataset = dataset.remove_columns('__index_level_0__')
    
    return dataset.train_test_split(test_size=0.1, seed=1)
    
dataset = load_dataset_sundanese()
test_dataset = dataset['test']

wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("cahya/wav2vec2-large-xlsr-sundanese")
model = Wav2Vec2ForCTC.from_pretrained("cahya/wav2vec2-large-xlsr-sundanese") 
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“\%\‘\'\”_\�]'
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
# We need to read the audio files as arrays
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

**Test Result**: 6.19 %

## Training

[OpenSLR High quality TTS data for Sundanese](https://openslr.org/44/) was used for training.
The script used for training can be found [here](https://github.com/cahya-wirawan/indonesian-speech-recognition/blob/main/XLSR_Wav2Vec2_for_Indonesian_Evaluation-Sundanese.ipynb) 
and to [evaluate it](https://github.com/cahya-wirawan/indonesian-speech-recognition/blob/main/XLSR_Wav2Vec2_for_Indonesian_Evaluation-Sundanese.ipynb)
