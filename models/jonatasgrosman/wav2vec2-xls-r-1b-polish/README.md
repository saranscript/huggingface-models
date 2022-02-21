---
language:
- pl
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- pl
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R Wav2Vec2 Polish by Jonatas Grosman
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: pl
    metrics:
       - name: Test WER
         type: wer
         value: 11.01
       - name: Test CER
         type: cer
         value: 2.55
       - name: Test WER (+LM)
         type: wer
         value: 7.32
       - name: Test CER (+LM)
         type: cer
         value: 1.95
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: pl
    metrics:
       - name: Dev WER
         type: wer
         value: 26.31
       - name: Dev CER
         type: cer
         value: 13.85
       - name: Dev WER (+LM)
         type: wer
         value: 20.33
       - name: Dev CER (+LM)
         type: cer
         value: 13.00
---

# XLS-R-1B-POLISH

Fine-tuned [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on Polish using the [Common Voice 8](https://huggingface.co/datasets/mozilla-foundation/common_voice_8_0).
When using this model, make sure that your speech input is sampled at 16kHz.

This model has been fine-tuned thanks to the GPU credits generously given by the [OVHcloud](https://www.ovhcloud.com/en/public-cloud/ai-training/) :)

The script used for training can be found here: https://github.com/jonatasgrosman/wav2vec2-sprint


## Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id jonatasgrosman/wav2vec2-xls-r-1b-polish --dataset mozilla-foundation/common_voice_8_0 --config pl --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id jonatasgrosman/wav2vec2-xls-r-1b-polish --dataset speech-recognition-community-v2/dev_data --config pl --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

## Citation
If you want to cite this model you can use this:

```bibtex
@misc{grosman2022wav2vec2-xls-r-1b-polish,
  title={XLS-R Wav2Vec2 Polish by Jonatas Grosman},
  author={Grosman, Jonatas},
  publisher={Hugging Face},
  journal={Hugging Face Hub},
  howpublished={\url{https://huggingface.co/jonatasgrosman/wav2vec2-xls-r-1b-polish}},
  year={2022}
}
```