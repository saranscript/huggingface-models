---
language: en
datasets:
- librispeech_asr
tags:
- audio
- automatic-speech-recognition
license: apache-2.0
---

TODO: [To be filled]


## Evaluation on LibriSpeech Test

The following script shows how to evaluate this model on the [LibriSpeech](https://huggingface.co/datasets/librispeech_asr) *"clean"* and *"other"* test dataset.

```python
from datasets import load_dataset
from transformers import Speech2TextTransformerForConditionalGeneration, Speech2TextTransformerTokenizer
import soundfile as sf
from jiwer import wer

librispeech_eval = load_dataset("librispeech_asr", "clean", split="test")  # change to "other" for other test dataset

model = Speech2TextTransformerForConditionalGeneration.from_pretrained("valhalla/s2t_librispeech_small").to("cuda")
tokenizer = Speech2TextTransformerTokenizer.from_pretrained("valhalla/s2t_librispeech_small", do_upper_case=True)

def map_to_array(batch):
    speech, _ = sf.read(batch["file"])
    batch["speech"] = speech
    return batch

librispeech_eval = librispeech_eval.map(map_to_array)

def map_to_pred(batch):
    features = tokenizer(batch["speech"], sample_rate=16000, padding=True, return_tensors="pt")
    input_features = features.input_features.to("cuda")
    attention_mask = features.attention_mask.to("cuda")

    gen_tokens = model.generate(input_ids=input_features, attention_mask=attention_mask)
    batch["transcription"] = tokenizer.batch_decode(gen_tokens, skip_special_tokens=True)
    return batch

result = librispeech_eval.map(map_to_pred, batched=True, batch_size=8, remove_columns=["speech"])

print("WER:", wer(result["text"], result["transcription"]))
```

*Result (WER)*:

| "clean" | "other" |
|---|---|
| 4.3 | 9.0 |