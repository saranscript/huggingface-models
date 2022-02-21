---
language: de
datasets:
- common_voice
metrics:
- wer
- cer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 German with LM by Florian Zimmermeister
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
         value: 5.7467896819046755
       - name: Test CER
         type: cer
         value: 1.8980142607670552
---

**Test Result**

| Model | WER | CER |
| ------------- | ------------- | ------------- |
| flozi00/wav2vec2-large-xlsr-53-german-with-lm | **5.7467896819046755%** | **1.8980142607670552%** |

## Evaluation
The model can be evaluated as follows on the German test data of Common Voice.

```python
import torchaudio.functional as F
import torch
from transformers import AutoModelForCTC, AutoProcessor
import re
from datasets import load_dataset, load_metric

CHARS_TO_IGNORE = [",", "?", "¿", ".", "!", "¡", ";", "；", ":", '""', "%", '"', "�", "ʿ", "·", "჻", "~", "՞",
                   "؟", "،", "।", "॥", "«", "»", "„", "“", "”", "「", "」", "‘", "’", "《", "》", "(", ")", "[", "]",
                   "{", "}", "=", "`", "_", "+", "<", ">", "…", "–", "°", "´", "ʾ", "‹", "›", "©", "®", "—", "→", "。",
                   "、", "﹂", "﹁", "‧", "～", "﹏", "，", "｛", "｝", "（", "）", "［", "］", "【", "】", "‥", "〽",
                   "『", "』", "〝", "〟", "⟨", "⟩", "〜", "：", "！", "？", "♪", "؛", "/", "\\", "º", "−", "^", "ʻ", "ˆ"]

chars_to_ignore_regex = f"[{re.escape(''.join(CHARS_TO_IGNORE))}]"

counter = 0
wer_counter = 0
cer_counter = 0

def main():
    model = AutoModelForCTC.from_pretrained("flozi00/wav2vec2-large-xlsr-53-german-with-lm")
    processor = AutoProcessor.from_pretrained("flozi00/wav2vec2-large-xlsr-53-german-with-lm")

    wer = load_metric("wer")
    cer = load_metric("cer")

    ds = load_dataset("common_voice", "de", split="test")
    #ds = ds.select(range(100))

    def calculate_metrics(batch):
        global counter, wer_counter, cer_counter
        resampled_audio = F.resample(torch.tensor(batch["audio"]["array"]), 48_000, 16_000).numpy()

        input_values = processor(resampled_audio, return_tensors="pt", sampling_rate=16_000).input_values

        with torch.no_grad():
            logits = model(input_values).logits.numpy()[0]


        decoded = processor.decode(logits)
        pred = decoded.text

        ref = re.sub(chars_to_ignore_regex, "", batch["sentence"]).upper()

        wer_result = wer.compute(predictions=[pred], references=[ref])
        cer_result = cer.compute(predictions=[pred], references=[ref])

        counter += 1
        wer_counter += wer_result
        cer_counter += cer_result

        print(f"WER: {(wer_counter/counter)*100} | CER: {(cer_counter/counter)*100}")

        return batch


    ds.map(calculate_metrics, remove_columns=ds.column_names)
    
main()
```

Credits: 

The Acoustic model is an copy of [jonatasgrosman's model](https://huggingface.co/jonatasgrosman/wav2vec2-large-xlsr-53-german) I used to train an matching kenlm language model for