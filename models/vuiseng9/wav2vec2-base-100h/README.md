---
language: en
datasets:
- librispeech_asr
tags:
- audio
- automatic-speech-recognition
license: apache-2.0
---

# Wav2Vec2-Base-100h

This is a fork of [```facebook/wav2vec2-base-100h```](https://huggingface.co/facebook/wav2vec2-base-100h)

### Changes & Notes
1. Document reproducible evaluation (below) to new transformer and datasets version.
2. Use batch size of 1 to reproduce results. 
3. Validated with ```transformers v4.15.0```, ```datasets 1.18.0```
4. You may need to manually install pypkg ```librosa```, ```jiwer```

 
 ## Evaluation
 
 This code snippet shows how to evaluate **facebook/wav2vec2-base-100h** on LibriSpeech's "clean" and "other" test data.
 
```python
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import soundfile as sf
import torch
from jiwer import wer

librispeech_eval = load_dataset("librispeech_asr", "clean", split="test")
# librispeech_eval = load_dataset("librispeech_asr", "other", split="test")

model = Wav2Vec2ForCTC.from_pretrained("facebook/wav2vec2-base-100h").to("cuda")
processor = Wav2Vec2Processor.from_pretrained("facebook/wav2vec2-base-100h")

def map_to_array(batch):
    # speech, _ = sf.read(batch["file"])
    # batch["speech"] = speech
    batch["speech"] = batch['audio']['array']
    return batch

librispeech_eval = librispeech_eval.map(map_to_array)

def map_to_pred(batch):
    input_values = processor(batch["speech"], return_tensors="pt", padding="longest").input_values
    with torch.no_grad():
        logits = model(input_values.to("cuda")).logits

    predicted_ids = torch.argmax(logits, dim=-1)
    transcription = processor.batch_decode(predicted_ids)
    batch["transcription"] = transcription
    return batch

result = librispeech_eval.map(map_to_pred, batched=True, batch_size=1, remove_columns=["speech"])

print("WER:", wer(result["text"], result["transcription"]))
```

*Result (WER)*:

| "clean/test" | "other/test" |
|--------------| ------------|
| 6.1 | 13.5 |
