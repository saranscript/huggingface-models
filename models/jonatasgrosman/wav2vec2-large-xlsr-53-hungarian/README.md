---
language: hu
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
- name: XLSR Wav2Vec2 Hungarian by Jonatas Grosman
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice hu
      type: common_voice
      args: hu
    metrics:
       - name: Test WER
         type: wer
         value: 31.40
       - name: Test CER
         type: cer
         value: 6.20
---

# Wav2Vec2-Large-XLSR-53-Hungarian

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Hungarian using the [Common Voice](https://huggingface.co/datasets/common_voice) and [CSS10](https://github.com/Kyubyong/css10).
When using this model, make sure that your speech input is sampled at 16kHz.

This model has been fine-tuned thanks to the GPU credits generously given by the [OVHcloud](https://www.ovhcloud.com/en/public-cloud/ai-training/) :)

The script used for training can be found here: https://github.com/jonatasgrosman/wav2vec2-sprint

## Usage

The model can be used directly (without a language model) as follows...

Using the [ASRecognition](https://github.com/jonatasgrosman/asrecognition) library:

```python
from asrecognition import ASREngine

asr = ASREngine("hu", model_path="jonatasgrosman/wav2vec2-large-xlsr-53-hungarian")

audio_paths = ["/path/to/file.mp3", "/path/to/another_file.wav"]
transcriptions = asr.transcribe(audio_paths)
```

Writing your own inference script:

```python
import torch
import librosa
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

LANG_ID = "hu"
MODEL_ID = "jonatasgrosman/wav2vec2-large-xlsr-53-hungarian"
SAMPLES = 5

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
| BÜSZKÉK VAGYUNK A MAGYAR EMBEREK NAGYSZERŰ SZELLEMI ALKOTÁSAIRA. | BÜSZKÉK VAGYUNK A MAGYAR EMBEREK NAGYSZERŰ SZELLEMI ALKOTÁSAIRE |
| A NEMZETSÉG TAGJAI KÖZÜL EZT TERMESZTIK A LEGSZÉLESEBB KÖRBEN ÍZLETES TERMÉSÉÉRT. | A NEMZETSÉG TAGJAI KÖZÜL ESZSZERMESZTIK A LEGSZELESEBB KÖRBEN IZLETES TERMÉSSÉÉRT |
| A VÁROSBA VÁGYÓDOTT A LEGJOBBAN, ÉPPEN MERT ODA NEM JUTHATOTT EL SOHA. | A VÁROSBA VÁGYÓDOTT A LEGJOBBAN ÉPPEN MERT ODA NEM JUTHATOTT EL SOHA |
| SÍRJA MÁRA MEGSEMMISÜLT. | SIMGI A MANDO MEG SEMMICSEN |
| MINDEN ZENESZÁMOT DRÁGAKŐNEK NEVEZETT. | MINDEN ZENA SZÁMODRAGAKŐNEK NEVEZETT |
| ÍGY MÚLT EL A DÉLELŐTT. | ÍGY MÚLT EL A DÍN ELŐTT |
| REMEK POFA! | A REMEG PUFO |
| SZEMET SZEMÉRT, FOGAT FOGÉRT. | SZEMET SZEMÉRT FOGADD FOGÉRT |
| BIZTOSAN LAKIK ITT NÉHÁNY ATYÁMFIA. | BIZTOSAN LAKIKÉT NÉHANY ATYAMFIA |
| A SOROK KÖZÖTT OLVAS. | A SOROG KÖZÖTT OLVAS |

## Evaluation

The model can be evaluated as follows on the Hungarian test data of Common Voice.

```python
import torch
import re
import librosa
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

LANG_ID = "hu"
MODEL_ID = "jonatasgrosman/wav2vec2-large-xlsr-53-hungarian"
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

In the table below I report the Word Error Rate (WER) and the Character Error Rate (CER) of the model. I ran the evaluation script described above on other models as well (on 2021-04-22). Note that the table below may show different results from those already reported, this may have been caused due to some specificity of the other evaluation scripts used.

| Model | WER | CER |
| ------------- | ------------- | ------------- |
| jonatasgrosman/wav2vec2-large-xlsr-53-hungarian | **31.40%** | **6.20%** |
| anton-l/wav2vec2-large-xlsr-53-hungarian | 42.39% | 9.39% |
| gchhablani/wav2vec2-large-xlsr-hu | 46.42% | 10.04% |
| birgermoell/wav2vec2-large-xlsr-hungarian | 46.93% | 10.31% |

## Citation
If you want to cite this model you can use this:

```bibtex
@misc{grosman2021wav2vec2-large-xlsr-53-hungarian,
  title={XLSR Wav2Vec2 Hungarian by Jonatas Grosman},
  author={Grosman, Jonatas},
  publisher={Hugging Face},
  journal={Hugging Face Hub},
  howpublished={\url{https://huggingface.co/jonatasgrosman/wav2vec2-large-xlsr-53-hungarian}},
  year={2021}
}
```