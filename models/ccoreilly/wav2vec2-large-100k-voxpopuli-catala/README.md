---
language: ca
datasets:
- common_voice 
- parlament_parla
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- speech-to-text
license: apache-2.0
model-index:
- name: Catalan VoxPopuli Wav2Vec2 Large
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    datasets:
      - name: Common Voice ca
        type: common_voice
        args: ca
      - name: ParlamentParla
        url: https://www.openslr.org/59/
    metrics:
       - name: Test WER
         type: wer
         value: 5.98
       - name: Google Crowsourced Corpus WER
         type: wer
         value: 12.14
       - name: Audiobook “La llegenda de Sant Jordi” WER
         type: wer
         value: 12.02
---

# Wav2Vec2-Large-100k-VoxPopuli-Català

**⚠️NOTICE⚠️: THIS MODEL HAS BEEN MOVED TO THE FOLLOWING URL:** 
https://huggingface.co/softcatala/wav2vec2-large-100k-voxpopuli-catala

Fine-tuned [facebook/wav2vec2-large-100k-voxpopuli](https://huggingface.co/facebook/wav2vec2-large-100k-voxpopuli) on Catalan language using the [Common Voice](https://huggingface.co/datasets/common_voice) and [ParlamentParla](https://www.openslr.org/59/) datasets.

**Attention:** The split train/dev/test used does not fully map with the CommonVoice 6.1 dataset. A custom split was used combining both the CommonVoice and ParlamentParla dataset and can be found [here](https://github.com/ccoreilly/wav2vec2-catala). Evaluating on the CV test dataset will produce a biased WER as 1144 audio files of that dataset were used in training/evaluation of this model.
WER was calculated using this [test.csv](https://github.com/ccoreilly/wav2vec2-catala/blob/master/test-filtered.csv) which was not seen by the model during training/evaluation.

You can find training and evaluation scripts in the github repository [ccoreilly/wav2vec2-catala](https://github.com/ccoreilly/wav2vec2-catala)

When using this model, make sure that your speech input is sampled at 16kHz.

## Results

Word error rate was evaluated on the following datasets unseen by the model:

| Dataset | WER |
| ------- | --- |
| [Test split CV+ParlamentParla]((https://github.com/ccoreilly/wav2vec2-catala/blob/master/test-filtered.csv)) | 5.98% |
| [Google Crowsourced Corpus](https://www.openslr.org/69/) | 12.14% |
| Audiobook “La llegenda de Sant Jordi” | 12.02% | 


## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "ca", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("ccoreilly/wav2vec2-large-100k-voxpopuli-catala") 
model = Wav2Vec2ForCTC.from_pretrained("ccoreilly/wav2vec2-large-100k-voxpopuli-catala")

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