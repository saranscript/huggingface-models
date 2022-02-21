---
---
language: 
- ur
license: apache-2.0
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
metrics:
- wer
model-index:
- name: wav2vec2-large-xls-r-300m-Urdu
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice 8
      args: ur
    metrics:
      - type: wer    # Required. Example: wer
        value: 39.89  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
      - name: Test CER
        type: cer
        value: 16.70
---
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-Urdu

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9889
- Wer: 0.5607
- Cer: 0.2370
#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id kingabzpro/wav2vec2-large-xls-r-300m-Urdu --dataset mozilla-foundation/common_voice_8_0 --config ur --split test
```


### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "kingabzpro/wav2vec2-large-xls-r-300m-Urdu"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "ur", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "اب نے ٹپیدسون دیتے ہیں"
```



### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 200

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:------:|:----:|:---------------:|:------:|:------:|
| 3.6398        | 30.77  | 400  | 3.3517          | 1.0    | 1.0    |
| 2.9225        | 61.54  | 800  | 2.5123          | 1.0    | 0.8310 |
| 1.2568        | 92.31  | 1200 | 0.9699          | 0.6273 | 0.2575 |
| 0.8974        | 123.08 | 1600 | 0.9715          | 0.5888 | 0.2457 |
| 0.7151        | 153.85 | 2000 | 0.9984          | 0.5588 | 0.2353 |
| 0.6416        | 184.62 | 2400 | 0.9889          | 0.5607 | 0.2370 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 52.03 | 39.89 |
