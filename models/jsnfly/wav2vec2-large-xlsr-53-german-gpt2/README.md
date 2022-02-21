---
language:
- de
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- de
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: Wav2Vec2-Large-XLSR-53-German-GPT2
  results:
  - task:
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: de
    metrics:
       - name: Test WER
         type: wer
         value: 10.02
       - name: Test CER
         type: cer
         value: 4.7
---

# Wav2Vec2-Large-XLSR-53-German-GPT2

This is an encoder-decoder model for automatic speech recognition trained on on the
MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - DE dataset. The encoder was initialized from
[jonatasgrosman/wav2vec2-large-xlsr-53-german](https://huggingface.co/jonatasgrosman/wav2vec2-large-xlsr-53-german) and
the decoder from [dbmdz/german-gpt2](https://huggingface.co/dbmdz/german-gpt2).

It was trained using a two step process:
* fine-tuning only the cross-attention weights and the decoder using the pre-computed outputs of the Wav2Vec-Modell
  * relatively fast training
  * also works on small GPU (eg. 8 GB)
  * but may take a lot of disk space
  * should already yield decent results
* fine-tuning the model end-to-end
  * much slower
  * needs a bigger GPU

There is also one trick, which seemed to improve performance significantly: adding position embeddings to the
encoder outputs and initializing them with the pre-trained position embeddings of the GPT2 model (See `eval.py`).

The training notebooks are still early drafts. Also results can probably improved a lot by using for example a learning
rate schedule.