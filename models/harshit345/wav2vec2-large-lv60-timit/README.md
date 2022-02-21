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

# Wav2Vec2-Large-LV60-TIMIT

Fine-tuned [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60)
on the [timit_asr dataset](https://huggingface.co/datasets/timit_asr).
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import soundfile as sf
import torch
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

model_name = "hktayal345/wav2vec2-large-lv60-timit-asr"
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
reference: the emblem depicts the acropolis all aglow
predicted: the amblum depicts the acropolis all a glo
--
reference: don't ask me to carry an oily rag like that
predicted: don't ask me to carry an oily rag like that
--
reference: they enjoy it when i audition
predicted: they enjoy it when i addition
--
reference: set aside to dry with lid on sugar bowl
predicted: set aside to dry with a litt on shoogerbowl
--
reference: a boring novel is a superb sleeping pill
predicted: a bor and novel is a suberb sleeping peel
--
reference: only the most accomplished artists obtain popularity
predicted: only the most accomplished artists obtain popularity
--
reference: he has never himself done anything for which to be hated which of us has
predicted: he has never himself done anything for which to be hated which of us has
--
reference: the fish began to leap frantically on the surface of the small lake
predicted: the fish began to leap frantically on the surface of the small lake
--
reference: or certain words or rituals that child and adult go through may do the trick
predicted: or certain words or rituals that child an adult go through may do the trick
--
reference: are your grades higher or lower than nancy's
predicted: are your grades higher or lower than nancies
--
```

## Fine-Tuning Script

You can find the script used to produce this model
[here](https://colab.research.google.com/drive/1gVaZhFuIXxBDN2pD0esW490azlbQtQ7C?usp=sharing).

**Note:** This model can be fine-tuned further;
[trainer_state.json](https://huggingface.co/harshit345/wav2vec2-large-lv60-timit/blob/main/trainer_state.json)
shows useful details, namely the last state (this checkpoint):

```json
{
    "epoch": 29.51,
    "eval_loss": 25.424150466918945,
    "eval_runtime": 182.9499,
    "eval_samples_per_second": 9.183,
    "eval_wer": 0.1351704233095107,
    "step": 8500
}
```
