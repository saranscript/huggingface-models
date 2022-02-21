---
language: multilingual
datasets:
- common_voice
- multilingual_librispeech
- covost2
tags:
- speech
- xls_r
- automatic-speech-recognition
- xls_r_translation
pipeline_tag: automatic-speech-recognition
license: apache-2.0
widget:
- example_title: Swedish
  src: https://cdn-media.huggingface.co/speech_samples/cv_swedish_1.mp3
- example_title: Arabic
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_ar_19058308.mp3
- example_title: Russian
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_ru_18849022.mp3
- example_title: German
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_de_17284683.mp3
- example_title: French
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_fr_17299386.mp3
- example_title: Indonesian
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_id_19051309.mp3
- example_title: Italian
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_it_17415776.mp3
- example_title: Japanese
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_ja_19482488.mp3
- example_title: Mongolian
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_mn_18565396.mp3
- example_title: Dutch
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_nl_17691471.mp3
- example_title: Russian
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_ru_18849022.mp3
- example_title: Turkish
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_tr_17341280.mp3
- example_title: Catalan
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_ca_17367522.mp3
- example_title: English
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_en_18301577.mp3
- example_title: Dutch
  src: https://cdn-media.huggingface.co/speech_samples/common_voice_nl_17691471.mp3
---

# Wav2Vec2-XLS-R-2B-22-16 (XLS-R-Any-to-Any)

Facebook's Wav2Vec2 XLS-R fine-tuned for **Speech Translation.**

![model image](https://raw.githubusercontent.com/patrickvonplaten/scientific_images/master/xls_r.png)

This is a [SpeechEncoderDecoderModel](https://huggingface.co/transformers/model_doc/speechencoderdecoder.html) model. 
The encoder was warm-started from the [**`facebook/wav2vec2-xls-r-2b`**](https://huggingface.co/facebook/wav2vec2-xls-r-2b) checkpoint and
the decoder from the [**`facebook/mbart-large-50`**](https://huggingface.co/facebook/mbart-large-50) checkpoint.
Consequently, the encoder-decoder model was fine-tuned on `{input_lang}` -> `{output_lang}` translation pairs
of the [Covost2 dataset](https://huggingface.co/datasets/covost2).

The model can translate from the following spoken languages `{input_lang}` to the following written languages `{output_lang}`:

`{input_lang}` -> `{output_lang}`

with `{input_lang}` one of:

{`en`, `fr`, `de`, `es`, `ca`, `it`, `ru`, `zh-CN`, `pt`, `fa`, `et`, `mn`, `nl`, `tr`, `ar`, `sv-SE`, `lv`, `sl`, `ta`, `ja`, `id`, `cy`}

and `{output_lang}`:

{`en`, `de`, `tr`, `fa`, `sv-SE`, `mn`, `zh-CN`, `cy`, `ca`, `sl`, `et`, `id`, `ar`, `ta`, `lv`, `ja`}

## Usage

### Demo

The model can be tested on [**this space**](https://huggingface.co/spaces/facebook/XLS-R-2B-22-16). 
You can select the target language, record some audio in any of the above mentioned input languages, 
and then sit back and see how well the checkpoint can translate the input.

### Example 

As this a standard sequence to sequence transformer model, you can use the `generate` method to generate the
transcripts by passing the speech features to the model.

You can use the model directly via the ASR pipeline. By default, the checkpoint will 
translate spoken English to written German. To change the written target language, 
you need to pass the correct `forced_bos_token_id` to `generate(...)` to condition 
the decoder on the correct target language. 

To select the correct `forced_bos_token_id` given your choosen language id, please make use 
of the following mapping:

```python
MAPPING = {
    "en": 250004,
    "de": 250003,
    "tr": 250023,
    "fa": 250029,
    "sv": 250042,
    "mn": 250037,
    "zh": 250025,
    "cy": 250007,
    "ca": 250005,
    "sl": 250052,
    "et": 250006,
    "id": 250032,
    "ar": 250001,
    "ta": 250044,
    "lv": 250017,
    "ja": 250012,
}
```

As an example, if you would like to translate to Swedish, you can do the following:

```python
from datasets import load_dataset
from transformers import pipeline

# select correct `forced_bos_token_id`
forced_bos_token_id = MAPPING["sv"]

# replace following lines to load an audio file of your choice
librispeech_en = load_dataset("patrickvonplaten/librispeech_asr_dummy", "clean", split="validation")
audio_file = librispeech_en[0]["file"]

asr = pipeline("automatic-speech-recognition", model="facebook/wav2vec2-xls-r-2b-22-to-16", feature_extractor="facebook/wav2vec2-xls-r-2b-22-to-16")

translation = asr(audio_file, forced_bos_token_id=forced_bos_token_id)
```

or step-by-step as follows:

```python
import torch
from transformers import Speech2Text2Processor, SpeechEncoderDecoderModel
from datasets import load_dataset

model = SpeechEncoderDecoderModel.from_pretrained("facebook/wav2vec2-xls-r-2b-22-to-16")
processor = Speech2Text2Processor.from_pretrained("facebook/wav2vec2-xls-r-2b-22-to-16")

ds = load_dataset("patrickvonplaten/librispeech_asr_dummy", "clean", split="validation")

# select correct `forced_bos_token_id`
forced_bos_token_id = MAPPING["sv"]

inputs = processor(ds[0]["audio"]["array"], sampling_rate=ds[0]["audio"]["array"]["sampling_rate"], return_tensors="pt")
generated_ids = model.generate(input_ids=inputs["input_features"], attention_mask=inputs["attention_mask"], forced_bos_token_id=forced_bos_token)
transcription = processor.batch_decode(generated_ids)
```

## More XLS-R models for `{lang}` -> `en` Speech Translation

- [Wav2Vec2-XLS-R-300M-EN-15](https://huggingface.co/facebook/wav2vec2-xls-r-300m-en-to-15)
- [Wav2Vec2-XLS-R-1B-EN-15](https://huggingface.co/facebook/wav2vec2-xls-r-1b-en-to-15)
- [Wav2Vec2-XLS-R-2B-EN-15](https://huggingface.co/facebook/wav2vec2-xls-r-2b-en-to-15)
- [Wav2Vec2-XLS-R-2B-22-16](https://huggingface.co/facebook/wav2vec2-xls-r-2b-22-to-16)
