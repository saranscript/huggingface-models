---
language:
- en
- tr
datasets:
- covost2
- librispeech_asr
tags:
- audio
- speech-translation
- automatic-speech-recognition
- speech2text2
license: mit
pipeline_tag: automatic-speech-recognition
widget:
- example_title: Common Voice 1
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_en_99989.mp3
- example_title: Common Voice 2
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_en_99986.mp3
- example_title: Common Voice 3
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_en_99987.mp3
---


# S2T2-Wav2Vec2-CoVoST2-EN-TR-ST

`s2t-wav2vec2-large-en-tr` is a Speech to Text Transformer model trained for end-to-end Speech Translation (ST).
The S2T2 model was proposed in [Large-Scale Self- and Semi-Supervised Learning for Speech Translation](https://arxiv.org/pdf/2104.06678.pdf) and officially released in
[Fairseq](https://github.com/pytorch/fairseq/blob/6f847c8654d56b4d1b1fbacec027f47419426ddb/fairseq/models/wav2vec/wav2vec2_asr.py#L266).


## Model description

S2T2 is a transformer-based seq2seq (speech encoder-decoder) model designed for end-to-end Automatic Speech Recognition (ASR) and Speech
Translation (ST). It uses a pretrained [Wav2Vec2](https://huggingface.co/transformers/model_doc/wav2vec2.html) as the encoder and a transformer-based decoder. The model is trained with standard autoregressive cross-entropy loss and generates the translations autoregressively.

## Intended uses & limitations

This model can be used for end-to-end English speech to Turkish text translation.
See the [model hub](https://huggingface.co/models?filter=speech2text2) to look for other S2T2 checkpoints.


### How to use

As this a standard sequence to sequence transformer model, you can use the `generate` method to generate the
transcripts by passing the speech features to the model.

You can use the model directly via the ASR pipeline

```python
from datasets import load_dataset
from transformers import pipeline

librispeech_en = load_dataset("patrickvonplaten/librispeech_asr_dummy", "clean", split="validation")
asr = pipeline("automatic-speech-recognition", model="facebook/s2t-wav2vec2-large-en-tr", feature_extractor="facebook/s2t-wav2vec2-large-en-tr")

translation = asr(librispeech_en[0]["file"])
```

or step-by-step as follows:

```python
import torch
from transformers import Speech2Text2Processor, SpeechEncoderDecoder
from datasets import load_dataset

import soundfile as sf
model = SpeechEncoderDecoder.from_pretrained("facebook/s2t-wav2vec2-large-en-tr")
processor = Speech2Text2Processor.from_pretrained("facebook/s2t-wav2vec2-large-en-tr")

def map_to_array(batch):
    speech, _ = sf.read(batch["file"])
    batch["speech"] = speech
    return batch
    
ds = load_dataset("patrickvonplaten/librispeech_asr_dummy", "clean", split="validation")
ds = ds.map(map_to_array)

inputs = processor(ds["speech"][0], sampling_rate=16_000, return_tensors="pt")
generated_ids = model.generate(input_ids=inputs["input_features"], attention_mask=inputs["attention_mask"])
transcription = processor.batch_decode(generated_ids)
```

## Evaluation results

CoVoST-V2 test results for en-tr (BLEU score): **17.5**

For more information, please have a look at the [official paper](https://arxiv.org/pdf/2104.06678.pdf) - especially row 10 of Table 2.

### BibTeX entry and citation info

```bibtex
@article{DBLP:journals/corr/abs-2104-06678,
  author    = {Changhan Wang and
               Anne Wu and
               Juan Miguel Pino and
               Alexei Baevski and
               Michael Auli and
               Alexis Conneau},
  title     = {Large-Scale Self- and Semi-Supervised Learning for Speech Translation},
  journal   = {CoRR},
  volume    = {abs/2104.06678},
  year      = {2021},
  url       = {https://arxiv.org/abs/2104.06678},
  archivePrefix = {arXiv},
  eprint    = {2104.06678},
  timestamp = {Thu, 12 Aug 2021 15:37:06 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2104-06678.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}

```
