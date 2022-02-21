---
language: en
datasets:
- superb
tags:
- speech
- audio
- wav2vec2
license: apache-2.0
---

# Wav2Vec2-Base for Intent Classification

## Model description

This is a ported version of [S3PRL's Wav2Vec2 for the SUPERB Intent Classification task](https://github.com/s3prl/s3prl/tree/master/s3prl/downstream/fluent_commands).

The base model is [wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base), which is pretrained on 16kHz 
sampled speech audio. When using the model make sure that your speech input is also sampled at 16Khz. 

For more information refer to [SUPERB: Speech processing Universal PERformance Benchmark](https://arxiv.org/abs/2105.01051)

## Task and dataset description

Intent Classification (IC) classifies utterances into predefined classes to determine the intent of
speakers. SUPERB uses the 
[Fluent Speech Commands](https://fluent.ai/fluent-speech-commands-a-dataset-for-spoken-language-understanding-research/) 
dataset, where each utterance is tagged with three intent labels: **action**, **object**, and **location**.

For the original model's training and evaluation instructions refer to the 
[S3PRL downstream task README](https://github.com/s3prl/s3prl/tree/master/s3prl/downstream#ic-intent-classification---fluent-speech-commands).


## Usage examples

You can use the model directly like so:
```python
import torch
import librosa
from datasets import load_dataset
from transformers import Wav2Vec2ForSequenceClassification, Wav2Vec2FeatureExtractor

def map_to_array(example):
    speech, _ = librosa.load(example["file"], sr=16000, mono=True)
    example["speech"] = speech
    return example

# load a demo dataset and read audio files
dataset = load_dataset("anton-l/superb_demo", "ic", split="test")
dataset = dataset.map(map_to_array)

model = Wav2Vec2ForSequenceClassification.from_pretrained("superb/wav2vec2-base-superb-ic")
feature_extractor = Wav2Vec2FeatureExtractor.from_pretrained("superb/wav2vec2-base-superb-ic")

# compute attention masks and normalize the waveform if needed
inputs = feature_extractor(dataset[:4]["speech"], sampling_rate=16000, padding=True, return_tensors="pt")

logits = model(**inputs).logits

action_ids = torch.argmax(logits[:, :6], dim=-1).tolist()
action_labels = [model.config.id2label[_id] for _id in action_ids]

object_ids = torch.argmax(logits[:, 6:20], dim=-1).tolist()
object_labels = [model.config.id2label[_id + 6] for _id in object_ids]

location_ids = torch.argmax(logits[:, 20:24], dim=-1).tolist()
location_labels = [model.config.id2label[_id + 20] for _id in location_ids]
```

## Eval results

The evaluation metric is accuracy.

|        | **s3prl** | **transformers** |
|--------|-----------|------------------|
|**test**| `0.9235`  | `N/A`         |

### BibTeX entry and citation info

```bibtex
@article{yang2021superb,
  title={SUPERB: Speech processing Universal PERformance Benchmark},
  author={Yang, Shu-wen and Chi, Po-Han and Chuang, Yung-Sung and Lai, Cheng-I Jeff and Lakhotia, Kushal and Lin, Yist Y and Liu, Andy T and Shi, Jiatong and Chang, Xuankai and Lin, Guan-Ting and others},
  journal={arXiv preprint arXiv:2105.01051},
  year={2021}
}
```