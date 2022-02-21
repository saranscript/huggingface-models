---
language: ary
datasets:
- mgb5 
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Moroccan Arabic dialect by Othmane Rifki
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: MGB5 from ELDA and https://arabicspeech.org/
      type: ELDA and https://arabicspeech.org/
      args: ary
    metrics:
       - name: Test WER
         type: wer
         value: 66.45
---

# Wav2Vec2-Large-XLSR-53-Moroccan

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on [MGB5 Moroccan Arabic](http://www.islrn.org/resources/938-639-614-524-5/) kindly provided by [ELDA](http://www.elra.info/en/about/elda/) and [ArabicSpeech](https://arabicspeech.org/mgb5/).

In order to have access to MGB5, please request it from ELDA.

When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import re
import torch
import librosa
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import soundfile as sf


dataset = load_dataset("ma_speech_corpus", split="test")

processor = Wav2Vec2Processor.from_pretrained("othrif/wav2vec2-large-xlsr-moroccan")
model = Wav2Vec2ForCTC.from_pretrained("othrif/wav2vec2-large-xlsr-moroccan")
model.to("cuda")


chars_to_ignore_regex = '[\\,\\?\\.\\!\\-\\;\\:\\"\\“\\'\\�]'

def remove_special_characters(batch):
    batch["text"] = re.sub(chars_to_ignore_regex, "", batch["sentence"]).lower() + " "
    return batch


dataset = dataset.map(remove_special_characters)
dataset = dataset.select(range(10))

def speech_file_to_array_fn(batch):
    start, stop = batch['segment'].split('_')
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    speech_array, sampling_rate = sf.read(batch["path"], start=int(float(start) * sampling_rate),
                                          stop=int(float(stop) * sampling_rate))
    batch["speech"] = librosa.resample(speech_array, sampling_rate, 16_000)
    batch["sampling_rate"] = 16_000
    batch["target_text"] = batch["text"]
    return batch


dataset = dataset.map(
    speech_file_to_array_fn
)

def predict(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["predicted"] = processor.batch_decode(pred_ids)
    return batch

dataset = dataset.map(predict, batched=True, batch_size=32)

for reference, predicted in zip(dataset["sentence"], dataset["predicted"]):
    print("reference:", reference)
    print("predicted:", predicted)
    print("--")
```

Here's the output:
```
reference: عشرين ألفريال الوحده وشي خمسميه دريال

predicted: عشرين علف ريا لوحده وشي خمسميات ريال
--
reference: واحد جوج تلاتة ربعه خمسة ستة

predicted: غيحك تويش تتبة نتاست
--
reference: هي هاديك غتجينا تقريبا ميه وسته وعشرين ألف ريال

predicted: ياض كتجينا تقريبه ميه أو ستي و عشيناأفرين
--
reference: ###والصرف ليبقا نجيب بيه الصالون فلهوندا... أهاه نديروها علاش لا؟...

predicted: أواصرف ليبقا نجيب يه اصالون فالهندا أه نديروها علاش لا
--
reference: ###صافي مشات... أنا أختي معندي مندير بهاد صداع الراس...

predicted: صافي مشات أنا خصي معندي مندير بهاد داع راسك
  ف
--
reference: خلصو ليا غير لكريدي ديالي وديرو ليعجبكوم

predicted: خلصو ليا غير لكريدي ديالي أوديرو لي عجبكوم
--
reference: أنا نتكلف يلاه لقى شي حاجه نشغل بيها راسي

predicted: أنا نتكلف يالله لقا شي حاجه نشغل بيها راسي
```

## Evaluation

The model can be evaluated as follows on the Arabic test data of Common Voice. 


```python
import re
import torch
import librosa
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import soundfile as sf

eval_dataset = load_dataset("ma_speech_corpus", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("othrif/wav2vec2-large-xlsr-moroccan")
model = Wav2Vec2ForCTC.from_pretrained("othrif/wav2vec2-large-xlsr-moroccan")
model.to("cuda")

chars_to_ignore_regex = '[\\,\\?\\.\\!\\-\\;\\:\\"\\“\\'\\�]'

def remove_special_characters(batch):
    batch["text"] = re.sub(chars_to_ignore_regex, "", batch["sentence"]).lower() + " "
    return batch


eval_dataset = eval_dataset.map(remove_special_characters, remove_columns=["sentence"])
#eval_dataset = eval_dataset.select(range(100))

def speech_file_to_array_fn(batch):
    start, stop = batch['segment'].split('_')
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    speech_array, sampling_rate = sf.read(batch["path"], start=int(float(start) * sampling_rate),
                                          stop=int(float(stop) * sampling_rate))
    batch["speech"] = librosa.resample(speech_array, sampling_rate, 16_000)
    batch["sampling_rate"] = 16_000
    batch["target_text"] = batch["text"]
    return batch


eval_dataset = eval_dataset.map(
    speech_file_to_array_fn,
    remove_columns=eval_dataset.column_names
)

def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch

result = eval_dataset.map(evaluate, batched=True, batch_size=32)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["target_text"])))
```

**Test Result**: 66.45


## Training

The  [MGB5](http://www.islrn.org/resources/938-639-614-524-5/) `train`, `validation` datasets were used for training.

The script used for training can be found [here](https://github.com/othrif/xlsr-wav2vec2) 