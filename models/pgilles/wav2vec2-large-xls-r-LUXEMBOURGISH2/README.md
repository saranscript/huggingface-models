---
language: 
  - lb
#thumbnail: "url to a thumbnail used in social sharing"
tags:
- ASR
- Automatic Speech Recognition
- speech
- wav2vec2
license: "mit"
datasets:
- "Wav2Vec2-XLS-R-300M"
#- "trained on custom data set (~8 hours)"
metrics:
- type: wer
- value: 0.188285

widget:
- src: https://luxappsdata.uni.lu/schnessen/media/recording_recordings/2021-10-13/pg_71_4629_rdc1j.wav
  example_title: Example 1
- src: https://luxappsdata.uni.lu/schnessen/media/recording_recordings/2021-08-20/pg_73_6801_3j86c.wav
  example_title: Example 2
- src: https://luxappsdata.uni.lu/schnessen/media/recording_recordings/2018-11-29/pg_347_1313_kolin.wav
  example_title: Example 3
- src: https://luxappsdata.uni.lu/schnessen/media/recording_recordings/2018-08-05/pg_192_3299_1zqrn.wav
  example_title: Example 4
- src: https://luxappsdata.uni.lu/schnessen/media/recording_recordings/2018-08-05/pg_193_3278_xqzv1.wav
  example_title: Example 5

---

# First Automatic Speech Recognition Model for Luxembourgish

Training pipeline based on the tutorials:
- [Fine-tuning XLS-R for Multi-Lingual ASR with 🤗 Transformers](https://colab.research.google.com/github/patrickvonplaten/notebooks/blob/master/Fine_Tune_XLSR_Wav2Vec2_on_Turkish_ASR_with_%F0%9F%A4%97_Transformers.ipynb)
- [Fine-tuning XLSR-Wav2Vec2 for WOLOF ASR with 🤗](https://www.kaggle.com/kingabzpro/fine-tuning-xlsr-wav2vec2-for-wolof-asr-with/notebook)

Trained on custom data set (~8 hours of Luxembourgish audio+transcript data)

WER: 0.188285

This a first shot and purely experimental. The inferences are thus based only on the trained acoustic model. The results are still catastrophic and need to be further optimised. No language model has been used yet.