---
language: lt
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
widget:
- example_title: Common Voice sample 11
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-lithuanian/resolve/main/sample11.flac
- example_title: Common Voice sample 74
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-lithuanian/resolve/main/sample74.flac
model-index:
- name: XLSR Wav2Vec2 Lithuanian by Mehrdad Farahani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice lt
      type: common_voice
      args: lt
    metrics:
       - name: Test WER
         type: wer
         value: 34.66
        
---

# Wav2Vec2-Large-XLSR-53-Lithuanian

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in Lithuanian using [Common Voice](https://huggingface.co/datasets/common_voice). When using this model, make sure that your speech input is sampled at 16kHz.

## Usage
The model can be used directly (without a language model) as follows:

**Requirements**
```bash
# requirement packages
!pip install git+https://github.com/huggingface/datasets.git
!pip install git+https://github.com/huggingface/transformers.git
!pip install torchaudio
!pip install librosa
!pip install jiwer
```

**Normalizer**
```bash
!wget -O normalizer.py https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-lithuanian/raw/main/normalizer.py
```

**Prediction**
```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset

import numpy as np
import re
import string

import IPython.display as ipd

from normalizer import normalizer


def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    speech_array = speech_array.squeeze().numpy()
    speech_array = librosa.resample(np.asarray(speech_array), sampling_rate, 16_000)

    batch["speech"] = speech_array
    return batch


def predict(batch):
    features = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)

    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits 
        
    pred_ids = torch.argmax(logits, dim=-1)

    batch["predicted"] = processor.batch_decode(pred_ids)[0]
    return batch


device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-lithuanian")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-lithuanian").to(device)

dataset = load_dataset("common_voice", "lt", split="test[:1%]")
dataset = dataset.map(
    normalizer, 
    fn_kwargs={"remove_extra_space": True},
    remove_columns=list(set(dataset.column_names) - set(['sentence', 'path']))
)

dataset = dataset.map(speech_file_to_array_fn)
result = dataset.map(predict)

max_items = np.random.randint(0, len(result), 20).tolist()
for i in max_items:
    reference, predicted =  result["sentence"][i], result["predicted"][i]
    print("reference:", reference)
    print("predicted:", predicted)
    print('---')
```

**Output:**
```text
reference: jos tikslas buvo rasti kelią į ramųjį vandenyną šiaurės amerikoje
predicted: jos tikstas buvo rasikelia į ramų į vandenyna šiaurės amerikoje
---
reference: pietrytinėje dalyje likusių katalikų kapinių teritorija po antrojo pasaulinio karo dar padidėjo
predicted: pietrytinė daljelikusių gatalikų kapinių teritoriją pontro pasaulnio karo dar padidėjo
---
reference: koplyčioje pakabintas aušros vartų marijos paveikslas
predicted: koplyčioje pakagintas aušos fortų marijos paveikslas
---
reference: yra politinių debatų vedėjas
predicted: yra politinių debatų vedėjas
---
reference: žmogui taip pat gali būti mirtinai pavojingi
predicted: žmogui taip pat gali būti mirtinai pavojingi
---
reference: tuo pačiu metu kijeve nuverstas netekęs vokietijos paramos skoropadskis
predicted: tuo pačiu metu kiei venų verstas netekės vokietijos paramos kropadskis
---
reference: visos dvylika komandų tarpusavyje sužaidžia po dvi rungtynes
predicted: visos dvylika komandų tarpuso vysų žaidžia po dvi rungtynės
---
reference: kaukazo regioną sudaro kaukazo kalnai ir gretimos žemumos
predicted: kau kazo regioną sudaro kaukazo kalnai ir gretimos žemumus
---
reference: tarptautinių ir rusiškų šaškių kandidatas į sporto meistrus
predicted: tarptautinio ir rusiškos šaškių kandidatus į sporto meistrus
---
reference: prasideda putorano plynaukštės pietiniame pakraštyje
predicted: prasideda futorano prynaukštės pietiniame pakraštyje
---
reference: miestas skirstomas į senamiestį ir naujamiestį
predicted: miestas skirstomas į senamėsti ir naujamiestė
---
reference: tais pačiais metais pelnė bronzą pasaulio taurės kolumbijos etape komandinio sprinto rungtyje
predicted: tais pačiais metais pelnį mronsa pasaulio taurės kolumbijos etape komandinio sprento rungtyje
---
reference: prasideda putorano plynaukštės pietiniame pakraštyje
predicted: prasideda futorano prynaukštės pietiniame pakraštyje
---
reference: moterų tarptautinės meistrės vardas yra viena pakopa žemesnis už moterų tarptautinės korespondencinių šachmatų didmeistrės
predicted: moterų tarptautinės meistrės vardas yra gana pakopo žymesnis už moterų tarptautinės kūrespondencinių šachmatų didmesčias
---
reference: teritoriją dengia tropinės džiunglės
predicted: teritorija dengia tropinės žiunglės
---
reference: pastaroji dažnai pereina į nimcovičiaus gynybą arba bogoliubovo gynybą
predicted: pastaruoji dažnai pereina nimcovičiaus gynyba arba bogalių buvo gymyba
---
reference: už tai buvo suimtas ir tris mėnesius sėdėjo butyrkų kalėjime
predicted: užtai buvo sujumtas ir tris mėne susiedėjo butirkų kalėjime
---
reference: tai didžiausias pagal gyventojų skaičių regionas
predicted: tai didžiausias pagal gyventojų skaičių redionus
---
reference: vilkyškių miške taip pat auga raganų eglė
predicted: vilkiškimiškė taip pat auga ragano eglė
---
reference: kitas gavo skaraitiškės dvarą su palivarkais
predicted: kitas gavos karaitiškės dvarą spolivarkais
---
```


## Evaluation

The model can be evaluated as follows on the test data of Common Voice.

```python
import librosa
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
from datasets import load_dataset, load_metric

import numpy as np
import re
import string

from normalizer import normalizer


def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    speech_array = speech_array.squeeze().numpy()
    speech_array = librosa.resample(np.asarray(speech_array), sampling_rate, 16_000)

    batch["speech"] = speech_array
    return batch


def predict(batch):
    features = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)

    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits 
        
    pred_ids = torch.argmax(logits, dim=-1)

    batch["predicted"] = processor.batch_decode(pred_ids)[0]
    return batch


device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-lithuanian")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-lithuanian").to(device)

dataset = load_dataset("common_voice", "lt", split="test")
dataset = dataset.map(
    normalizer, 
    fn_kwargs={"remove_extra_space": True},
    remove_columns=list(set(dataset.column_names) - set(['sentence', 'path']))
)

dataset = dataset.map(speech_file_to_array_fn)
result = dataset.map(predict)

wer = load_metric("wer")

print("WER: {:.2f}".format(100 * wer.compute(predictions=result["predicted"], references=result["sentence"])))
```
]

**Test Result**: 
- WER: 34.66%


## Training & Report
The Common Voice `train`, `validation` datasets were used for training.

You can see the training states [here](https://wandb.ai/m3hrdadfi/wav2vec2_large_xlsr_lt/reports/Fine-Tuning-for-Wav2Vec2-Large-XLSR-53-Lithuanian--Vmlldzo1OTM1MTU?accessToken=kdkpara4hcmjvrlpbfsnu4s8cdk3a0xeyrb84ycpr4k701n13hzr9q7s60b00swx)

The script used for training can be found [here](https://colab.research.google.com/github/m3hrdadfi/notebooks/blob/main/Fine_Tune_XLSR_Wav2Vec2_on_Lithuanian_ASR_with_%F0%9F%A4%97_Transformers_ipynb.ipynb)


## Questions?
Post a Github issue on the [Wav2Vec](https://github.com/m3hrdadfi/wav2vec) repo.