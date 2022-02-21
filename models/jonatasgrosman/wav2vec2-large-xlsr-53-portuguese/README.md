---
language: pt
license: apache-2.0
datasets:
- common_voice
- mozilla-foundation/common_voice_6_0
metrics:
- wer
- cer
tags:
- pt
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
- robust-speech-event
- mozilla-foundation/common_voice_6_0
model-index:
- name: XLSR Wav2Vec2 Portuguese by Jonatas Grosman
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice pt
      type: common_voice
      args: pt
    metrics:
       - name: Test WER
         type: wer
         value: 11.31
       - name: Test CER
         type: cer
         value: 3.74
       - name: Test WER (+LM)
         type: wer
         value: 9.01
       - name: Test CER (+LM)
         type: cer
         value: 3.21
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: pt
    metrics:
       - name: Dev WER
         type: wer
         value: 42.10
       - name: Dev CER
         type: cer
         value: 17.93
       - name: Dev WER (+LM)
         type: wer
         value: 36.92
       - name: Dev CER (+LM)
         type: cer
         value: 16.88
---

# Wav2Vec2-Large-XLSR-53-Portuguese

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Portuguese using the [Common Voice](https://huggingface.co/datasets/common_voice).
When using this model, make sure that your speech input is sampled at 16kHz.

This model has been fine-tuned thanks to the GPU credits generously given by the [OVHcloud](https://www.ovhcloud.com/en/public-cloud/ai-training/) :)

The script used for training can be found here: https://github.com/jonatasgrosman/wav2vec2-sprint

## Usage

The model can be used directly (without a language model) as follows...

Using the [ASRecognition](https://github.com/jonatasgrosman/asrecognition) library:

```python
from asrecognition import ASREngine

asr = ASREngine("pt", model_path="jonatasgrosman/wav2vec2-large-xlsr-53-portuguese")

audio_paths = ["/path/to/file.mp3", "/path/to/another_file.wav"]
transcriptions = asr.transcribe(audio_paths)
```

Writing your own inference script:

```python
import torch
import librosa
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

LANG_ID = "pt"
MODEL_ID = "jonatasgrosman/wav2vec2-large-xlsr-53-portuguese"
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
| NEM O RADAR NEM OS OUTROS INSTRUMENTOS DETECTARAM O BOMBARDEIRO STEALTH. | NEMHUM VADAN OS  OLTWES INSTRUMENTOS DE TTÉÃN UM BOMBERDEIRO OSTER |
| PEDIR DINHEIRO EMPRESTADO ÀS PESSOAS DA ALDEIA | E DIR ENGINHEIRO EMPRESTAR AS PESSOAS DA ALDEIA |
| OITO | OITO |
| TRANCÁ-LOS | TRANCAUVOS |
| REALIZAR UMA INVESTIGAÇÃO PARA RESOLVER O PROBLEMA | REALIZAR UMA INVESTIGAÇÃO PARA RESOLVER O PROBLEMA |
| O YOUTUBE AINDA É A MELHOR PLATAFORMA DE VÍDEOS. | YOUTUBE AINDA É A MELHOR PLATAFOMA DE VÍDEOS |
| MENINA E MENINO BEIJANDO NAS SOMBRAS | MENINA E MENINO BEIJANDO NAS SOMBRAS |
| EU SOU O SENHOR | EU SOU O SENHOR |
| DUAS MULHERES QUE SENTAM-SE PARA BAIXO LENDO JORNAIS. | DUAS MIERES QUE SENTAM-SE PARA BAICLANE JODNÓI |
| EU ORIGINALMENTE ESPERAVA | EU ORIGINALMENTE ESPERAVA |

## Evaluation

1. To evaluate on `mozilla-foundation/common_voice_6_0` with split `test`

```bash
python eval.py --model_id jonatasgrosman/wav2vec2-large-xlsr-53-portuguese --dataset mozilla-foundation/common_voice_6_0 --config pt --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id jonatasgrosman/wav2vec2-large-xlsr-53-portuguese --dataset speech-recognition-community-v2/dev_data --config pt --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

## Citation
If you want to cite this model you can use this:

```bibtex
@misc{grosman2021wav2vec2-large-xlsr-53-portuguese,
  title={XLSR Wav2Vec2 Portuguese by Jonatas Grosman},
  author={Grosman, Jonatas},
  publisher={Hugging Face},
  journal={Hugging Face Hub},
  howpublished={\url{https://huggingface.co/jonatasgrosman/wav2vec2-large-xlsr-53-portuguese}},
  year={2021}
}
```
