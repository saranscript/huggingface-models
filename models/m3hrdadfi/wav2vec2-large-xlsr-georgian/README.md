---
language: ka
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
widget:
- example_title: Common Voice sample 566
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-georgian/resolve/main/sample566.flac
- example_title: Common Voice sample 95
  src: https://huggingface.co/m3hrdadfi/wav2vec2-large-xlsr-georgian/resolve/main/sample95.flac
model-index:
- name: XLSR Wav2Vec2 Georgian by Mehrdad Farahani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice ka
      type: common_voice
      args: ka
    metrics:
       - name: Test WER
         type: wer
         value: 43.86
        
---

# Wav2Vec2-Large-XLSR-53-Georgian

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) in Georgian using [Common Voice](https://huggingface.co/datasets/common_voice). When using this model, make sure that your speech input is sampled at 16kHz.

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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-georgian")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-georgian").to(device)

dataset = load_dataset("common_voice", "ka", split="test[:1%]")
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
reference: პრეზიდენტობისას ბუში საქართველოს და უკრაინის დემოკრატიულ მოძრაობების და ნატოში გაწევრიანების აქტიური მხარდამჭერი იყო
predicted: პრეზიდენტო ვისას ბუში საქართველოს და უკრაინის დემოკრატიულ მოძრაობების და ნატიში დაწევრიანების აქტიური მხარდამჭერი იყო
---
reference: შესაძლებელია მისი დამონება და მსახურ დემონად გადაქცევა
predicted: შესაძლებელია მისი დამონებათ და მსახურდემანად გადაქცევა
---
reference: ეს გამოსახულებები აღბეჭდილი იყო მოსკოვის დიდი მთავრებისა და მეფეების ბეჭდებზე
predicted: ეს გამოსახულებები აღბეჭდილი იყო მოსკოვის დიდი მთავრებისა და მეფეების ბეჭდებზე
---
reference: ჯოლიმ ოქროს გლობუსისა და კინომსახიობთა გილდიის ნომინაციები მიიღო
predicted: ჯოლი მოქროს გლობუსისა და კინამსახიობთა გილდიის ნომინაციები მიიღო
---
reference: შემდგომში საქალაქო ბიბლიოთეკა სარაიონო ბიბლიოთეკად გადაკეთდა გაიზარდა წიგნადი ფონდი
predicted: შემდღომში საქალაქო ბიბლიოთეკა სარაიონო ბიბლიოთეკად გადაკეთა გაიზარდა წიგნადი ფოვდი
---
reference: აბრამსი დაუკავშირდა მირანდას და ორი თვის განმავლობაში ისინი მუშაობდნენ აღნიშნული სცენის თანმხლებ მელოდიაზე
predicted: აბრამში და უკავშირდა მირანდეს და ორითვის განმავლობაში ისინი მუშაობდნენა აღნიშნულის ჩენის მთამხლევით მელოდიაში
---
reference: ამჟამად თემთა პალატის ოპოზიციის ლიდერია ლეიბორისტული პარტიის ლიდერი ჯერემი კორბინი
predicted: ამჟამად თემთა პალატის ოპოზიციის ლიდერია ლეიბურისტული პარტიის ლიდერი ჯერემი კორვინი
---
reference: ორი
predicted: ორი
---
reference: მას შემდეგ იგი კოლექტივის მუდმივი წევრია
predicted: მას შემდეგ იგი კოლექტივის ფუდ მივი წევრია
---
reference: აზერბაიჯანულ ფილოსოფიას შეიძლება მივაკუთვნოთ რუსეთის საზოგადო მოღვაწე ჰეიდარ ჯემალი
predicted: აზერგვოიჯანალ ფილოსოფიას შეიძლება მივაკუთვნოთ რუსეთის საზოგადო მოღვაწე ჰეიდარ ჯემალი
---
reference: ბრონქსში ჯერომის ავენიუ ჰყოფს გამჭოლ ქუჩებს აღმოსავლეთ და დასავლეთ ნაწილებად
predicted: რონგში დერომიწ ავენილ პოფს გამ დოლფურქებს აღმოსავლეთ და დასავლეთ ნაწილებად
---
reference: ჰაერი არის ჟანგბადის ის ძირითადი წყარო რომელსაც საჭიროებს ყველა ცოცხალი ორგანიზმი
predicted: არი არის ჯამუბადესის ძირითადი წყარო რომელსაც საჭიროოებს ყველა ცოცხალი ორგანიზმი
---
reference: ჯგუფი უმეტესწილად ასრულებს პოპმუსიკის ჟანრის სიმღერებს
predicted: ჯგუფიუმეტესწევად ასრულებს პოპნუსიკის ჟანრის სიმრერებს
---
reference: ბაბილინა მუდმივად ცდილობდა შესაძლებლობების ფარგლებში მიეღო ცოდნა და ახალი ინფორმაცია
predicted: ბაბილინა მუდმივა ცდილობდა შესაძლებლობების ფარგლებში მიიღო ცოტნა და ახალი ინფორმაცია
---
reference: მრევლის რწმენით რომელი ჯგუფიც გაიმარჯვებდა მთელი წლის მანძილზე სიუხვე და ბარაქა არ მოაკლდებოდა
predicted: მრევრის რწმენით რომელიჯგუფის გაიმარჯვებდა მთელიჭლის მანძილზა სიუყვეტაბარაქა არ მოაკლდებოდა
---
reference: ნინო ჩხეიძეს განსაკუთრებული ღვაწლი მიუძღვის ქუთაისისა და რუსთაველის თეატრების შემოქმედებით ცხოვრებაში
predicted: მინო ჩხეიძეს განსაკუთრებული ღოვაწლი მიოცხვის ქუთაისისა და რუსთაველის თეატრების შემოქმედებით ცხოვრებაში
---
reference: იგი სამი დიალექტისგან შედგება
predicted: იგი სამი დიალეთის გან შედგება
---
reference: ფორმით სირაქლემებს წააგვანან
predicted: ომიცი რაქლემებს ააგვანამ
---
reference: დანი დაიბადა კოლუმბუსში ოჰაიოში
predicted: დონი დაიბაოდა კოლუმბუსში ოხვაიოში
---
reference: მშენებლობისათვის გამოიყო ადგილი ყოფილი აეროპორტის რაიონში
predicted: შენებლობისათვის გამოიყო ადგილი ყოფილი აეროპორტის რაიონში
---
```


## Evaluation

The model can be evaluated as follows on the Georgian test data of Common Voice.

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
processor = Wav2Vec2Processor.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-georgian")
model = Wav2Vec2ForCTC.from_pretrained("m3hrdadfi/wav2vec2-large-xlsr-georgian").to(device)

dataset = load_dataset("common_voice", "ka", split="test")
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


**Test Result**: 
- WER: 43.86%


## Training & Report
The Common Voice `train`, `validation` datasets were used for training.

You can see the training states [here](https://wandb.ai/m3hrdadfi/wav2vec2_large_xlsr_ka/reports/Fine-Tuning-for-Wav2Vec2-Large-XLSR-53-Georgian--Vmlldzo1OTQyMzk?accessToken=ytf7jseje66a3byuheh68o6a7215thjviscv5k2ewl5hgq9yqr50yxbko0bnf1d3)

The script used for training can be found [here](https://colab.research.google.com/github/m3hrdadfi/notebooks/blob/main/Fine_Tune_XLSR_Wav2Vec2_on_Georgian_ASR_with_%F0%9F%A4%97_Transformers_ipynb.ipynb)

## Questions?
Post a Github issue on the [Wav2Vec](https://github.com/m3hrdadfi/wav2vec) repo.