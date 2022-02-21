# finetuned-wav2vec2-960h

This model was trained as a part of my **GSoC'21 (Google Summer of Code)** project. It is fine-tuned on 960h of **LibriSpeech dataset** (`train-clean-100`, `train-clean-360`, `train-other-500`) and evaluated on `test-clean` data.

| WER (word error rate) | 5.67 |
|-----------------------|------|

You can find code for training here: https://github.com/vasudevgupta7/gsoc-wav2vec2.