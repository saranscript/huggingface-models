---
language: fr
datasets:
- common_voice
metrics:
- wer
- cer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: Voxpopuli Wav2Vec2 French by Jonatas Grosman
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice fr
      type: common_voice
      args: fr
    metrics:
       - name: Test WER
         type: wer
         value: 17.62
       - name: Test CER
         type: cer
         value: 6.04
---

# Wav2vec2-Large-FR-Voxpopuli-French

Fine-tuned [facebook/wav2vec2-large-fr-voxpopuli](https://huggingface.co/facebook/wav2vec2-large-fr-voxpopuli) on French using the [Common Voice](https://huggingface.co/datasets/common_voice).
When using this model, make sure that your speech input is sampled at 16kHz.

This model has been fine-tuned thanks to the GPU credits generously given by the [OVHcloud](https://www.ovhcloud.com/en/public-cloud/ai-training/) :)

The script used for training can be found here: https://github.com/jonatasgrosman/wav2vec2-sprint

## Usage

The model can be used directly (without a language model) as follows...

Using the [ASRecognition](https://github.com/jonatasgrosman/asrecognition) library:

```python
from asrecognition import ASREngine

asr = ASREngine("fr", model_path="jonatasgrosman/wav2vec2-large-fr-voxpopuli-french")

audio_paths = ["/path/to/file.mp3", "/path/to/another_file.wav"]
transcriptions = asr.transcribe(audio_paths)
```

Writing your own inference script:

```python
import torch
import librosa
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

LANG_ID = "fr"
MODEL_ID = "jonatasgrosman/wav2vec2-large-fr-voxpopuli-french"
SAMPLES = 10

test_dataset = load_dataset("common_voice", LANG_ID, split=f"test[:{SAMPLES}]")

processor = Wav2Vec2Processor.from_pretrained(MODEL_ID)
model = Wav2Vec2ForCTC.from_pretrained(MODEL_ID)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = librosa.load(batch["path"], sr=16_000)
    batch["speech"] = speech_array
    batch["sentence"] = batch["sentence"].upper()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)
predicted_sentences = processor.batch_decode(predicted_ids)

for i, predicted_sentence in enumerate(predicted_sentences):
    print("-" * 100)
    print("Reference:", test_dataset[i]["sentence"])
    print("Prediction:", predicted_sentence)
```

| Reference  | Prediction |
| ------------- | ------------- |
| "CE DERNIER A ÉVOLUÉ TOUT AU LONG DE L'HISTOIRE ROMAINE." | CE DERNIER A ÉVOLÉ TOUT AU LONG DE L'HISTOIRE ROMAINE |
| CE SITE CONTIENT QUATRE TOMBEAUX DE LA DYNASTIE ACHÉMÉNIDE ET SEPT DES SASSANIDES. | CE SITE CONTIENT QUATRE TOMBEAUX DE LA DYNESTIE ACHÉMÉNIDE ET SEPT DES SACENNIDES |
| "J'AI DIT QUE LES ACTEURS DE BOIS AVAIENT, SELON MOI, BEAUCOUP D'AVANTAGES SUR LES AUTRES." | JAI DIT QUE LES ACTEURS DE BOIS AVAIENT SELON MOI BEAUCOUP DAVANTAGE SUR LES AUTRES |
| LES PAYS-BAS ONT REMPORTÉ TOUTES LES ÉDITIONS. | LE PAYS-BAS ON REMPORTÉ TOUTES LES ÉDITIONS |
| IL Y A MAINTENANT UNE GARE ROUTIÈRE. | IL A MAINTENANT GULA E RETIREN |
| HUIT | HUIT |
| DANS L’ATTENTE DU LENDEMAIN, ILS NE POUVAIENT SE DÉFENDRE D’UNE VIVE ÉMOTION | DANS LATTENTE DU LENDEMAIN IL NE POUVAIT SE DÉFENDRE DUNE VIVE ÉMOTION |
| LA PREMIÈRE SAISON EST COMPOSÉE DE DOUZE ÉPISODES. | LA PREMIÈRE SAISON EST COMPOSÉE DE DOUZ ÉPISODES |
| ELLE SE TROUVE ÉGALEMENT DANS LES ÎLES BRITANNIQUES. | ELLE SE TROUVE ÉGALEMENT DANS LES ÎLES BRITANNIQUES |
| ZÉRO | ZÉRO |

## Evaluation

The model can be evaluated as follows on the French (fr) test data of Common Voice.

```python
import torch
import re
import librosa
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

LANG_ID = "fr"
MODEL_ID = "jonatasgrosman/wav2vec2-large-fr-voxpopuli-french"
DEVICE = "cuda"

CHARS_TO_IGNORE = [",", "?", "¿", ".", "!", "¡", ";", "；", ":", '""', "%", '"', "�", "ʿ", "·", "჻", "~", "՞",
                   "؟", "،", "।", "॥", "«", "»", "„", "“", "”", "「", "」", "‘", "’", "《", "》", "(", ")", "[", "]",
                   "{", "}", "=", "`", "_", "+", "<", ">", "…", "–", "°", "´", "ʾ", "‹", "›", "©", "®", "—", "→", "。",
                   "、", "﹂", "﹁", "‧", "～", "﹏", "，", "｛", "｝", "（", "）", "［", "］", "【", "】", "‥", "〽",
                   "『", "』", "〝", "〟", "⟨", "⟩", "〜", "：", "！", "？", "♪", "؛", "/", "\\", "º", "−", "^", "ʻ", "ˆ"]

test_dataset = load_dataset("common_voice", LANG_ID, split="test")

wer = load_metric("wer.py") # https://github.com/jonatasgrosman/wav2vec2-sprint/blob/main/wer.py
cer = load_metric("cer.py") # https://github.com/jonatasgrosman/wav2vec2-sprint/blob/main/cer.py

chars_to_ignore_regex = f"[{re.escape(''.join(CHARS_TO_IGNORE))}]"

processor = Wav2Vec2Processor.from_pretrained(MODEL_ID)
model = Wav2Vec2ForCTC.from_pretrained(MODEL_ID)
model.to(DEVICE)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    with warnings.catch_warnings():
        warnings.simplefilter("ignore")
        speech_array, sampling_rate = librosa.load(batch["path"], sr=16_000)
    batch["speech"] = speech_array
    batch["sentence"] = re.sub(chars_to_ignore_regex, "", batch["sentence"]).upper()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to(DEVICE), attention_mask=inputs.attention_mask.to(DEVICE)).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

predictions = [x.upper() for x in result["pred_strings"]]
references = [x.upper() for x in result["sentence"]]

print(f"WER: {wer.compute(predictions=predictions, references=references, chunk_size=1000) * 100}")
print(f"CER: {cer.compute(predictions=predictions, references=references, chunk_size=1000) * 100}")
```

**Test Result**:

In the table below I report the Word Error Rate (WER) and the Character Error Rate (CER) of the model. I ran the evaluation script described above on other models as well (on 2021-05-16). Note that the table below may show different results from those already reported, this may have been caused due to some specificity of the other evaluation scripts used.

| Model | WER | CER |
| ------------- | ------------- | ------------- |
| jonatasgrosman/wav2vec2-large-xlsr-53-french | **15.90%** | **5.29%** |
| jonatasgrosman/wav2vec2-large-fr-voxpopuli-french | 17.62% | 6.04% |
| Ilyes/wav2vec2-large-xlsr-53-french | 19.67% | 6.70% |
| Nhut/wav2vec2-large-xlsr-french | 24.09% | 8.42% |
| facebook/wav2vec2-large-xlsr-53-french | 25.45% | 10.35% |
| MehdiHosseiniMoghadam/wav2vec2-large-xlsr-53-French | 28.22% | 9.70% |
| Ilyes/wav2vec2-large-xlsr-53-french_punctuation | 29.80% | 11.79% |
| facebook/wav2vec2-base-10k-voxpopuli-ft-fr | 61.06% | 33.31% |

## Citation
If you want to cite this model you can use this:

```bibtex
@misc{grosman2021wav2vec2-large-fr-voxpopuli-french,
  title={Wav2Vec2 French by Jonatas Grosman},
  author={Grosman, Jonatas},
  publisher={Hugging Face},
  journal={Hugging Face Hub},
  howpublished={\url{https://huggingface.co/jonatasgrosman/wav2vec2-large-fr-voxpopuli-french}},
  year={2021}
}
```
