---
language:
- cs
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
- xlsr-fine-tuning-week
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: Czech comodoro Wav2Vec2 XLSR 300M CV8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: cs
    metrics:
       - name: Test WER
         type: wer
         value: 10.3
       - name: Test CER
         type: cer 
         value: 2.6
---
<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-cs-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice 8.0 dataset.
It achieves the following results on the evaluation set while training:
- Loss: 0.2327
- Wer: 0.1608
- Cer: 0.0376

The `eval.py` script results using a LM are:
WER: 0.10281503199350225
CER: 0.02622802241689026

## Model description

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Czech using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset.
When using this model, make sure that your speech input is sampled at 16kHz.


The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("mozilla-foundation/common_voice_8_0", "cs", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("comodoro/wav2vec2-xls-r-300m-cs-cv8")
model = Wav2Vec2ForCTC.from_pretrained("comodoro/wav2vec2-xls-r-300m-cs-cv8")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
	speech_array, sampling_rate = torchaudio.load(batch["path"])
	batch["speech"] = resampler(speech_array).squeeze().numpy()
	return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset[:2]["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
	logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset[:2]["sentence"])
```

## Evaluation

The model can be evaluated using the attached `eval.py` script:
```
python eval.py --model_id comodoro/wav2vec2-xls-r-300m-cs-cv8 --dataset mozilla-foundation/common-voice_8_0 --split test --config cs
```

## Training and evaluation data

The Common Voice 8.0 `train` and `validation` datasets were used for training

## Training procedure

### Training hyperparameters

The following hyperparameters were used during first stage of training:

- learning_rate: 7e-05
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 20
- total_train_batch_size: 640
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 150
- mixed_precision_training: Native AMP

The following hyperparameters were used during second stage of training:

- learning_rate: 0.001
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 20
- total_train_batch_size: 640
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:------:|:----:|:---------------:|:------:|:------:|
| 7.2926        | 8.06   | 250  | 3.8497          | 1.0    | 1.0    |
| 3.417         | 16.13  | 500  | 3.2852          | 1.0    | 0.9857 |
| 2.0264        | 24.19  | 750  | 0.7099          | 0.7342 | 0.1768 |
| 0.4018        | 32.25  | 1000 | 0.6188          | 0.6415 | 0.1551 |
| 0.2444        | 40.32  | 1250 | 0.6632          | 0.6362 | 0.1600 |
| 0.1882        | 48.38  | 1500 | 0.6070          | 0.5783 | 0.1388 |
| 0.153         | 56.44  | 1750 | 0.6425          | 0.5720 | 0.1377 |
| 0.1214        | 64.51  | 2000 | 0.6363          | 0.5546 | 0.1337 |
| 0.1011        | 72.57  | 2250 | 0.6310          | 0.5222 | 0.1224 |
| 0.0879        | 80.63  | 2500 | 0.6353          | 0.5258 | 0.1253 |
| 0.0782        | 88.7   | 2750 | 0.6078          | 0.4904 | 0.1127 |
| 0.0709        | 96.76  | 3000 | 0.6465          | 0.4960 | 0.1154 |
| 0.0661        | 104.82 | 3250 | 0.6622          | 0.4945 | 0.1166 |
| 0.0616        | 112.89 | 3500 | 0.6440          | 0.4786 | 0.1104 |
| 0.0579        | 120.95 | 3750 | 0.6815          | 0.4887 | 0.1144 |
| 0.0549        | 129.03 | 4000 | 0.6603          | 0.4780 | 0.1105 |
| 0.0527        | 137.09 | 4250 | 0.6652          | 0.4749 | 0.1090 |
| 0.0506        | 145.16 | 4500 | 0.6958          | 0.4846 | 0.1133 |

Further fine-tuning with slightly different architecture and higher learning rate:

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 0.576         | 8.06  | 250  | 0.2411          | 0.2340 | 0.0502 |
| 0.2564        | 16.13 | 500  | 0.2305          | 0.2097 | 0.0492 |
| 0.2018        | 24.19 | 750  | 0.2371          | 0.2059 | 0.0494 |
| 0.1549        | 32.25 | 1000 | 0.2298          | 0.1844 | 0.0435 |
| 0.1224        | 40.32 | 1250 | 0.2288          | 0.1725 | 0.0407 |
| 0.1004        | 48.38 | 1500 | 0.2327          | 0.1608 | 0.0376 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
