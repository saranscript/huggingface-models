---
language:
- sk
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- robust-speech-event
- xlsr-fine-tuning-week
datasets:
- common_voice
model-index:
- name: Slovak comodoro Wav2Vec2 XLSR 300M CV8
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
         value: 49.6
       - name: Test CER
         type: cer 
         value: 13.3
---

# wav2vec2-xls-r-300m-cs-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice 8.0 dataset.
It achieves the following results on the evaluation set:

- WER: 0.49575384615384616
- CER: 0.13333333333333333

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("mozilla-foundation/common_voice_8_0", "sk", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("comodoro/wav2vec2-xls-r-300m-sk-cv8")
model = Wav2Vec2ForCTC.from_pretrained("comodoro/wav2vec2-xls-r-300m-sk-cv8")

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
python eval.py --model_id comodoro/wav2vec2-xls-r-300m-sk-cv8 --dataset mozilla-foundation/common_voice_8_0 --split test --config sk
```

## Training and evaluation data

The Common Voice 8.0 `train` and `validation` datasets were used for training

### Training hyperparameters

The following hyperparameters were used during training:

- learning_rate: 7e-4
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

### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
