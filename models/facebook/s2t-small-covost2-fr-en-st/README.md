---
language:
- fr
- en
datasets:
- covost2
tags:
- audio
- speech-translation
- automatic-speech-recognition
license: mit
pipeline_tag: automatic-speech-recognition
widget:
- example_title: Librispeech sample 1
  src: https://cdn-media.huggingface.co/speech_samples/sample1.flac
- example_title: Librispeech sample 2
  src: https://cdn-media.huggingface.co/speech_samples/sample2.flac
---


# S2T-SMALL-COVOST2-FR-EN-ST

`s2t-small-covost2-fr-en-st` is a Speech to Text Transformer (S2T) model trained for end-to-end Speech Translation (ST).
The S2T model was proposed in [this paper](https://arxiv.org/abs/2010.05171) and released in
[this repository](https://github.com/pytorch/fairseq/tree/master/examples/speech_to_text)


## Model description

S2T is a transformer-based seq2seq (encoder-decoder) model designed for end-to-end Automatic Speech Recognition (ASR) and Speech
Translation (ST). It uses a convolutional downsampler to reduce the length of speech inputs by 3/4th before they are
fed into the encoder. The model is trained with standard autoregressive cross-entropy loss and generates the
transcripts/translations autoregressively.

## Intended uses & limitations

This model can be used for end-to-end French speech to English text translation.
See the [model hub](https://huggingface.co/models?filter=speech_to_text) to look for other S2T checkpoints.


### How to use

As this a standard sequence to sequence transformer model, you can use the `generate` method to generate the
transcripts by passing the speech features to the model.

*Note: The `Speech2TextProcessor` object uses [torchaudio](https://github.com/pytorch/audio)  to extract the
filter bank features. Make sure to install the `torchaudio` package before running this example.*

You could either install those as extra speech dependancies with
`pip install transformers"[speech, sentencepiece]"` or install the packages seperatly 
with `pip install torchaudio sentencepiece`.


```python
import torch
from transformers import Speech2TextProcessor, Speech2TextForConditionalGeneration
from datasets import load_dataset
import soundfile as sf

model = Speech2TextForConditionalGeneration.from_pretrained("facebook/s2t-small-covost2-fr-en-st")
processor = Speech2TextProcessor.from_pretrained("facebook/s2t-small-covost2-fr-en-st")

def map_to_array(batch):
    speech, _ = sf.read(batch["file"])
    batch["speech"] = speech
    return batch

ds = load_dataset(
    "patrickvonplaten/librispeech_asr_dummy",
    "clean",
    split="validation"
)
ds = ds.map(map_to_array)

inputs = processor(
    ds["speech"][0],
    sampling_rate=48_000,
    return_tensors="pt"
)
generated_ids = model.generate(input_ids=inputs["input_features"], attention_mask=inputs["attention_mask"])

translation = processor.batch_decode(generated_ids, skip_special_tokens=True)
```


## Training data

The s2t-small-covost2-fr-en-st is trained on French-English subset of [CoVoST2](https://github.com/facebookresearch/covost).
CoVoST is a large-scale multilingual ST corpus based on [Common Voice](https://arxiv.org/abs/1912.06670), created to to foster 
ST research with the largest ever open dataset


## Training procedure

### Preprocessing

The speech data is pre-processed by extracting Kaldi-compliant 80-channel log mel-filter bank features automatically from
WAV/FLAC audio files via PyKaldi or torchaudio. Further utterance-level CMVN (cepstral mean and variance normalization)
is applied to each example.

The texts are lowercased and tokenized using character based SentencePiece vocab.


### Training

The model is trained with standard autoregressive cross-entropy loss and using [SpecAugment](https://arxiv.org/abs/1904.08779).
The encoder receives speech features, and the decoder generates the transcripts autoregressively. To accelerate
model training and for better performance the encoder is pre-trained for English ASR.

## Evaluation results

CoVOST2 test results for fr-en (BLEU score): 26.25



### BibTeX entry and citation info

```bibtex
@inproceedings{wang2020fairseqs2t,
  title = {fairseq S2T: Fast Speech-to-Text Modeling with fairseq},
  author = {Changhan Wang and Yun Tang and Xutai Ma and Anne Wu and Dmytro Okhonko and Juan Pino},
  booktitle = {Proceedings of the 2020 Conference of the Asian Chapter of the Association for Computational Linguistics (AACL): System Demonstrations},
  year = {2020},
}

```
