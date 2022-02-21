---
language: en
datasets:
- timit_asr
tags:
- audio
- automatic-speech-recognition
- speech
license: apache-2.0
---

# Wav2Vec2-Base-TIMIT

Fine-tuned [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base)
on the [timit_asr dataset](https://huggingface.co/datasets/timit_asr).
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import soundfile as sf
import torch
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

model_name = "elgeish/wav2vec2-base-timit-asr"
processor = Wav2Vec2Processor.from_pretrained(model_name)
model = Wav2Vec2ForCTC.from_pretrained(model_name)
model.eval()

dataset = load_dataset("timit_asr", split="test").shuffle().select(range(10))
char_translations = str.maketrans({"-": " ", ",": "", ".": "", "?": ""})

def prepare_example(example):
    example["speech"], _ = sf.read(example["file"])
    example["text"] = example["text"].translate(char_translations)
    example["text"] = " ".join(example["text"].split())  # clean up whitespaces
    example["text"] = example["text"].lower()
    return example

dataset = dataset.map(prepare_example, remove_columns=["file"])
inputs = processor(dataset["speech"], sampling_rate=16000, return_tensors="pt", padding="longest")

with torch.no_grad():
    predicted_ids = torch.argmax(model(inputs.input_values).logits, dim=-1)
predicted_ids[predicted_ids == -100] = processor.tokenizer.pad_token_id  # see fine-tuning script
predicted_transcripts = processor.tokenizer.batch_decode(predicted_ids)

for reference, predicted in zip(dataset["text"], predicted_transcripts):
    print("reference:", reference)
    print("predicted:", predicted)
    print("--")
```

Here's the output:

```
reference: she had your dark suit in greasy wash water all year
predicted: she had your dark suit in greasy wash water all year
--
reference: where were you while we were away
predicted: where were you while we were away
--
reference: cory and trish played tag with beach balls for hours
predicted: tcory and trish played tag with beach balls for hours
--
reference: tradition requires parental approval for under age marriage
predicted: tradition requires parrental proval for under age marrage
--
reference: objects made of pewter are beautiful
predicted: objects made of puder are bautiful
--
reference: don't ask me to carry an oily rag like that
predicted: don't o ask me to carry an oily rag like that
--
reference: cory and trish played tag with beach balls for hours
predicted: cory and trish played tag with beach balls for ours
--
reference: don't ask me to carry an oily rag like that
predicted: don't ask me to carry an oily rag like that
--
reference: don't do charlie's dirty dishes
predicted: don't  do chawly's tirty dishes
--
reference: only those story tellers will remain who can imitate the style of the virtuous
predicted: only those story tillaers will remain who can imvitate the style the virtuous
```

## Fine-Tuning Script

You can find the script used to produce this model
[here](https://github.com/elgeish/transformers/blob/cfc0bd01f2ac2ea3a5acc578ef2e204bf4304de7/examples/research_projects/wav2vec2/finetune_base_timit_asr.sh).
