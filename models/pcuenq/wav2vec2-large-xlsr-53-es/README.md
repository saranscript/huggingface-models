---
language: es
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
- name: XLSR Wav2Vec2 Large 53 Spanish by pcuenq 
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice es
      type: common_voice
      args: es
    metrics:
       - name: Test WER
         type: wer
         value: 10.50
---

# Wav2Vec2-Large-XLSR-53-Spanish

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Spanish using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset{s}.
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "es", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("pcuenq/wav2vec2-large-xlsr-53-es")
model = Wav2Vec2ForCTC.from_pretrained("pcuenq/wav2vec2-large-xlsr-53-es")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
	speech_array, sampling_rate = torchaudio.load(batch["path"])
	batch["speech"] = resampler(speech_array).squeeze().numpy()
	return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
	logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```


## Evaluation

The model can be evaluated as follows on the Spanish test data of Common Voice.

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "es", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("pcuenq/wav2vec2-large-xlsr-53-es")
model = Wav2Vec2ForCTC.from_pretrained("pcuenq/wav2vec2-large-xlsr-53-es")
model.to("cuda")

## Text pre-processing

chars_to_ignore_regex = '[\,\¿\?\.\¡\!\-\;\:\"\“\%\‘\”\￼\…\’\ː\'\‹\›\`\´\®\—\→]'
chars_to_ignore_pattern = re.compile(chars_to_ignore_regex)

def remove_special_characters(batch):
    batch["sentence"] = chars_to_ignore_pattern.sub('', batch["sentence"]).lower() + " "
    return batch

def replace_diacritics(batch):
    sentence = batch["sentence"]
    sentence = re.sub('ì', 'í', sentence)
    sentence = re.sub('ù', 'ú', sentence)
    sentence = re.sub('ò', 'ó', sentence)
    sentence = re.sub('à', 'á', sentence)
    batch["sentence"] = sentence
    return batch

def replace_additional(batch):
    sentence = batch["sentence"]
    sentence = re.sub('ã', 'a', sentence)   # Portuguese, as in São Paulo
    sentence = re.sub('ō', 'o', sentence)   # Japanese
    sentence = re.sub('ê', 'e', sentence)   # Português
    batch["sentence"] = sentence
    return batch

## Audio pre-processing

# I tried to perform the resampling using a `torchaudio` `Resampler` transform,
# but found that the process deadlocked when using multiple processes.
# Perhaps my torchaudio is using the wrong sox library under the hood, I'm not sure.
# Fortunately, `librosa` seems to work fine, so that's what I'll use for now.

import librosa
def speech_file_to_array_fn(batch):
    speech_array, sample_rate = torchaudio.load(batch["path"])
    batch["speech"] = librosa.resample(speech_array.squeeze().numpy(), sample_rate, 16_000)
    return batch

# One-pass mapping function

# Text transformation and audio resampling
def cv_prepare(batch):
    batch = remove_special_characters(batch)
    batch = replace_diacritics(batch)
    batch = replace_additional(batch)
    batch = speech_file_to_array_fn(batch)
    return batch

# Number of CPUs or None
num_proc = 16

test_dataset = test_dataset.map(cv_prepare, remove_columns=['path'], num_proc=num_proc)

def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

# WER Metric computation
# `wer.compute` crashes in my computer with more than ~10000 samples.
# Until I confirm in a different one, I created a "chunked" version of the computation.
# It gives the same results as `wer.compute` for smaller datasets.

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

print("WER: {:2f}".format(100 * chunked_wer(result["sentence"], result["pred_strings"], chunk_size=4000)))
#print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))

```

**Test Result**: 10.50 %

## Text processing

The Common Voice `es` dataset has a lot of characters that don't belong to the Spanish language, even after discarding separators and punctuators. I made some translations and discarded most of the extraneous characters.

I decided to keep all the Spanish language diacritics. This is a difficult decision. Some times the diacritics are added just because of ortography rules, but they don't alter the meaning of the word. In other cases, however, the diacritics carry meaning, as they disambiguate among different senses. A better WER score would surely have been achieved using just the non-accented characters, and the resulting text would be understood by Spanish speakers. Nevertheless, I think keeping them is "more correct".

All the rules I applied are shown in the evaluation script.

## Training

The Common Voice `train` and `validation` datasets were used for training.

For dataset handling reasons, I initially split `train`+`validation` in 10% splits so I could see progress earlier and react if needed.

* I trained for 30 epochs on the first split only, using similar values as the ones proposed by Patrick in his demo notebook. I used a batch_size of 24 with 2 gradient accumulation steps. This gave a WER of about 16.3%on the full test set.
* I then trained the resulting model on the 9 remaining splits, for 3 epochs each, but with a faster warmup of 75 steps.
* Next, I trained 3 epochs on each of the 10 splits using a smaller learning rate of `1e-4`. A warmup of 75 steps was used in this case too. The final model had a WER of about 11.7%.
* By this time we had already figured out the reason for the initial delay in training time, and I decided to use the full dataset for training. However, in my tests I had seen that varying the learning rate seemed to work well, so I wanted to replicate that. I selected a cosine schedule with hard restarts, a reference learning rate of `3e-5` and 10 epochs. I configured the cosine schedule to have 10 cycles too, and used no warmup. This produced a WER of ~10.5%.


## Other things I tried

* Starting from the same fine-tuned model, I compared a constant lr of 1e-4 against a linear schedule with warmup. The linear schedule worked better (11.85 vs 12.72 WER%).
* I tried to use a Spanish model to improve a Basque one. I transformed the text to make ortography more similar to the target language, but the Basque model did not improve.
* Label smoothing did not work.

## Issues and other technical challenges

I had previously used the `transformers` library as an end user, just to try Bert on some tasks, but this is the first time I have needed to look into the code.

* The `Datasets` abstraction is great because, being based on memory-mapped files, it allows arbitrarily-sized datasets to be processed. However, it is important to understand its limitations and trade-offs. I found caching convenient, but disk usage explodes fast. I keep the datasets for my current projects in a 1 TB, fast SSD disk, and a couple of times I ran out of space. I had to understand how cache files are stored and learn when it's best to disable caching and manually save when you need to. I found that data exploration is better suited for smaller datasets or sampled ones, but actual processing is most efficient when you have identified the transformations you need and apply them in a single `map` operation.

* There was a noticeable delay before training started. Fortunately, we found the reason why, discussed it in Slack and the forums and created a workaround.

* The WER metric crashed on large datasets. I evaluated on a small sample (also, it's faster) and wrote an accumulative version of wer that runs on fixed memory. I'd like to verify whether this change makes sense to be used inside the training loop.

* `torchaudio` deadlocks when using multiple processes. `librosa` works fine. To be investigated.

* When using `num_proc` inside a notebook, I could not see progress bars. This is surely some permissions issue in my computer. I still need to find it out.

