---
language: WOLOF
datasets:
- AI4D Baamtu Datamation - Automatic Speech Recognition in WOLOF
tags:
- speech
- audio
- automatic-speech-recognition
license: apache-2.0
metrics:
- WER
---

## Evaluation on WOLOF Test

[![github](https://img.shields.io/badge/github-ffbf00?logo=github&color=black&style=for-the-badge)](https://github.com/kingabzpro/WOLOF-ASR-Wav2Vec2)
```python
import pandas as pd
from datasets import load_dataset, load_metric,Dataset
from tqdm import tqdm
import torch
import soundfile as sf
import torchaudio
from transformers import Wav2Vec2ForCTC
from transformers import Wav2Vec2Processor
from transformers import Wav2Vec2FeatureExtractor
from transformers import Wav2Vec2CTCTokenizer

model_name = "kingabzpro/wav2vec2-large-xlsr-53-wolof"
device = "cuda"

model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(model_name)

val =pd.read_csv("../input/automatic-speech-recognition-in-wolof/Test.csv")
val["path"] = "../input/automatic-speech-recognition-in-wolof/Noise Removed/tmp/WOLOF_ASR_dataset/noise_remove/"+val["ID"]+".wav"
val.rename(columns = {'transcription':'sentence'}, inplace = True)
common_voice_val = Dataset.from_pandas(val)

def speech_file_to_array_fn_test(batch):
    speech_array, sampling_rate = sf.read(batch["path"])#(.wav) 16000 sample rate
    batch["speech"] = speech_array
    batch["sampling_rate"] = sampling_rate
    return batch

def prepare_dataset_test(batch):
    # check that all files have the correct sampling rate
    assert (
        len(set(batch["sampling_rate"])) == 1
    ), f"Make sure all inputs have the same sampling rate of {processor.feature_extractor.sampling_rate}."

    batch["input_values"] = processor(batch["speech"], padding=True,sampling_rate=batch["sampling_rate"][0]).input_values
    return batch

common_voice_val = common_voice_val.remove_columns([ "ID","age",  "down_votes", "gender",  "up_votes"]) # Remove columns
common_voice_val = common_voice_val.map(speech_file_to_array_fn_test, remove_columns=common_voice_val.column_names)# Applying speech_file_to_array function
common_voice_val = common_voice_val.map(prepare_dataset_test, remove_columns=common_voice_val.column_names, batch_size=8, num_proc=4, batched=True)# Applying prepare_dataset_test function

final_pred = []
for i in tqdm(range(common_voice_val.shape[0])):# Testing model on Wolof Dataset    
    input_dict = processor(common_voice_val[i]["input_values"], return_tensors="pt", padding=True)

    logits = model(input_dict.input_values.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)[0]
    prediction = processor.decode(pred_ids)
    final_pred.append(prediction)

```
You can check my result on [Zindi](https://zindi.africa/competitions/ai4d-baamtu-datamation-automatic-speech-recognition-in-wolof/leaderboard), I got 8th rank in AI4D Baamtu Datamation - Automatic Speech Recognition in WOLOF

**Result**: 7.88 %