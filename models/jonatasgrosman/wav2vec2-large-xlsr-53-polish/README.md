---
language: pl
license: apache-2.0
datasets:
- common_voice
- mozilla-foundation/common_voice_6_0
metrics:
- wer
- cer
tags:
- pl
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
- robust-speech-event
- mozilla-foundation/common_voice_6_0
model-index:
- name: XLSR Wav2Vec2 Polish by Jonatas Grosman
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice pl
      type: common_voice
      args: pl
    metrics:
       - name: Test WER
         type: wer
         value: 14.21
       - name: Test CER
         type: cer
         value: 3.49
       - name: Test WER (+LM)
         type: wer
         value: 10.98
       - name: Test CER (+LM)
         type: cer
         value: 2.93
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: pl
    metrics:
       - name: Dev WER
         type: wer
         value: 33.18
       - name: Dev CER
         type: cer
         value: 15.92
       - name: Dev WER (+LM)
         type: wer
         value: 29.31
       - name: Dev CER (+LM)
         type: cer
         value: 15.17
---

# Wav2Vec2-Large-XLSR-53-Polish

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Polish using the [Common Voice](https://huggingface.co/datasets/common_voice).
When using this model, make sure that your speech input is sampled at 16kHz.

This model has been fine-tuned thanks to the GPU credits generously given by the [OVHcloud](https://www.ovhcloud.com/en/public-cloud/ai-training/) :)

The script used for training can be found here: https://github.com/jonatasgrosman/wav2vec2-sprint

## Usage

The model can be used directly (without a language model) as follows...

Using the [ASRecognition](https://github.com/jonatasgrosman/asrecognition) library:

```python
from asrecognition import ASREngine

asr = ASREngine("pl", model_path="jonatasgrosman/wav2vec2-large-xlsr-53-polish")

audio_paths = ["/path/to/file.mp3", "/path/to/another_file.wav"]
transcriptions = asr.transcribe(audio_paths)
```

Writing your own inference script:

```python
import torch
import librosa
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

LANG_ID = "pl"
MODEL_ID = "jonatasgrosman/wav2vec2-large-xlsr-53-polish"
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
| """CZY DRZWI BYŁY ZAMKNIĘTE?""" | PRZY DRZWI BYŁY ZAMKNIĘTE |
| GDZIEŻ TU POWÓD DO WYRZUTÓW? | WGDZIEŻ TO POM DO WYRYDÓ |
| """O TEM JEDNAK NIE BYŁO MOWY.""" | O TEM JEDNAK NIE BYŁO MOWY |
| LUBIĘ GO. | LUBIĄ GO |
| — TO MI NIE POMAGA. | TO MNIE NIE POMAGA |
| WCIĄŻ LUDZIE WYSIADAJĄ PRZED ZAMKIEM, Z MIASTA, Z PRAGI. | WCIĄŻ LUDZIE WYSIADAJĄ PRZED ZAMKIEM Z MIASTA Z PRAGI |
| ALE ON WCALE INACZEJ NIE MYŚLAŁ. | ONY MONITCENIE PONACZUŁA NA MASU |
| A WY, CO TAK STOICIE? | A WY CO TAK STOICIE |
| A TEN PRZYRZĄD DO CZEGO SŁUŻY? | A TEN PRZYRZĄD DO CZEGO SŁUŻY |
| NA JUTRZEJSZYM KOLOKWIUM BĘDZIE PIĘĆ PYTAŃ OTWARTYCH I TEST WIELOKROTNEGO WYBORU. | NAJUTRZEJSZYM KOLOKWIUM BĘDZIE PIĘĆ PYTAŃ OTWARTYCH I TEST WIELOKROTNEGO WYBORU |

## Evaluation

1. To evaluate on `mozilla-foundation/common_voice_6_0` with split `test`

```bash
python eval.py --model_id jonatasgrosman/wav2vec2-large-xlsr-53-polish --dataset mozilla-foundation/common_voice_6_0 --config pl --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id jonatasgrosman/wav2vec2-large-xlsr-53-polish --dataset speech-recognition-community-v2/dev_data --config pl --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

## Citation
If you want to cite this model you can use this:

```bibtex
@misc{grosman2021wav2vec2-large-xlsr-53-polish,
  title={XLSR Wav2Vec2 Polish by Jonatas Grosman},
  author={Grosman, Jonatas},
  publisher={Hugging Face},
  journal={Hugging Face Hub},
  howpublished={\url{https://huggingface.co/jonatasgrosman/wav2vec2-large-xlsr-53-polish}},
  year={2021}
}
```