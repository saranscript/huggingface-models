---
language:
- sk
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Slovak
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sk
    metrics:
       - name: Test WER
         type: wer
         value: 18.609
       - name: Test CER
         type: cer
         value: 5.488
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: sk
    metrics:
       - name: Test WER
         type: wer
         value: 40.548
       - name: Test CER
         type: cer
         value: 17.733
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M - Slovak

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SK dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3067
- Wer: 0.2678

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1500
- num_epochs: 60.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.175         | 2.41  | 400  | 4.6909          | 1.0    |
| 3.3785        | 4.82  | 800  | 3.3080          | 1.0    |
| 2.6964        | 7.23  | 1200 | 2.0651          | 1.1055 |
| 1.3008        | 9.64  | 1600 | 0.5845          | 0.6207 |
| 1.1185        | 12.05 | 2000 | 0.4195          | 0.4193 |
| 1.0252        | 14.46 | 2400 | 0.3824          | 0.3570 |
| 0.935         | 16.87 | 2800 | 0.3693          | 0.3462 |
| 0.8818        | 19.28 | 3200 | 0.3587          | 0.3318 |
| 0.8534        | 21.69 | 3600 | 0.3420          | 0.3180 |
| 0.8137        | 24.1  | 4000 | 0.3426          | 0.3130 |
| 0.7968        | 26.51 | 4400 | 0.3349          | 0.3102 |
| 0.7558        | 28.92 | 4800 | 0.3216          | 0.3019 |
| 0.7313        | 31.33 | 5200 | 0.3451          | 0.3060 |
| 0.7358        | 33.73 | 5600 | 0.3272          | 0.2967 |
| 0.718         | 36.14 | 6000 | 0.3315          | 0.2882 |
| 0.6991        | 38.55 | 6400 | 0.3299          | 0.2830 |
| 0.6529        | 40.96 | 6800 | 0.3140          | 0.2836 |
| 0.6225        | 43.37 | 7200 | 0.3128          | 0.2751 |
| 0.633         | 45.78 | 7600 | 0.3211          | 0.2774 |
| 0.5876        | 48.19 | 8000 | 0.3162          | 0.2764 |
| 0.588         | 50.6  | 8400 | 0.3082          | 0.2722 |
| 0.5915        | 53.01 | 8800 | 0.3120          | 0.2681 |
| 0.5798        | 55.42 | 9200 | 0.3133          | 0.2709 |
| 0.5736        | 57.83 | 9600 | 0.3086          | 0.2676 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-300m-sk-cv8-with-lm --dataset mozilla-foundation/common_voice_8_0 --config sk --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-300m-sk-cv8-with-lm --dataset speech-recognition-community-v2/dev_data --config sk --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-xls-r-300m-sk-cv8-with-lm"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "sk", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => ""
```

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 26.707 | 18.609 |