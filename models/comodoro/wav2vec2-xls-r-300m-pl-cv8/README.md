---
language:
- pl
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- robust-speech-event
- xlsr-fine-tuning-week
datasets:
- common_voice
model-index:
- name: Polish comodoro Wav2Vec2 XLSR 300M CV8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: pl
    metrics:
       - name: Test WER
         type: wer
         value: 17.0
       - name: Test CER
         type: cer 
         value: 3.8
---
# wav2vec2-xls-r-300m-pl-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice 8.0 dataset.
It achieves the following results on the evaluation set while training:
- Loss: 0.1716
- Wer: 0.1697
- Cer: 0.0385

The `eval.py` script results are:
WER: 0.16970531733661967
CER: 0.03839135416519316

## Model description

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Polish using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset.
When using this model, make sure that your speech input is sampled at 16kHz.


The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("mozilla-foundation/common_voice_8_0", "pl", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("comodoro/wav2vec2-xls-r-300m-pl-cv8")
model = Wav2Vec2ForCTC.from_pretrained("comodoro/wav2vec2-xls-r-300m-pl-cv8")

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
python eval.py --model_id comodoro/wav2vec2-xls-r-300m-pl-cv8 --dataset mozilla-foundation/common-voice_8_0 --split test --config pl
```

## Training and evaluation data

The Common Voice 8.0 `train` and `validation` datasets were used for training

## Training procedure

### Training hyperparameters

The following hyperparameters were used:

- learning_rate: 1e-4
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 1
- total_train_batch_size: 640
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 150
- mixed_precision_training: Native AMP

The training was interrupted after 3250 steps.

### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
