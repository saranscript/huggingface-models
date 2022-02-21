---
language: de
datasets:
- common_voice
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: {XLSR Wav2Vec2 Large 53 CV-de}
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice de
      type: common_voice
      args: de
    metrics:
       - name: Test WER
         type: wer
         value: 12.77
---

# Wav2Vec2-Large-XLSR-53-German

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on German using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset.
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "de", split="test[:8]") # use a batch of 8 for demo purposes

processor = Wav2Vec2Processor.from_pretrained("maxidl/wav2vec2-large-xlsr-german")
model = Wav2Vec2ForCTC.from_pretrained("maxidl/wav2vec2-large-xlsr-german") 

resampler = torchaudio.transforms.Resample(48_000, 16_000)

"""
Preprocessing the dataset by:
- loading audio files
- resampling to 16kHz
- converting to array
- prepare input tensor using the processor
"""
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

# run forward
with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"])
"""
Example Result:

Prediction: [
    'zieh durch bittet draußen die schuhe aus',
    'es kommt zugvorgebauten fo',
    'ihre vorterstrecken erschienen it modemagazinen wie der voge karpes basar mariclair',
    'fürliepert eine auch für manachen ungewöhnlich lange drittelliste',
    'er wurde zu ehren des reichskanzlers otto von bismarck errichtet',
    'was solls ich bin bereit',
    'das internet besteht aus vielen computern die miteinander verbunden sind',
    'der uranus ist der siebinteplanet in unserem sonnensystem s'
]

Reference: [
    'Zieht euch bitte draußen die Schuhe aus.',
    'Es kommt zum Showdown in Gstaad.',
    'Ihre Fotostrecken erschienen in Modemagazinen wie der Vogue, Harper’s Bazaar und Marie Claire.',
    'Felipe hat eine auch für Monarchen ungewöhnlich lange Titelliste.',
    'Er wurde zu Ehren des Reichskanzlers Otto von Bismarck errichtet.',
    'Was solls, ich bin bereit.',
    'Das Internet besteht aus vielen Computern, die miteinander verbunden sind.',
    'Der Uranus ist der siebente Planet in unserem Sonnensystem.'
]
"""
```


## Evaluation

The model can be evaluated as follows on the German test data of Common Voice:


```python
import re
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

"""
Evaluation on the full test set:
- takes ~20mins (RTX 3090).
- requires ~170GB RAM to compute the WER. Below, we use a chunked implementation of WER to avoid large RAM consumption.
"""
test_dataset = load_dataset("common_voice", "de", split="test") # use "test[:1%]" for 1% sample
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("maxidl/wav2vec2-large-xlsr-german")
model = Wav2Vec2ForCTC.from_pretrained("maxidl/wav2vec2-large-xlsr-german")
model.to("cuda")

chars_to_ignore_regex = '[\\,\\?\\.\\!\\-\\;\\:\\"\\“]'
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
\tbatch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
\tspeech_array, sampling_rate = torchaudio.load(batch["path"])
\tbatch["speech"] = resampler(speech_array).squeeze().numpy()
\treturn batch

test_dataset = test_dataset.map(speech_file_to_array_fn)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def evaluate(batch):
\tinputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

\twith torch.no_grad():
\t\tlogits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

\tpred_ids = torch.argmax(logits, dim=-1)
\tbatch["pred_strings"] = processor.batch_decode(pred_ids)
\treturn batch

result = test_dataset.map(evaluate, batched=True, batch_size=8) # batch_size=8 -> requires ~14.5GB GPU memory

# non-chunked version:
# print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
# WER: 12.900291 

# Chunked version, see https://discuss.huggingface.co/t/spanish-asr-fine-tuning-wav2vec2/4586/5:
import jiwer

def chunked_wer(targets, predictions, chunk_size=None):
    if chunk_size is None: return jiwer.wer(targets, predictions)
    start = 0
    end = chunk_size
    H, S, D, I = 0, 0, 0, 0
    while start < len(targets):
        chunk_metrics = jiwer.compute_measures(targets[start:end], predictions[start:end])
        H = H + chunk_metrics["hits"]
        S = S + chunk_metrics["substitutions"]
        D = D + chunk_metrics["deletions"]
        I = I + chunk_metrics["insertions"]
        start += chunk_size
        end += chunk_size
    return float(S + D + I) / float(H + S + D)

print("Total (chunk_size=1000), WER: {:2f}".format(100 * chunked_wer(result["pred_strings"], result["sentence"], chunk_size=1000)))
# Total (chunk=1000), WER: 12.768981
```

**Test Result**: WER: 12.77 %


## Training

The Common Voice German `train` and `validation` were used for training.
The script used for training can be found [here](https://github.com/maxidl/wav2vec2).
The model was trained for 50k steps, taking around 30 hours on a single A100.

The arguments used for training this model are:
```
python run_finetuning.py \\
--model_name_or_path="facebook/wav2vec2-large-xlsr-53" \\
--dataset_config_name="de" \\
--output_dir=./wav2vec2-large-xlsr-german \\
--preprocessing_num_workers="16" \\
--overwrite_output_dir \\
--num_train_epochs="20" \\
--per_device_train_batch_size="64" \\
--per_device_eval_batch_size="32" \\
--learning_rate="1e-4" \\
--warmup_steps="500" \\
--evaluation_strategy="steps" \\
--save_steps="5000" \\
--eval_steps="5000" \\
--logging_steps="1000" \\
--save_total_limit="3" \\
--freeze_feature_extractor \\
--activation_dropout="0.055" \\
--attention_dropout="0.094" \\
--feat_proj_dropout="0.04" \\
--layerdrop="0.04" \\
--mask_time_prob="0.08" \\
--gradient_checkpointing="1" \\
--fp16 \\
--do_train \\
--do_eval \\
--dataloader_num_workers="16" \\
--group_by_length
```
