---
license: apache-2.0
language:
- es
tags:
- generated_from_trainer
- robust-speech-event
- common_voice_8_0
- mozilla-foundation/common_voice_8_0

datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wave2vec-xls-r-300m-es
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: mozilla-foundation/common_voice_8_0 es
      type: mozilla-foundation/common_voice_8_0
      args: es
    metrics:
       - name: Test WER
         type: wer
         value: 14.6
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Wav2Vec2-XLSR-300m-es  

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the spanish common_voice dataset thanks to the GPU credits generously given by the OVHcloud for the Speech Recognition challenge.
It achieves the following results on the evaluation set (without LM):
- Loss : 0.1900
- Wer : 0.146

### Usage with 5-gram.

The model can be used with n-gram (n=5) included in the processor as follows.

```python
import re
from transformers import AutoModelForCTC,Wav2Vec2ProcessorWithLM
import torch

# Loading model and processor
processor = Wav2Vec2ProcessorWithLM.from_pretrained("polodealvarado/xls-r-300m-es")
model = AutoModelForCTC.from_pretrained("polodealvarado/xls-r-300m-es")

# Cleaning characters
def remove_extra_chars(batch):
    chars_to_ignore_regex = '[^a-záéíóúñ ]'
    text = batch["translation"][target_lang]
    batch["text"] = re.sub(chars_to_ignore_regex, "", text.lower())
    return batch
    
# Preparing dataset
def prepare_dataset(batch):
    audio = batch["audio"]
    batch["input_values"] = processor(audio["array"], sampling_rate=audio["sampling_rate"],return_tensors="pt",padding=True).input_values[0]    
    with processor.as_target_processor():
        batch["labels"] = processor(batch["sentence"]).input_ids
    return batch
  

common_voice_test = load_dataset("mozilla-foundation/common_voice_8_0", "es", split="test",use_auth_token=True)
common_voice_test = common_voice_test.remove_columns(["accent", "age", "client_id", "down_votes", "gender", "locale", "segment", "up_votes"])
common_voice_test = common_voice_test.cast_column("audio", Audio(sampling_rate=16_000))        
common_voice_test = common_voice_test.map(remove_extra_chars, remove_columns=dataset.column_names)
common_voice_test = common_voice_test.map(prepare_dataset)

# Testing first sample
inputs = torch_tensor(common_voice_test[0]["input_values"])

with torch.no_grad():
    logits = model(inputs).logits

pred_ids = torch.argmax(logits, dim=-1)
text = processor.batch_decode(logits.numpy()).text
print(text) # 'bien y qué regalo vas a abrir primero'

```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 4
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.6747        | 0.3   | 400  | 0.6535          | 0.5926 |
| 0.4439        | 0.6   | 800  | 0.3753          | 0.3193 |
| 0.3291        | 0.9   | 1200 | 0.3267          | 0.2721 |
| 0.2644        | 1.2   | 1600 | 0.2816          | 0.2311 |
| 0.24          | 1.5   | 2000 | 0.2647          | 0.2179 |
| 0.2265        | 1.79  | 2400 | 0.2406          | 0.2048 |
| 0.1994        | 2.09  | 2800 | 0.2357          | 0.1869 |
| 0.1613        | 2.39  | 3200 | 0.2242          | 0.1821 |
| 0.1546        | 2.69  | 3600 | 0.2123          | 0.1707 |
| 0.1441        | 2.99  | 4000 | 0.2067          | 0.1619 |
| 0.1138        | 3.29  | 4400 | 0.2044          | 0.1519 |
| 0.1072        | 3.59  | 4800 | 0.1917          | 0.1457 |
| 0.0992        | 3.89  | 5200 | 0.1900          | 0.1438 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
