---
---
language:
- la
license: agpl-3.0
tags:
- robust-speech-event
datasets:
- lsb/poetaexmachina-mp3-recitations
metrics:
- wer
model-index:
- name: wav2vec2-base-it-latin
  results:
    - task:
        type: automatic-speech-recognition
        name: Speech Recognition
      dataset:
        type: lsb/poetaexmachina-mp3-recitations
        name: Poeta Ex Machina mp3 recitations
      metrics:
        - type: wer
          value: 0.398
          name: Test WER

---
---

# wav2vec2-base-it-latin

This model is a fine-tuned version of [wav2vec2-base-it-voxpopuli](https://huggingface.co/facebook/wav2vec2-base-it-voxpopuli)

The dataset used is the [poetaexmachina-mp3-recitations](https://github.com/lsb/poetaexmachina-mp3-recitations),
all of the 2-series texts (vergil) and every tenth 1-series text (words from Poeta Ex Machina's [database](https://github.com/lsb/poetaexmachina/blob/master/merged-scansions.db) of words with scansions).

It achieves the following [results](https://github.com/lsb/tironiculum/blame/trunk/wav2vec2%20base%20it%20latin.ipynb#L1234) on the evaluation set:

- Loss: 0.1943
- WER: 0.398
