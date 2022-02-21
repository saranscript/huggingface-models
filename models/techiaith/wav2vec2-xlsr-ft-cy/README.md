---
language: cy
datasets:
- common_voice 
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- ken-lm
- robust-speech-event
license: apache-2.0
model-index:
- name: wav2vec2-xlsr-ft-cy with KenLM language model (by Bangor University)
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice cy
      type: common_voice
      args: cy
    metrics:
       - name: Test WER
         type: wer
         value: 13.79%
---

# wav2vec2-xlsr-ft-cy

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the [Welsh Common Voice version 8 dataset](https://huggingface.co/datasets/common_voice).

Source code and scripts for training acoustic and KenLM language models, as well as examples of inference in transcribing or a self-hosted API service, can be found at [https://github.com/techiaith/docker-wav2vec2-xlsr-ft-cy](https://github.com/techiaith/docker-wav2vec2-xlsr-ft-cy). 



## Usage

The wav2vec2-xlsr-ft-cy (acoustic) model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
import librosa

from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

processor = Wav2Vec2Processor.from_pretrained("techiaith/wav2vec2-xlsr-ft-cy")
model = Wav2Vec2ForCTC.from_pretrained("techiaith/wav2vec2-xlsr-ft-cy")

audio, rate = librosa.load(audio_file, sr=16000)

inputs = processor(audio, sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
  tlogits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

# greedy decoding
predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))

```

## Using the Language Model

See https://github.com/techiaith/docker-wav2vec2-xlsr-ft-cy/releases/tag/21.08 for more details and
examples of a KenLM usage with the Parlance PyTorch CTC decode bindings library: [https://github.com/parlance/ctcdecode](https://github.com/parlance/ctcdecode)


## Evaluation

According to the Welsh Common Voice version 8 test set, the WER of techiaith/wav2vec2-xlsr-ft-cy standalone is **24.03%**

When assisted by the KenLM language model the same test produces a WER of **13.79%**

See: https://github.com/techiaith/docker-wav2vec2-xlsr-ft-cy/blob/main/train/python/evaluate.py


