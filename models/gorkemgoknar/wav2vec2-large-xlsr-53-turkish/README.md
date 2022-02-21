---
language: 
- tr
datasets:
- common_voice 
- movies
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Large Turkish with extended dataset by Gorkem Goknar 
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
         value: 50.41
---
# Wav2Vec2-Large-XLSR-53-Turkish

Note: This model is trained with 5 Turkish movies additional to common voice dataset.
Although WER is high (50%) per common voice test dataset,  performance from "other sources " seems pretty good.

Disclaimer: Please use another wav2vec2-tr model in hub for "clean environment" dialogues as they tend to do better in clean sounds with less background noise.

Dataset building from csv and merging code can be found on below of this Readme.

Please try speech yourself on the right side to see its performance.

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Turkish using the [Common Voice](https://huggingface.co/datasets/common_voice) and 5 Turkish movies that include background noise/talkers .

When using this model, make sure that your speech input is sampled at 16kHz.
## Usage
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
import pydub 
from pydub.utils import mediainfo
import array
from pydub import AudioSegment
from pydub.utils import get_array_type
import numpy as np 

from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
test_dataset = load_dataset("common_voice", "tr", split="test[:2%]") 
processor = Wav2Vec2Processor.from_pretrained("gorkemgoknar/wav2vec2-large-xlsr-53-turkish")
model = Wav2Vec2ForCTC.from_pretrained("gorkemgoknar/wav2vec2-large-xlsr-53-turkish") 



new_sample_rate = 16000

def audio_resampler(batch, new_sample_rate = 16000):
    
    #not working without complex library compilation in windows for mp3
    #speech_array, sampling_rate = torchaudio.load(batch["path"])
    #speech_array, sampling_rate = librosa.load(batch["path"])

    #sampling_rate =  pydub.utils.info['sample_rate']  ##gets current samplerate
    
    sound = pydub.AudioSegment.from_file(file=batch["path"])
    sampling_rate = new_sample_rate
    sound = sound.set_frame_rate(new_sample_rate)
    left = sound.split_to_mono()[0]
    bit_depth = left.sample_width * 8
    array_type = pydub.utils.get_array_type(bit_depth)

    numeric_array = np.array(array.array(array_type, left._data) )

    speech_array = torch.FloatTensor(numeric_array)
    
    batch["speech"] = numeric_array
    batch["sampling_rate"] = sampling_rate
    #batch["target_text"] = batch["sentence"]

    return batch
    

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch = audio_resampler(batch, new_sample_rate = new_sample_rate)
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
The model can be evaluated as follows on the Turkish test data of Common Voice. 
```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re
import pydub 
import array
import numpy as np 

test_dataset = load_dataset("common_voice", "tr", split="test") 
wer = load_metric("wer")
processor = Wav2Vec2Processor.from_pretrained("gorkemgoknar/wav2vec2-large-xlsr-53-turkish") 
model = Wav2Vec2ForCTC.from_pretrained("gorkemgoknar/wav2vec2-large-xlsr-53-turkish") 
model.to("cuda")

#Note: Not ignoring "'"  on this one 
#Note: Not ignoring "'"  on this one 
chars_to_ignore_regex = '[\\,\\?\\.\\!\\-\\;\\:\\"\\“\\%\\‘\\”\\�\\#\\>\\<\\_\\’\\[\\]\\{\\}]'


#resampler = torchaudio.transforms.Resample(48_000, 16_000)
#using custom load and transformer for audio  -> see audio_resampler
new_sample_rate = 16000

def audio_resampler(batch, new_sample_rate = 16000):
    
    #not working without complex library compilation in windows for mp3
    #speech_array, sampling_rate = torchaudio.load(batch["path"])
    #speech_array, sampling_rate = librosa.load(batch["path"])
    #sampling_rate =  pydub.utils.info['sample_rate']  ##gets current samplerate
    
    sound = pydub.AudioSegment.from_file(file=batch["path"])

    sound = sound.set_frame_rate(new_sample_rate)
    left = sound.split_to_mono()[0]
    bit_depth = left.sample_width * 8
    array_type = pydub.utils.get_array_type(bit_depth)

    numeric_array = np.array(array.array(array_type, left._data) )

    speech_array = torch.FloatTensor(numeric_array)
    
    
    return speech_array, new_sample_rate

def remove_special_characters(batch):

    ##this one comes from subtitles if additional timestamps not processed  -> 00:01:01   00:01:01,33
    batch["sentence"] = re.sub('\\b\\d{2}:\\d{2}:\\d{2}(,+\\d{2})?\\b', ' ', batch["sentence"])
    ##remove all caps in text [AÇIKLAMA] etc, do it before..
    batch["sentence"] = re.sub('\\[(\\b[A-Z]+\\])', '', batch["sentence"]) 
    ##replace three dots (that are inside string with single)
    batch["sentence"] = re.sub("([a-zA-Z]+)\\.\\.\\.", r"\\1.", batch["sentence"])
    #standart ignore list
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower() + " "
    
    return batch

    
# Preprocessing the datasets.
# We need to read the aduio files as arrays
new_sample_rate = 16000
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower() 
    ##speech_array, sampling_rate = torchaudio.load(batch["path"])
    ##load and conversion done in resampler , takes and returns batch
    speech_array, sampling_rate = audio_resampler(batch, new_sample_rate = new_sample_rate)
    batch["speech"] = speech_array
    batch["sampling_rate"] = sampling_rate
    batch["target_text"] = batch["sentence"]

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

print("EVALUATING:")

##for 8GB RAM on GPU best is batch_size 2 for windows,  4 may fit in linux only
result = test_dataset.map(evaluate, batched=True, batch_size=2)
print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))

```

**Test Result**: 50.41 %  


## Training


The Common Voice `train` and `validation` datasets were used for training. Additional 5 Turkish movies with subtitles also used for training.
Similar training model used as base fine-tuning, additional audio resampler is on above code.

Putting model building and merging code below for reference


```python
import pandas as pd 
from datasets import load_dataset, load_metric

import os 
from pathlib import Path
from datasets import Dataset
import csv

#Walk all subdirectories of base_set_path and find csv files
base_set_path = r'C:\\dataset_extracts'
csv_files = []
for path, subdirs, files in os.walk(base_set_path):
    for name in files:
        if name.endswith(".csv"):
            deckfile= os.path.join(path, name)
            csv_files.append(deckfile)

def get_dataset_from_csv_file(csvfilename,names=['sentence', 'path']):
  path = Path(csvfilename)
  csv_delimiter="\\t"  ##tab seperated, change if something else
  
  ##Pandas has bug reading non-ascii file names, make sure use open with encoding
  df=pd.read_csv(open(path, 'r', encoding='utf-8'), delimiter=csv_delimiter,header=None , names=names, encoding='utf8')
  return Dataset.from_pandas(df)

custom_datasets= []
for csv_file in csv_files:
  this_dataset=get_dataset_from_csv_file(csv_file) 
  custom_datasets.append(this_dataset)




from datasets import concatenate_datasets, load_dataset
from datasets import load_from_disk

# Merge datasets together (from csv files)
dataset_file_path = ".\\dataset_file"
custom_datasets_concat = concatenate_datasets( [dset for dset in custom_datasets] )

#save this one to disk
custom_datasets_concat.save_to_disk( dataset_file_path ) 

#load back from disk
custom_datasets_from_disk = load_from_disk(dataset_file_path)
```
